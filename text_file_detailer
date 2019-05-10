# Coding: utf-8

# CONTENT: PERSONAL FUNCTIONS PROJECT - HANDLING TEXT;
# AUTHOR: RONALDO PIMENTAL MARQUES DA SILVA;
# DATE: 2019 APRIL;
# LANGUAGE: PYTHON 3.7;
# PLATFORM: VS CODE 1.32.3, WITH ANACONDA 4.5.12, ON M.S.WINDOWS 7;

# This file: lwcsdcount.py ;
# Means: lines words characters spaces dictionary counter.


# IMPORTS:
import sys
import os



# CONSTANTS:
# Application info:
global _app_name
_app_name = 'lwcsdcount'
global _app_version
_app_version = 'v 0.1'
global _app_description
_app_description = 'Lines, Words, Characters, Spaces, Dictionary, Counts'

# Standard syntax of this application on command line.
global _syntax
_syntax = ' \n'
_syntax += _app_name +' '+ _app_version +' \n'
_syntax += _app_description +' \n'
_syntax += ' syntax: <./lwcsdcount.py> [[<->h|l,w,c,s,d] <text_file>] \n'
_syntax += ' \n'

# Standard help of this application on command line.
global _help
_help = _syntax
_help += 'Options letters: \n'
_help += ' -l : how many lines; \n'
_help += ' -w : how many word, spaces are not considered; \n'
_help += ' -c : how many characteres, spaces are not considered; \n'
_help += ' -s : how many spaces; \n'
_help += ' -d : how many words and each their respective quantities on \
target-file\'s dictionary,\n      spaces are not considered; \n'
_help += ' -h : print the syntax and a brief help for user. \n'
_help += ' \n'
_help += 'Text file: \n'
_help += '  It must be a text file on ASCI format; \n'
_help += '  It must be ... \n'
_help += '  It must have ... \n'
_help += ' \n'

# Standards arguments acceptables;
global _acceptables_opts_set
_acceptables_opts_set = set(['l','w','c','s','d','h'])

# Base directory wich where script is executing;
global _base_dir
_base_dir = os.path.dirname(os.path.realpath(__file__))




# MY FUNCTIONS.
def show_syntax():
    print(_syntax)
    return




def show_help():
    print(_help)
    return




def is_a_opt_on_args(passed_opt):
    return_list = list()
    passed_opt = list(passed_opt)

    if (len(passed_opt) >= 2): 
        # len >= '-X'
        if (passed_opt[0] == '-'):
            # Possibly opt.
            if len(passed_opt)<=(len(_acceptables_opts_set)+1) :
                # Currectly sized.
                for i in range(1, len(passed_opt)):
                    if (passed_opt[i] in _acceptables_opts_set):
                        # Opt letter acceptable.
                        return_list += passed_opt[i]
                    else:
                        print('ERROR: Invalid option: \'{}\' will be disconsidered.'.format(passed_opt[i]))
            else:
                # Too many options.
                print('ERROR: Too many options.')
                print('Expected {} at most {}.'.format(len(_acceptables_opts_set) , _acceptables_opts_set))
                print('But {} were found: {}.'.format(len(passed_opt)-1 , passed_opt[1:]))
                print('Only {} first will be used: {}.'.format(len(_acceptables_opts_set), passed_opt[1:len(_acceptables_opts_set)+1]) )
                return is_a_opt_on_args( ''.join(str(e) for e in passed_opt[0:len(_acceptables_opts_set)+1]) )
        else:
            # It is not an opt.
            # May be a FILE.
            return False
    else:
        # Not asked opt .
        return False
    
    if len(return_list)==0:

        return False
    else:
        return list(set(return_list))




def is_a_file_on_args(passed_file):
    return_file = ''

    if (len(passed_file) > 0) and (passed_file != ''):
        # Possibly file.
        global _base_dir
        file_path = _base_dir +"\\" + passed_file
        if os.path.exists(file_path):
            # Exists a DIR or FILE.
            if os.path.isfile(file_path):
                # It is a file.
                try:
                    with open(file_path, 'r') as open_file:
                        return_file = passed_file
                
                except:
                    print('ERROR: File opening failed: \'{}\', at: \'{}\'.'.format(passed_file, _base_dir))
                    return False
            else:
                # It is note file, it is a dir.
                print('ERROR: File opening failed: \'{}\', at: \'{}\'.'.format(passed_file, _base_dir))
                print('File not found. Possibly it is a directory.')
                return False
        else:
            # Path + file do not exists.
            print('ERROR: File opening failed: \'{}\', at: \'{}\'.'.format(passed_file, _base_dir))
            print('File not found.')
            return False
    else:
        # Not asked file .
        return False

    if len(return_file)==0:
        return False
    else:
        return return_file




def x_counter(target_file):
    
    open_file = open(target_file,'r')
    
    a_text = open_file.read() # whole text
    a_text = open_file.read(int) # num of chars in text
    a_text = open_file.readline() # 1 line each time
    a_text = open_file.readlines() # all lines in a list

    open_file.close()
    print(a_text)
    return




# MODULE BODY:
if len(sys.argv) == 1:
    # No arguments. 1 first = script executing.
    # Print the application syntax.
    show_syntax()
    # Finished.

elif len(sys.argv) == 2:
    # Argument must be an opt or a file.
    if is_a_opt_on_args(sys.argv[1]):
        # Execute the opts. It would be '-h'.
        if sys.argv[1] == '-h':
            show_help()
        else:
            # Command line passe opt without target-file. Error.
            print('Error: the target file is missed.')

    elif is_a_file_on_args(sys.argv[1]):
        # Execute the file without opts: except 'h' assume all else opts.
        print('exec full opt.')
        x_counter(sys.argv[1])

elif len(sys.argv) == 3:
    # Arguments must be an option sequence, and a file, respectively.
    if is_a_opt_on_args(sys.argv[1]):
        # Execute with opts.
        if is_a_file_on_args(sys.argv[2]):
            # Execute the file.
            print('exec with passed opt.')

else:
    # Others quantities (beyond 2) of arguments are not considered.
    # 1 first = script executing; 2 second = otpins; 3 tird = file target. At most.
    # Print the application syntax.
    show_syntax()
    # Finished.
