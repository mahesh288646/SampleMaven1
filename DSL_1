job('DSL-Tutorial-3-Test') {

    scm {

        checkout([
                $class                           : 'GitSCM',
                branches                         : [[name: '*/master/Release1.1/*']],
                doGenerateSubmoduleConfigurations: false,
                extensions                       : [[$class: 'CleanCheckout']],
                submoduleCfg                     : [],
                userRemoteConfigs                : [[credentialsId: 'Azure-GIT-ID', url: 'https://maheshbadenehal@dev.azure.com/maheshbadenehal/MyFirstProject/_git/Sample1']]
        ])
    }


    steps {
        //maven('-e clean test')
        //println("Mahesh Babu")
        shell "echo Maheshhhhhhhhh"
    }
}
