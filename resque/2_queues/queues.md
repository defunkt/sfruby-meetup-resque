!SLIDE bullets incremental

# Queues 

* Supports multiple queues
* Determine priority
* Determine locality
* (or both)

!SLIDE ruby

# Priority

## `$ QUEUES=high,low rake resque:work`

!SLIDE ruby

# Locality

## `$ QUEUES=file_serve rake resque:work`

!SLIDE ruby

# Consume all queues

## `$ QUEUES=* rake resque:work`

