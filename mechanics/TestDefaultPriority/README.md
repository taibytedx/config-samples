## Model/Submodel/Attribute Inheritance

### Sample project to test what takes precedence and gets in the payload when the there is an overlap between the following:
- Default value assigned to a Simple Attribute in a Model
- Default value assigned to a Simple Attribute in an Instance
- Default object value assigned to a Modeled Attribute in a Model
- Default object value assigned to a Modeled Attribute in an Instance
- Reference/Expression value mapped to a Simple Attribute in an Instance
- Reference/Expression value mapped to a Modeled Attribute in an Instance

### Findings
Lowest level definition takes precedence
1. Lower level mapped Reference/Expression
2. Lower level assigned Default value

#### Example precedence for 2 level structure:
1. Instance Attribute Reference
2. Instance Attribute Default
3. Model Attribute Default
4. Instance Branch object Reference
5. Instance Branch object Default
6. Model Branch object Default

<img width="1508" height="832" alt="image" src="https://github.com/user-attachments/assets/e908d15f-fa0b-4921-a57d-90d3fa6353ee" />

### The attribute naming is structured as follows:
#### Example attribute: 
```
childModelDef0InstanceDef0Ref1
```
- child: either child leaf or parent branch
- ModelDef0/1: Model default value is empty or populated
- InstanceDef0/1: Instance Attribute Default empty or populated
- InstanceRef0/1: Instance Attribute Reference empty or populated

