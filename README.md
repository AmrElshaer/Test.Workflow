# Test.Workflow
# command
  docker run --rm -p 32777:5000   -e "ASPNETCORE_ENVIRONMENT=Development" -e "ASPNETCORE_URLS=http://+:5000"  amrelsher/test.workflow.command:branch_name
# query
docker run --rm -p 32778:5000   -e "ASPNETCORE_ENVIRONMENT=Development" -e "ASPNETCORE_URLS=http://+:5000" image
