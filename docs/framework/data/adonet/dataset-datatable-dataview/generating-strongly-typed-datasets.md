---
title: Generowanie silnie typizowanych elementów DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 25883b7be10c68e527e4e04182b7162574b994d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149633"
---
# <a name="generating-strongly-typed-datasets"></a>Generowanie silnie typizowanych elementów DataSet
Biorąc pod uwagę schematu XML, który jest zgodny z języka definicji schematu XML (XSD) standard, możesz wygenerować silnie typizowaną <xref:System.Data.DataSet> korzystania z narzędzia XSD.exe dołączonym [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].  
  
 (Aby utworzyć xsd z tabel bazy danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Praca z zestawami danych w programie Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).  
  
 Poniższy kod przedstawia składnię do generowania **DataSet** za pomocą tego narzędzia.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 W tej składni `/d` dyrektywy informuje narzędzie w celu wygenerowania **DataSet**i `/l:` nakazuje narzędziu język do użycia (na przykład w języku C# lub Visual Basic .NET). Opcjonalny `/eld` dyrektywa określa, że można użyć [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] do wykonywania zapytań względem wygenerowany **zestawu danych.** Ta opcja jest używana podczas `/d` jest także określona opcja. Aby uzyskać więcej informacji, zobacz [zapytań wpisanych zestawów danych](../../../../../docs/framework/data/adonet/querying-typed-datasets.md). Opcjonalny `/n:` dyrektywy informuje o narzędzia można również wygenerować przestrzeni nazw **DataSet** o nazwie **XSDSchema.Namespace**. Dane wyjściowe polecenia jest XSDSchemaFileName.cs, który zostanie skompilowany i używane w aplikacji ADO.NET. Wygenerowany kod może być kompilowane jako bibliotekę lub modułu.  
  
 Poniższy kod przedstawia składnię do kompilowania wygenerowanego kodu jako biblioteki za pomocą kompilatora C# (csc.exe).  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` Dyrektywy informuje o narzędzia do kompilowania w bibliotece i `/r:` dyrektywy Określ zależne biblioteki wymaganego do skompilowania. Dane wyjściowe polecenia jest XSDSchemaFileName.dll, które mogą być przekazywane do kompilator podczas kompilowania aplikacji ADO.NET za pomocą `/r:` dyrektywy.  
  
 Poniższy kod przedstawia składnię do uzyskiwania dostępu do przestrzeni nazw, przekazywane do XSD.exe w aplikacji ADO.NET.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 Poniższy przykład kodu wykorzystuje wpisane **DataSet** o nazwie **CustomerDataSet** załadować listę klientów z **Northwind** bazy danych. Po załadowaniu danych za pomocą **wypełnienia** metody przykład w pętli każdego klienta w **klientów** tabeli, używając wpisanego **CustomersRow** ( **DataRow**) obiektu. To zapewnia bezpośredni dostęp do **CustomerID** kolumny, w przeciwieństwie do za pomocą **DataColumnCollection**.  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 Poniżej przedstawiono schematu XML, używany dla przykładu.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Typizowane elementy DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
