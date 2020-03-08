To reproduce the results, it is convenient to call R from Python.

#install rpy2

#install package
from rpy2.robjects.packages import importr
utils = importr('utils')
utils.install_packages('forecast')

#evalute R snippets
robjects.r('''
        # create a function `f`
        f <- function(r, verbose=FALSE) {
            if (verbose) {
                cat("I am calling f().\n")
            }
            2 * pi * r
        }
        # call the function `f` with argument value 3
        f(3)
        ''')

# get function
func = robjects.r['f']
