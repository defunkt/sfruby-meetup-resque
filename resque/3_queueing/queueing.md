!SLIDE bullets incremental

# Jobs

* Normal Ruby classes or modules
* Must respond to `perform`
* Any arguments are passed to `perform`
* `@queue` class ivar determines queue

!SLIDE ruby

    @@@ ruby
    class Archive
      @queue = :file_serve

      def self.perform(repo_id, branch = nil)
        repo = Repository.find(repo_id)
        repo.create_archive(branch || "master")
      end
    end
    
!SLIDE ruby
    
    @@@ ruby
    Resque.enqueue(Archive, @repo.id, branch)    
    
!SLIDE ruby

    @@@ ruby
    Resque::Job.create(:file_serve, 
                       Archive, 
                       @repo.id, 
                       branch)   

!SLIDE                       

# Persistence

## Jobs are stored as JSON

!SLIDE javascript

    @@@ javascript
    {
        "class": "Archive",
        "args": [ 44, "masterbrew" ]
    }

!SLIDE                       

# Persistence

## Only objects that can be serialized to JSON can be queued as args