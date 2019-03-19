# Linux---How-to-configure-raid-1-in-LVM
Linux - How to configure raid-1 in LVM

lvs -o+devices --segments <vg_data/lv_opt_data>

pvcreate </dev/sdc>

vgextend <vg_data> </dev/sdc>

lvconvert -m1 <vg_data/lv_opt/data> </dev/sdc>

lvs <vg_data/lv_opt_data>
