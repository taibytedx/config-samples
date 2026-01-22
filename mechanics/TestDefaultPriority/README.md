## Model/Submodel/Attribute Inheritance

<img width="1508" height="832" alt="image" src="https://github.com/user-attachments/assets/e908d15f-fa0b-4921-a57d-90d3fa6353ee" />

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
1. Instance Simple Attribute Reference
2. Instance Simple Attribute Default
3. Model Simple Attribute Default
4. Instance Modeled Attribute (Branch) Reference
5. Instance Modeled Attribute (Branch) Default
6. Model Modeled Attribute (Branch) Default

### The attribute naming is structured as follows:
#### Example attribute: 
```
childModelDef0InstanceDef0Ref1
```
- child: either child leaf or parent branch
- ModelDef0/1: Model default value is empty or populated
- InstanceDef0/1: Instance Attribute Default empty or populated
- InstanceRef0/1: Instance Attribute Reference empty or populated

#### Wherever the Instance Attribute has a Reference/Expression populated, that will always resolve as shown where all attribute that end in "...Ref1":
<img width="1181" height="1038" alt="image" src="https://github.com/user-attachments/assets/9e9e9cde-be83-45ab-86ea-bb4878406245" />

#### If there is no Instance Attribute Reference/Expression, then its Default value will resolve:
<img width="703" height="825" alt="image" src="https://github.com/user-attachments/assets/b2f41f35-1372-4924-9a22-011c41533970" />

#### If there is no Instance Attribute Default or Reference/Expression value, then the Model Attribute Default will resolve:
<img width="713" height="829" alt="image" src="https://github.com/user-attachments/assets/68248e7d-9d45-44db-9c76-ef11d2a58cbb" />

#### If there is none of Model Attribute Default, Instance Default/Reference, then the Branch object that has a property with the same name as the Attribute will get resolved:
<img width="706" height="825" alt="image" src="https://github.com/user-attachments/assets/4b7aa452-2833-448e-85fb-da088ae8668c" />

#### If there is no Branch object Reference/Expression, then its Default value is next:
<img width="714" height="831" alt="image" src="https://github.com/user-attachments/assets/b515f0aa-98ab-4835-a1dc-ffa7db441110" />

#### Then the Branch object's Models Default:
<img width="707" height="832" alt="image" src="https://github.com/user-attachments/assets/b32f1182-fda3-4986-91f0-3839984fb482" />

#### The very last object where all the values are populated may be the most immediately helpful.
- The branch has the Model, InstanceDef and Instance Ref populated.
- The leaf attributes show the various permutations and what ends up getting resolved.

<img width="695" height="216" alt="image" src="https://github.com/user-attachments/assets/228d8bab-64da-4dbc-a17a-f3f15767ee41" />
