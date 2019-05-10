pipeline {
    agent any
    stages {
        stage('Test') {
            environment {
                PATH = "$PATH:/usr/local/cmake-3.14.3-Linux-x86_64/bin"
            }
            parallel {
                stage('test1') {
                    agent {label 'node1'}
                    steps {
                        sh '''cd cmake/handson/3_installing_libs/solution/dotprod_with_export
                              mkdir build && cd build
                              cmake .. -DCMAKE_INSTALL_PREFIX=$(pwd)/../install
                              make install
                              ./tests/test_norm'''
                    }
                }
                stage('test2') {
                    agent {label 'node2'}
                    steps {
                        sh '''cd cmake/handson/3_installing_libs/exercise/dotprodcl/src
                              mkdir build && cd build
                              cmake .. -DDotprod_DIR=$(pwd)/../../../solution/dotprod_with_export/install/lib64/cmake
                              make
                              ./src/dotprodcl --size=20'''
                    }
                }
            }
        }
    }
}
