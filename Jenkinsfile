pipeline{
    agent any
    environment{
        PATH = "D:\\Samiksha\\HDFC_BANK\\DevOps\\"
        file_name = "1st_Discussion_Yuvraj.txt"
        file_name1 = "test.txt"
        test_var = "a"
        file = 'test.txt,1st_Discussion_Yuvraj.txt,test1.txt'
    }
    properties([pipelineTriggers([githubPush()])])
    stages{
        /*stage ('Test file existence'){
            steps{
                script{
                    file.tokenize(',').each{
                        if(!fileExists ("${PATH}${it}")){
                        echo "${test_var},${it}"  
                        test_var = "${test_var},${file_name}"  
                        echo "exist file ${test_var}"
                    }
                        else{
                            echo 'does not exist'
                        }
                    }
                }
            }
        }*/
        stage ('Test file existence for loop'){
            steps{
                script{
                    def inputDetails = "1234-a0-12;1111-b0-34";
                    def cDesc = file.tokenize(",");
                    for (int i=0; i<cDesc.size(); ++i)
                    {
                        def cVer = cDesc.get(i);
                        if(!fileExists ("${PATH}${cVer}")){
                            if (i == 0){
                            //echo "${cVer}"  
                            test_var = "${cVer}"  
                            //echo "exist file ${test_var}"
                        }
                            else{
                                //echo "${test_var},${cVer}"  
                                test_var = "${test_var},${cVer}"  
                            }
                        }
                        /*def cNum = cVer.tokenize("-");
                        def a = cNum.get(0);
                        def b = cNum.get(1);
                        def c = cNum.get(2);
                    
                        println (" DEBUG : Input details are, ${a} : ${b} : ${c} \n");*/
                    }
                }
            }
        }
        stage('Print Output'){
            steps{
                echo "exist file ${test_var}"
                echo test_var
            }
        }
    }
}
