pipeline{
    agent any
    stages
    {
     stage("test")
       {
    		steps
            {
    			bat "npm test" 
    	    }
	}
	    stage("build")
        {
            steps
            {
                bat "docker build -t jenkinimage ."
            }
        }
          stage("push")
        {
            steps
            {
		        bat "docker tag jenkinimage radhikamanglik/jenkinimage"
	            bat "docker push radhikamanglik/jenkinimage"
            }
        }
      stage("deploy")
        {
            steps
            {
		      bat   "docker pull radhikamanglik/jenkinimage"
	          bat "docker run -d -p 3000:3000 radhikamanglik/jenkinimage"
	        }
        }
    }
}
