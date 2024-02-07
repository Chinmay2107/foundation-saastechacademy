### Overview of Product Feature Management Entities

UDM offers framework for managing product features and specifications. Key to this functionality are several interrelated entities: Product, ProductFeature, ProductFeatureType, ProductFeatureAppl, and ProductFeatureApplType.

#### 1. Product Entity
**Purpose**: Represents items for sale or use.

**Key Attributes**:
- Product ID: Unique identifier.
- Product Name.
- Description.
- Product Type.
- Price.
- Quantity.

#### 2. ProductFeature Entity
**Purpose**: Specifies attributes or characteristics of a product.

**Key Attributes**:
- Product Feature ID: Unique identifier.
- Feature Type: Linked to ProductFeatureType.
- Description.

#### 3. ProductFeatureType Entity
**Purpose**: Classifies product features.

**Key Attributes**:
- Product Feature Type ID: Unique identifier.
- Description.

#### 4. ProductFeatureAppl Entity
**Purpose**: Links a ProductFeature to a Product, facilitating a many-to-many relationship.

**Key Attributes**:
- Product ID.
- Product Feature ID.
- From Date and Thru Date: Applicability period.
- Sequence Number.
- Amount.

#### 5. ProductFeatureApplType Entity
**Purpose**: Defines the nature of feature application to a product.

**Key Attributes**:
- Product Feature Appl Type ID: Unique identifier.
- Description.

#### Common ProductFeatureApplType Values:
1. **DISTINGUISHING_FEAT**: For unique or characteristic features that distinguish one product from another.
2. **OPTIONAL_FEATURE**: Represents add-on features that are not essential but can be chosen by the user.
3. **REQUIRED_FEATURE**: Essential features necessary for the product’s operation.
4. **SELECTABLE_FEATURE**: Features that offer multiple options, requiring a selection.
5. **STANDARD_FEATURE**: Standard features included in every unit of the product.

### Utilizing Entities for Product Feature Definition

1. **Define ProductFeatureType**: Classify the feature.
2. **Define ProductFeature**: Create a feature with specific details.
3. **Link Feature to Product using ProductFeatureAppl**: Associate the feature with a product, detailing applicability and sequence.
4. **Specify Feature Application using ProductFeatureApplType**: Clarify the nature of the feature's application, whether it's standard, optional, required, distinguishing, or selectable.

**Discuss** ProductFeatureAppl and ProductFeatureApplType entities and analyse similarity with ProductAssoc and ProductAssocType entities.

* ProductFeatureAppl entity is used to establish relationship between **Product** and **ProductFeature** entity.
Many products can have multiple features governing many to many relationship
* ProductFeatureApplType entity defines the meta data or characteristics of a product feature, It can be **OPTIONAL_FEATURE, REQUIRED_FEATURE, SELECTABLE_FEATURE, STANDARD_FEATURE**
* Similarly, **ProductAssoc** is ued to establish relationship between multiple Products. A product can be related to another product with some several types **For example: Complementary Product, Also Bought Together, Upgrade Product, Product Variant**. These types are defined in **ProductAssocType** entity 

**Define** Men's Denim Pants product that is available in 3 colors (Light Blue, Nevy, Black) and 4 sizes (28, 30, 32, 34)
```json
{
  "Product": {
    "ProductID": "1002",
    "ProductName": "Men's Denim Pants",
    "Description": "Comfortable and stylish blue denim pants for men",
    "ProductType": "Clothing",
    "Price": 60.00,
    "Quantity": 600
  },
  "ProductFeature": [
    {
      "ProductFeatureID": "20001",
      "FeatureType": "30001",
      "Description": "28"
    },
    {
      "ProductFeatureID": "20002",
      "FeatureType": "30002",
      "Description": "30"
    },
    {
      "ProductFeatureID": "20003",
      "FeatureType": "30003",
      "Description": "32"
    },
    {
      "ProductFeatureID": "20004",
      "FeatureType": "30004",
      "Description": "34"
    },
    {
      "ProductFeatureID": "20005",
      "FeatureType": "30005",
      "Description": "Light Blue"
    },
    {
      "ProductFeatureID": "20006",
      "FeatureType": "30006",
      "Description": "Nevy Blue"
    },
    {
      "ProductFeatureID": "20007",
      "FeatureType": "30007",
      "Description": "Black"
    }
  ],
  "ProductFeatureTypes": [
    {
      "ProductFeatureTypeID": "30001",
      "Description": "Size"
    },
    {
      "ProductFeatureTypeID": "30002",
      "Description": "Size"
    },
    {
      "ProductFeatureTypeID": "30003",
      "Description": "Size"
    }
    {
      "ProductFeatureTypeID": "30004",
      "Description": "Color"
    },
    {
      "ProductFeatureTypeID": "30005",
      "Description": "Color"
    },
    {
      "ProductFeatureTypeID": "30006",
      "Description": "Color"
    }
  ],
  "ProductFeatureAppl": [
    {
      "ProductID": "1002",
      "ProductFeatureID": "20001",
      "FromDate": "2024-02-01",
      "ThruDate": "2024-02-01",
      "SequenceNumber": 1,
      "Amount": null,
      "ProductFeatureApplTypeID": "40001"
    },
    {
      "ProductID": "1002",
      "ProductFeatureID": "20002",
      "FromDate": "2024-02-01",
      "ThruDate": "2024-02-01",
      "SequenceNumber": 2,
      "Amount": null,
      "ProductFeatureApplTypeID": "40002"
    },
    {
      "ProductID": "1002",
      "ProductFeatureID": "20003",
      "FromDate": "2024-02-01",
      "ThruDate": "2024-02-01",
      "SequenceNumber": 3,
      "Amount": null,
      "ProductFeatureApplTypeID": "40003"
    },
    {
      "ProductID": "1002",
      "ProductFeatureID": "20004",
      "FromDate": "2024-02-01",
      "ThruDate": "2024-02-01",
      "SequenceNumber": 4,
      "Amount": null,
      "ProductFeatureApplTypeID": "40004"
    },
    {
      "ProductID": "1002",
      "ProductFeatureID": "20005",
      "FromDate": "2024-02-01",
      "ThruDate": "2024-02-01",
      "SequenceNumber": 5,
      "Amount": null,
      "ProductFeatureApplTypeID": "40005"
    },
    {
      "ProductID": "1002",
      "ProductFeatureID": "20006",
      "FromDate": "2024-02-01",
      "ThruDate": "2024-02-01",
      "SequenceNumber": 6,
      "Amount": null,
      "ProductFeatureApplTypeID": "40006"
    }
  ],
  "ProductFeatureApplTypes": [
    {
      "ProductFeatureApplTypeID": "40001",
      "Description": "SELECTABLE_FEATURE"
    },
    {
      "ProductFeatureApplTypeID": "40002",
      "Description": "SELECTABLE_FEATURE"
    },
    {
      "ProductFeatureApplTypeID": "40003",
      "Description": "SELECTABLE_FEATURE"
    },
    {
      "ProductFeatureApplTypeID": "40004",
      "Description": "SELECTABLE_FEATURE"
    },
    {
      "ProductFeatureApplTypeID": "40005",
      "Description": "SELECTABLE_FEATURE"
    },
    {
      "ProductFeatureApplTypeID": "40006",
      "Description": "SELECTABLE_FEATURE"
    }
  ]
}
```
  
**Write SQL** to select all available sizes for each color
```sql
SELECT
	pf1.DESCRIPTION as Size,
	pf.DESCRIPTION as Color
FROM
	Product_Feature_Type pft1
JOIN Product_Feature pf on
	pft1.PRODUCT_FEATURE_TYPE_ID = pf.PRODUCT_FEATURE_TYPE_ID
	and pft1.PRODUCT_FEATURE_TYPE_ID = "COLOR"
JOIN Product_Feature pf1 ON
	pft1.PRODUCT_FEATURE_TYPE_ID = pf.PRODUCT_FEATURE_TYPE_ID
	AND pf1.DESCRIPTION IN (SELECT DESCRIPTION FROM Product_Feature WHERE Product_Feature.PRODUCT_FEATURE_TYPE_ID="SIZE" and DESCRIPTION>0);
```
