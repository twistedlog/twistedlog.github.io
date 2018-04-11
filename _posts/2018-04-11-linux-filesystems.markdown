---
layout: post
title: "Linux filesystems"
date: 2018-04-11 15:03:00 +0530
categories: linux filesystems
---
Down the rabbit hole of linux filesystems.

VFS interface calls mapping

checkout the [Code][github-ex2-file.c]
{% highlight c %}
const struct file_operations ext2_file_operations = {
	.llseek		= generic_file_llseek,
	.read_iter	= ext2_file_read_iter,
	.write_iter	= ext2_file_write_iter,
	.unlocked_ioctl = ext2_ioctl,
#ifdef CONFIG_COMPAT
	.compat_ioctl	= ext2_compat_ioctl,
#endif
	.mmap		= ext2_file_mmap,
	.open		= dquot_file_open,
	.release	= ext2_release_file,
	.fsync		= ext2_fsync,
	.get_unmapped_area = thp_get_unmapped_area,
	.splice_read	= generic_file_splice_read,
	.splice_write	= iter_file_splice_write,
};
{% endhighlight %}

[github-ex2-file.c]: https://github.com/torvalds/linux/blob/master/fs/ext2/file.c#L182
