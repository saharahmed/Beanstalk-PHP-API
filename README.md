# Beanstalk PHP API Documentation v0.1 #

## Installation ##
Requires PHP 5, libcurl library and SimpleXML extension

1. Copy beanstalk_api.php into a directory on your webserver
2. Call beanstalk_api.php in the php file you wish to use it in using `require_once('path/beanstalk_api.php');`

## Usage ##
Before using any of the following methods, you must first declare the following:
	
	$varname = new beanstalk_api(array('account_name' => 'ACCOUNT_NAME_HERE', 'username' => 'USERNAME_HERE', 'password' => 'PASSWORD_HERE'));

Make sure to put your account details in the correct places.

### API Methods ###
List of available function calls:

* `get_account_details();`
* `update_account_details();`
* `find_all_plans();`
* `find_all_users();`
* `find_single_user(user_id);`
* `find_current_user();`
* `create_user(login, email, first_name, last_name, password);`
* `update_user(user_id, params);`
* `delete_user(user_id);`
* `find_all_public_keys();`
* `find_single_public_key(key_id);`
* `create_public_key(content);`
* `update_public_key(key_id, params);`
* `delete_public_key(key_id);`
* `find_all_repositories();`
* `find_single_repository(repo_id);`
* `create_repository(name, type_id, title);`
* `update_repository(repo_id, params);`
* `find_user_permissions(user_id);`
* `create_user_permissions(user_id, repo_id, read, write, full_deployments_access);`
* `delete_user_permissions(user_id);`
* `find_all_changesets();`
* `find_single_repository_changesets(repo_id);`
* `find_single_changeset(repo_id, revision);`
* `find_all_comments(repo_id);`
* `find_all_changeset_comments(repo_id, revision);`
* `find_single_comment(repo_id, comment_id);`
* `create_comment(repo_id, revision_id, body, file_path, line_number);`
* `find_all_server_environments(repo_id);`
* `find_single_server_environment(repo_id, environment_id);`
* `create_server_environment(repo_id, name, automatic);`
* `update_server_environment(repo_id, environment_id, params);`
* `find_all_release_servers(repo_id, environment_id);`
* `find_single_release_server(repo_id, server_id);`
* `create_release_server(repo_id, environment_id, name, local_path, remote_path, remote_addr, protocol, port, login, password);`
* `update_release_server(repo_id, server_id, params);`
* `delete_release_server(repo_id, server_id);`
* `find_all_releases(repo_id);`
* `find_single_release(repo_id, release_id);`
* `create_release(repo_id, revision_id);`
* `retry_release(repo_id, release_id);`

Example simple test file:

	<?php
		require_once('libraries/beanstalk_api.php')
		$beanstalk = new beanstalk_api(array('account_name' => 'myaccount', 'username' => 'chris', 'password' => 'pass'));
		
		$account_details = $beanstalk->get_account_details();
		
		var_dump($account_details);
	?>

## Further info ##
Detailed documentation about the API can be found on the Beanstalk website at http://api.beanstalkapp.com/