# Search

## **Searching records in one model according to several inputs in differents columns**

### Problem
PG search search for one input in several column or tables. We want a SQL request that may have one or several inputs to search on several colums

### Solution
`def index

  @jobs = Job.all
  
  @jobs = @jobs.where(category: params[:category]) if params[:category].present?
  
  @jobs = @jobs.where(location: params[:location]) if params[:location].present?
  
  @jobs = @jobs.where(name: params[:name]) if params[:name].present?
  
end`

*We narrow the search from ActiveRecord collection*
