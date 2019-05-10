pipeline {
    agent any
    stages {
        stage('Test) {
            parallel {
                stage('test1') {
                    node {label 'node1'}
                    steps {
                        sh '''cd cmake/handson/3_installing_libs/solution/dotprod_with_export
                              mkdir build && cd build
                              cmake .. -DCMAKE_INSTALL_PREFIX=$(pwd)/../install
                              make install
                              ./tests/test_norm'''
                    }
                }
                stage('test2') {
                    node {label 'node2'}
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
