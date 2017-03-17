# Requirements are always lumped together

Splitting conflicting dependencies (e.g. same package with different version pinning) like suggested in http://stackoverflow.com/a/39890333/2626627 do not solve the problem as all listed dependencies get grouped into one `pip` invocation:

    /opt/pyenv/versions/all/bin/python /opt/pycharm-professional/helpers/pycharm/_jb_tox_runner.py
    Testing started at 3:16 PM ...
    py36 create: /home/oliver/Dropbox/projects/tox/lab/mini/.tox/py36
    py36 installdeps: mock, -rreq1.txt, -rreq2.txt
    WARNING:Discarding $PYTHONPATH from environment, to override specify PYTHONPATH in 'passenv' in your configuration.
    ERROR: invocation failed (exit code 1), logfile: /home/oliver/Dropbox/projects/tox/lab/mini/.tox/py36/log/py36-1.log
    ERROR: actionid: py36
    msg: getenv
    cmdargs: ['/home/oliver/Dropbox/projects/tox/lab/mini/.tox/py36/bin/pip', 'install', 'mock', '-rreq1.txt', '-rreq2.txt']
    env: {...}
    
    Double requirement given: tox==1.6.0 (from -r req2.txt (line 2)) (already in tox==2.6.0 (from -r req1.txt (line 2)), name='tox')
    
    ERROR: could not install deps [mock, -rreq1.txt, -rreq2.txt]; v = InvocationError('/home/oliver/Dropbox/projects/tox/lab/mini/.tox/py36/bin/pip install mock -rreq1.txt -rreq2.txt (see /home/oliver/Dropbox/projects/tox/lab/mini/.tox/py36/log/py36-1.log)', 1)
    could not install deps [mock, -rreq1.txt, -rreq2.txt]; v = InvocationError('/home/oliver/Dropbox/projects/tox/lab/mini/.tox/py36/bin/pip install mock -rreq1.txt -rreq2.txt (see /home/oliver/Dropbox/projects/tox/lab/mini/.tox/py36/log/py36-1.log)', 1)
