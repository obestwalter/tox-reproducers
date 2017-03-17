# Requirements are always lumped together

[![Build Status](https://travis-ci.org/obestwalter/tox-reproducers.svg?branch=master)](https://travis-ci.org/obestwalter/tox-reproducers)

Splitting conflicting dependencies (e.g. same package with different version pinning) like suggested in http://stackoverflow.com/a/39890333/2626627 do not solve the problem as all listed dependencies get grouped into one `pip` invocation:

    /opt/pyenv/versions/all/bin/python /opt/pycharm-professional/helpers/pycharm/_jb_tox_runner.py
    Testing started at 3:26 PM ...
    py35 create: /home/oliver/Dropbox/projects/tox/lab/mini/.tox/py35
    py35 installdeps: mock, -rreq1.txt, -rreq2.txt
    WARNING:Discarding $PYTHONPATH from environment, to override specify PYTHONPATH in 'passenv' in your configuration.
    ERROR: invocation failed (exit code 1), logfile: /home/oliver/Dropbox/projects/tox/lab/mini/.tox/py35/log/py35-1.log
    ERROR: actionid: py35
    msg: getenv
    cmdargs: ['/home/oliver/Dropbox/projects/tox/lab/mini/.tox/py35/bin/pip', 'install', 'mock', '-rreq1.txt', '-rreq2.txt']
    env: {...}

    Double requirement given: tox==1.6.0 (from -r req2.txt (line 2)) (already in tox==2.6.0 (from -r req1.txt (line 2)), name='tox')
    
    ERROR: could not install deps [mock, -rreq1.txt, -rreq2.txt]; v = InvocationError('/home/oliver/Dropbox/projects/tox/lab/mini/.tox/py35/bin/pip install mock -rreq1.txt -rreq2.txt (see /home/oliver/Dropbox/projects/tox/lab/mini/.tox/py35/log/py35-1.log)', 1)
    could not install deps [mock, -rreq1.txt, -rreq2.txt]; v = InvocationError('/home/oliver/Dropbox/projects/tox/lab/mini/.tox/py35/bin/pip install mock -rreq1.txt -rreq2.txt (see /home/oliver/Dropbox/projects/tox/lab/mini/.tox/py35/log/py35-1.log)', 1)
