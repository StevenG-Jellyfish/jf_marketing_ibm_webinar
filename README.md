# Jellyfish Webinar Series 
# ibm_webinar
Jellyfish Webinar Series : IBM Webinar Site


## environment configuration:
```bash
cd /home/sites
mkdir JellyfishMarketing
cd JellyfishMarketing

git clone git@github.com:YOUR-USERNAME/ibm_webinar
cd /home/sites/JellyfishMarketing/ibm_webinar
git remote add upstream git@github.com:JellyfishGroup/ibm_webinar
git remote set-url upstream --push no-pushing
git remote -v
chown apache:apache -R ./public_html/
```


## .ini configuration: (not needed)
```bash
cd /home/sites/JellyfishMarketing/ibm_webinar
cp install/ibm_webinar.ini /etc/jellyfish/
nano /etc/jellyfish/ibm_webinar.ini
# copy the correct definitions from sgel6 container for the .ini file
service httpd restart
```


## vhost:
```bash
cd /home/sites/JellyfishMarketing/ibm_webinar
cp install/ibm_webinar.conf /home/vhosts/
service httpd restart
```

## front end developer begin:
Are you a new developer to the company? If so, following the instruction guide here:
- http://wiki.jellyfish.tmp/index.php/Sass_Set_Up_on_a_Dev_Container


## task runner set-up:
```bash
cd /home/sites/ibm_webinar/Front-End/task_runner/
npm install
gulp watch
```


## environment urls:
- **[dev]**     http://ibm_webinar.sgel6.dev.jellyfish.tmp
- **[build]**   N/A
- **[stage]**   N/A
- **[prod]**    N/A


## deployment processes:
- **[dev => build & stage]**  N/A
- **[production/live]**       N/A


## administration access:
- Non-Production: `{URL}/wp-admin`
- Production: N/A
  - u: admin | p: **[refer to mavenlink]**
  - u: content | p: **[refer to mavenlink]**


## asset duplication:
The rcopy command will copy all files within the first path to the second path defined.
```sh
# connect to your dev container and execute the following to copy all uploads
rcopy root@sgel6.dev.jellyfish.tmp:/home/sites/JellyfishMarketing/ibm_webinar/public_html/images/* /home/sites/JellyfishMarketing/ibm_webinar/public_html/images/
```

## known bugs:
- **403 Forbidden Error** 
- White screen may be any of the following:
  - ``chown apache:apache`` the entire ``/home/sites/JellyfishMarketing/ibm_webinar/public_html`` directory
- "The uploaded file could not be moved to"... error is typically a migration/permissions issue
  - ``chown apache:apache`` the entire ``/home/sites/JellyfishMarketing/ibm_webinar/public_html`` directory
    - *Still didn't work? See here: http://goo.gl/OtT0a9*
