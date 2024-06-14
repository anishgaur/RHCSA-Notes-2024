## File and Directory Commands
The following is a list of CLI commands that you must be familiar with for the RHCSA 9 examination. These commands were based on the video and textual course from Sander Van Vugt.

## Find Command

- `find /path -name filename -type f/d -exec command {}\;`: This is a find command with the -exec option that triggers a command. The `{}` are placeholders for the filenames resulting from the search.

## Tar Commands

- `tar cvf /archive.tar /targetstoarchive`: This command compresses files.
- `tar xvf /archive.tar /extraction/path`: This command extracts files from the archive.
- `tar tvf /archive.tar`: This command allows you to view the contents of the archive.
- `tar rvf`: This command appends new files to a preexisting archive.
- `tar cvfz /archive.gz /targetstoarchive`: This command uses gzip compression.
- `tar cvfJ /archive.xz /targetstoarchive`: This command uses xz compression.
- `tar cvfj /archive.bz2 /targetstoarchive`: This command uses bzip2 compression.

## Awk Command

- `awk -F : '{command}' file`: The `-F` is used for specifying the field separator. For example, `awk -F : '{print$1, $3}' file.txt` prints out the first and third column in file.txt. It uses `:` as a field separator for recognizing different columns in the file. Without specifying `:` as the field separator, it will use a space to determine columns.

## Sed Commands

- `sed -i s/searchterm/replacement/g file`: This command is used to replace a specific term in a file. The `-i` makes certain that the changes are written to the file immediately. The `g` specifies that the changes need to be applied to all instances of the search term.
- `sed -i '10d' file`: This command is used to delete the 10th line in a file. The `-i` functions the same as the statement above.

## User and Group Commands

- `useradd <username> -s /sbin/nologin`: This command adds a user to the system. The `-s` sets the login shell. `/sbin/nologin` sets the shell so that no login might take place.
- `usermod -aG groupname user`: This command adds the user to the group `groupname` as a secondary group. The `-a` appends instead of replacing the secondary group.
- `usermod -L user`: This command locks the user.
- `usermod -U user`: This command unlocks the user.
- `usermod -e user`: This command sets the account expiration date.
- `passwd -l user`: This command locks the password.
- `passwd -u  user`: This command unlocks the password.
- `usermod -s /sbin/nologin user`: The `-s` specifies the path of the user's new login shell. `/sbin/nologin` specifies the message that refuses login access to the user.
- `lid -g groupname`: This command lists all members belonging to that group.

## Chage Command

- `chage user`: This command changes user password properties such as minimum time before password change, maximum age of a password, and password expiration.

## Chmod Commands

- `chmod g+s .`: This command applies setgid permission on a directory allowing the ones that are created in it to inherit group ownership.
- `chmod +t .`: This command applies sticky bit to a file or a directory.

## Hostnamectl Command

- `hostnamectl set-hostname`: This command changes the host name. It can be changed through the editing of the `/etc/hostname` file or through the `nmtui` command.

## Nmcli Commands

- `nmcli`: This command is a network manager command line interface.
- `nmcli connection up connectionname`: This command reestablishes connection.

## Ss Commands

- `ss -tu`: This command shows TCP packets.
- `ss -tuna`: This command shows UDP packets.
- `ss -tunap`: This command does not resolve service names. It displays all sockets and shows the process using sockets.

## Rpm Commands

- `rpm -qa`: This command shows all installed packages.
- `rpm -qf filename`: This command shows from which package `filename` was installed.
- `rpm -ql packagename`: This command lists all files from a package.
- `rpm -q --scripts packagename`: This command shows scripts executed while installing a package.
- `rpm -q --changelog package`: This command shows the changelog for a package.

## Rpm2cpio Commands

- `rpm2cpio packagename.rpm | cpio -idmv`: This command converts the RPM package into a CPIO data stream. The `-idmv` will list the files in the package while they are being extracted to the current directory.
- `rpm2cpio packagename.rpm | cpio -tv`: This command lists the contents of a package without extracting them.

## Dnf Commands

- `dnf config-manager --enable reponame`: This command is used to enable a specific repository.
- `dnf config-manager --add-repo=file:///path/to/repo`: This command is used to add a 3rd party repo.
- `dnf list`: This command lists all packages.
- `dnf list searchterm`: This command lists all packages that match `searchterm`.
- `dnf search`: This command searches in names and memory.
- `dnf search all`: This command includes searching in description.
- `dnf provides */searchterm`: This command searches in package file list for the package.
- `dnf info`: This command provides information about a package.
- `dnf install`: This command installs a package.
- `dnf remove`: This command removes a package.
- `dnf update`: This command updates a package.
- `dnf repoquery`: This command queries a package in a repository.
- `dnf download`: This command downloads a package.
- `dnf history`: This command gives an overview of dnf activity.
- `dnf history undo x`: This command reverses an action.

## Lscpu Command

- `lscpu`: This command gives information regarding the CPU.

## Uptime Command

- `uptime`: This command checks CPU usage.

## Nice and Renice Commands

- `nice -n <priority> -p <PID>`: This command sets the priority of a process.
- `renice -n <priority> -p <PID>`: This command changes the priority of a process.

## Kill Command

- `kill -SIGCHLD <pidoftheparentprocess>`: This command sends a signal to the parent process to remove a zombie process.

## Tuned-adm Commands

- `tuned-adm list`: This command presents a list of all the profiles available.
- `tuned-adm profile profilename`: This command instructs tuned to apply a new profile.

## Loginctl Commands

- `loginctl list-users`: This command gives a list of active users.
- `loginctl list-sessions`: This command gives a list of active sessions along with the users.
- `loginctl terminate-session`: This command terminates a specific user session.
- `loginctl terminate-user`: This command ends all user sessions of that particular user.
- `loginctl user-status username`: This command gives the user's status.

## Systemctl Commands

- `systemctl list-units`: This command is used to display a list of all active units that systemd currently knows about.
- `systemctl list-unit -t timer`: This command lists units of a particular type.
- `systemctl list-unit-files`: This command lists installed unit files.
- `systemctl status servicename`: This command shows the status of a service.
- `systemctl start servicename`: This command starts a service.
- `systemctl stop servicename`: This command stops a service.
- `systemctl enable servicename`: This command enables a service.
- `systemctl disable servicename`: This command disables a service.
- `systemctl reload servicename`: This command reloads a service.
- `systemctl restart systemd-journald-flush`: This command reloads the new systemd-journal parameters.
- `systemctl unit-dependencies servicename`: This command lists all dependencies of any services.
- `systemctl isolate xyz.target`: This command switches to the targeted interface.
- `systemctl get-default`: This command shows the current default target.
- `systemctl set-default`: This command changes the current default target.
- `systemctl.unit=xxx.target`: This command from the Grub 2 boot prompt allows the user to boot into a specific target.
- `systemctl enable --now debug-shell.service`: This command enables the debug-shell to be used at boot. It can be disabled after use.
- `systemctl --user`: This command is used to interact with systemd user instance.

## Mount Command

- `mount -o remount,rw /`: The `-o` specifies mounting options. `remount,rw /` mounts the root file system as read-write.

## Ssh Commands

- `ssh-keygen`: This command generates a public/private key pair.
- `ssh-copy-id <targetip>`: This command copies the private key over to the target server. The format can be `username@targetip`.
- `ssh -X`: This command enables X forwarding.
- `ssh -Y`: This command enables trusted X forwarding.

## Scp Commands

- `scp /path/to/local/file user@remote_server:/path/to/destination`: This command copies a file from the local machine to the remote server.
- `scp user@remote_server:/path/to/remote/file path/to/local/destination`: This command

## Docker/Podman Commands
RHEL 9 uses podman to manage containers instead of docker. Due to its nature, these commands are interchangeable with podman. Installing docker on RHEL 9 takes a few extra steps. Given these commands will work for both podman and docker I would suggest sticking to podman. Substitute docker for podman in the following commands in RHEL9.

- `docker pull imagename`: Allows for docker to pull an image from the registery.
- `docker images`: Lists available container images to run locally. 
- `docker run`: Execution command for docker. 
- `docker run -d -p hostport:containerport -v volumename:containterdirectory:Z -i -t --mount source=/location,destination=/location --name nameforthecontainer -e environmentvariables --rm true|false containerimagename` : -d allows for detached deployment, -p allows for port binding of the containers, -v allows for volume mount, --mount allow for mount bind, :Z|z sets SELinux context label, --name specifiies a custom name for the container, --rm allow for automatic removal of the container after it has finished execution running, -i allows for an interactive container and -t allows for a virtual console and -e allows for passing certain environment variables like passwords to be passed the container.
- `docker attach containername` : Allows to jump back in the container once it is running. 
- `docker start containername`: This commands starts a container that is already loaded in or stopped. 
- `docker stop containtername`: This command stops a running container. 
- `docker ps -a`: This command shows a list of running containers. -a displays all containers, even the stopped ones.
- `docker rm containername`: This command removes a stopped container.
- `docker volume create`: This command creates a volume specifically for container use.