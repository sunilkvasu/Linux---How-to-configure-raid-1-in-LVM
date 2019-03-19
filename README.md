# Linux---How-to-configure-raid-1-in-LVM
Linux - How to configure raid-1 in LVM

lvs -o+devices --segments <vg_data/lv_opt_data>

pvcreate </dev/sdc>

vgextend <vg_data> </dev/sdc>

lvconvert -m1 <vg_data/lv_opt/data> </dev/sdc>

lvs <vg_data/lv_opt_data>



# Replace failed disk in LVM
Scenario - 1 Faulty disk is still live:

lvconvert --replace /dev/sdb /dev/mapper/vg_data-lv_opt_data /dev/sdc


Scenario - 2 Faulty disk is completele dead:

vgreduce --removemissing <vg_data>

lvconvert -m0 </dev/mapper/vg_data-lv_opt_data>

pvcreate </dev/sdc>

vgextend <vg_data> </dev/sdc>

lvconvert -m1 <vg_data/lv_opt/data> </dev/sdc>

lvs <vg_data/lv_opt_data>

