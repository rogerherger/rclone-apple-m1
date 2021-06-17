# Mount Google Cloud Storage Buckets on Apple M1 via CLI

This tutorial describes how to mount a Google Cloud Storage (GCS) bucket on Apple M1 via command line interface (CLI) using `rclone`.

## Get `rclone`

Download rclone binary for Apple's ARM architecture on the rclone download page. Choose the 64 bit ARM version for Apple M1.
https://rclone.org/downloads/

Unpack and copy the binary to a typical folder, e.g., 
`/usr/local/bin/`

Check that you see the binary

```
% which rclone
/usr/local/bin/rclone
```


Enable `rclone` by, e.g., checking the version

`% rclone version`

Go to `System Preferences` and allow `rclone`


## Configure `rclone`

Follow the steps on rclone homepage to configure rclone for GCS buckets. Call

`% rclone config`

and follow the steps on

https://rclone.org/googlecloudstorage/

Check that your configuration is working properly and you can access your bucket(s) on GCS
```
% rclone lsd remote:
          -1 2021-06-17 08:58:33        -1 <yourbucket1>
          -1 2021-06-17 08:58:33        -1 <yourbucket2>
```

## Mount your GCS buckets

Create local folders as mount points
```
% mkdir <youlocalbucket1>
% mkdir <yourlocalbucket2>
```

Use 
```
% rclone mount --daemon remote:<yourbucket1> <yourlocalbucket1>
% rclone mount --daemon remote:<yourbucket1> <yourlocalbucket1>
```
to mount your buckets to your local folders. The `--daemon` option prevents rclone from running in the foreground.

You're all set!


