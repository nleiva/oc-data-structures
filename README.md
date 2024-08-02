# OpenConfig Go data structures for public consumption

To run demos in the Go Playground for example.

## Generating Go binding from YANG models

The Go generated code in the features folder is the result of the following ([PR](https://github.com/openconfig/ygot/issues/977)):

1. Clone YANG models and instal YGOT's code generator. 

```bash
./clone.sh
```

### VLANs

2. Run the generator for a handful of YANG models.

```bash
generator -path=yang \
  -output_file=features/vlan/oc.go \
  -package_name=oc -generate_fakeroot -fakeroot_name=device -compress_paths=true \
  -shorten_enum_leaf_names \
  -trim_enum_openconfig_prefix \
  -typedef_enum_with_defmod \
  -enum_suffix_for_simple_union_enums \
  -exclude_modules=ietf-interfaces \
  -generate_rename \
  -generate_append \
  -generate_getters \
  -generate_leaf_getters \
  -generate_populate_defaults \
  -generate_simple_unions \
  yang/openconfig/network-instance/openconfig-network-instance.yang \
  yang/openconfig/interfaces/openconfig-interfaces.yang \
  yang/openconfig/interfaces/openconfig-if-ip.yang \
  yang/openconfig/vlan/openconfig-vlan.yang
```