---
title: Drupal Security Patches
description: How to manually patch Drupal 7 and 8 with security patches, ahead of the upstream updates.
categories: [drupal]
contributors: [alexfornuto, ari]
---

When Drupal releases critical security releases, Pantheon takes immediate steps to patch our Drupal upstreams. These updates may not always be accessible for users who:

- use a [Custom Upstream](/docs/custom-upstream/) or [Public Distribution](/docs/start-state/#public-distributions) which hasn't been patched, or no upstream
- encounter merge conflicts when applying upstream updates


This doc describes how to manually patch your Drupal core.

<div class="alert alert-danger" role="alert">
<h4 class="info">Warning</h4>
<p markdown="1">Use the [standard process to update core](/docs/core-updates/) if the security patch is available to be applied in the Site Dashboard. The advanced method described on this page is intended to be used when a security patch is not yet available as a one-click update in the Site Dashboard, or when handling merge conflicts.</p>
</div>

## SA-CORE-2018-004

On April 25th 2018 Drupal release a [**highly critical** security patch](https://www.drupal.org/SA-CORE-2018-004){.extenral} to prevent remote code execution.

The Drupal community documentation describes how to [apply patches](https://www.drupal.org/patch/apply){.external} using git.


<ul class="nav nav-tabs" role="tablist">
  <li id="tab-4-id" role="presentation" class="active"><a href="#tab-4-anchor" aria-controls="tab-4-anchor" role="tab" data-toggle="tab">Drupal 8.5</a></li>
  <li id="tab-5-id" role="presentation"><a href="#tab-5-anchor" aria-controls="tab-5-anchor" role="tab" data-toggle="tab">Drupal 7</a></li>
  <li id="tab-6-id" role="presentation"><a href="#tab-6-anchor" aria-controls="tab-6-anchor" role="tab" data-toggle="tab">Drupal 6</a></li>
</ul>
<div class="tab-content">

<div role="tabpanel" class="tab-pane active" id="tab-4-anchor" markdown="1">

### Apply Patch Using Git {.info}

You'll need a local git clone of your site code.

1. Change directory to your site code. For example:

    ```bash
    cd ~/repos/site-name/
    ```

2. Make sure your local copy is up to date:

    ```bash
    git pull origin master
    ```

3. Download and apply the patch:

    ```bash
    curl -O https://patch-diff.githubusercontent.com/raw/pantheon-systems/drops-8/pull/212.patch
    patch -p1 < 212.patch
    ```

4. Remove the patch file, and stage code changes:

    ```bash
    rm 212.patch
    git add .
    ```

5. Confirm your changes:

    ```bash
    git status
    ```

6. Commit and push your changes back to Pantheon:

    ```bash
    git commit -m "Manually apply Drupal security patch"
    git push origin master
    ```

</div>

<div role="tabpanel" class="tab-pane" id="tab-5-anchor" markdown="1">

### Apply Patch Using Git {.info}

You'll need a local git clone of your site code.

1. Change directory to your site code. For example:

    ```bash
    cd ~/repos/site-name/
    ```

2. Make sure your local copy is up to date:

    ```bash
    git pull origin master
    ```

3. Download and apply the patch:

    ```bash
    curl -O https://patch-diff.githubusercontent.com/raw/pantheon-systems/drops-7/pull/121.patch
    patch -p1 < 121.patch
    ```

4. Remove the patch file, and stage code changes:

    ```bash
    rm 121.patch
    git add .
    ```

5. Confirm your changes:

    ```bash
    git status
    ```

6. Commit and push your changes back to Pantheon:

    ```bash
    git commit -m "Manually apply Drupal security patch"
    git push origin master
    ```

</div>

<div role="tabpanel" class="tab-pane" id="tab-6-anchor" markdown="1">

### Apply Patch Using Git {.info}

You'll need a local git clone of your site code.

1. Change directory to your site code. For example:

    ```bash
    cd ~/repos/site-name/
    ```

2. Make sure your local copy is up to date:

    ```bash
    git pull origin master
    ```

3. Download and apply the patch:

    ```bash
    curl -O https://patch-diff.githubusercontent.com/raw/pantheon-systems/drops-6/pull/20.patch
    patch -p1 < 20.patch
    ```

4. Remove the patch file, commit and push your changes back to Pantheon:

    ```bash
    rm 20.patch
    git commit -am "Manually apply Drupal security patch"
    git push origin master
    ```

</div>

</div>

## SA-CORE-2018-002

On March 28 2018 Drupal released a [critical security patch](https://www.drupal.org/SA-CORE-2018-002){.external} for Drupal 7 and 8 (also affecting Drupal 6).

The Drupal community documentation describes how to [apply patches](https://www.drupal.org/patch/apply){.external} using git.


<ul class="nav nav-tabs" role="tablist">
  <li id="tab-1-id" role="presentation" class="active"><a href="#tab-1-anchor" aria-controls="tab-1-anchor" role="tab" data-toggle="tab">Drupal 8.5</a></li>
  <li id="tab-2-id" role="presentation"><a href="#tab-2-anchor" aria-controls="tab-2-anchor" role="tab" data-toggle="tab">Drupal 7</a></li>
  <li id="tab-3-id" role="presentation"><a href="#tab-3-anchor" aria-controls="tab-3-anchor" role="tab" data-toggle="tab">Drupal 6</a></li>
</ul>
<div class="tab-content">

<div role="tabpanel" class="tab-pane active" id="tab-1-anchor" markdown="1">

### Apply Patch Using Git {.info}

You'll need a local git clone of your site code.

1. Change directory to your site code. For example:

    ```bash
    cd ~/repos/site-name/
    ```

2. Make sure your local copy is up to date:

    ```bash
    git pull origin master
    ```

3. Download and apply the patch:

    ```bash
    curl -O https://patch-diff.githubusercontent.com/raw/pantheon-systems/drops-8/pull/206.patch
    patch -p1 < 206.patch
    ```

4. Remove the patch file, and stage code changes:

    ```bash
    rm 206.patch
    git add .
    ```

5. Confirm your changes:

    ```bash
    git status
    ```

6. Commit and push your changes back to Pantheon:

    ```bash
    git commit -m "Manually apply Drupal security patch"
    git push origin master
    ```


</div>

<div role="tabpanel" class="tab-pane" id="tab-2-anchor" markdown="1">

### Apply Patch Using Git {.info}

You'll need a local git clone of your site code.

1. Change directory to your site code. For example:

    ```bash
    cd ~/repos/site-name/
    ```

2. Make sure your local copy is up to date:

    ```bash
    git pull origin master
    ```

3. Download and apply the patch:

    ```bash
    curl -O https://patch-diff.githubusercontent.com/raw/pantheon-systems/drops-7/pull/119.patch
    patch -p1 < 119.patch
    ```

4. Remove the patch file, and stage code changes:

    ```bash
    rm 119.patch
    git add .
    ```

5. Confirm your changes:

    ```bash
    git status
    ```

6. Commit and push your changes back to Pantheon:

    ```bash
    git commit -m "Manually apply Drupal security patch"
    git push origin master
    ```

</div>

<div role="tabpanel" class="tab-pane" id="tab-3-anchor" markdown="1">

### Apply Patch Using Git {.info}

You'll need a local git clone of your site code.

1. Change directory to your site code. For example:

    ```bash
    cd ~/repos/site-name/
    ```

2. Make sure your local copy is up to date:

    ```bash
    git pull origin master
    ```

3. Download and apply the patch:

    ```bash
    curl -O https://patch-diff.githubusercontent.com/raw/pantheon-systems/drops-6/pull/17.patch
    patch -p1 < 17.patch
    ```

4. Remove the patch file, commit and push your changes back to Pantheon:

    ```bash
    rm 17.patch
    git commit -am "Manually apply Drupal security patch"
    git push origin master
    ```

</div>

</div>

## Lock Multidev Environments

As an additional security measures, sites with [Multidev](/docs/multidev/) environments should consider [locking](/docs/security/) them until they can be patched. If you have [Terminus](/docs/terminus/) installed on your local computer, you can lock all environments at once with the following Bash script:

```bash
#!/bin/bash

#############################################################
# This script will, for a specified Pantheon site, lock all #
# multidev environments for the site.                       #
############################################################

# Asks user for the site name.
read -p 'Site name: ' SITE

# Define a user name and password to lock the site with.
read -p 'Username to unlock the environments (NOT your Pantheon account username): ' USER
read -sp 'Password: ' PASSWORD

echo

ALL_ENVS="$(terminus env:list $SITE --field=id | grep -v live | grep -v dev | grep -v test)"

for ENV in $ALL_ENVS ; do
  is_locked="$(terminus lock:info "$SITE.$ENV" --field=locked)"
  if [[ "$is_locked" == "true" ]] ; then
    echo "# $SITE.$ENV is already locked"
  else
    echo "# Locking $SITE.$ENV"
    terminus lock:enable "$SITE.$ENV" "$USER" "$PASSWORD"
  fi
done

```

##See Also

 - [Drupal Security Advisory](https://www.drupal.org/SA-CORE-2018-002){.external}
