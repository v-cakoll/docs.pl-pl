---
title: Generowanie silnie typizowanych elementów DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: f1c1fd77bed700fae8e5a658da8b267120518ca9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786307"
---
# <a name="generating-strongly-typed-datasets"></a>Generowanie silnie typizowanych elementów DataSet
W przypadku schematu XML, który jest zgodny ze standardem XML schematu definicji języka (XSD), można wygenerować silnie wpisaną <xref:System.Data.DataSet> przy użyciu narzędzia XSD. exe dostępnego w zestawie Windows Software Development Kit (SDK).  
  
 (Aby utworzyć XSD z tabel baz danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Working with datasetss in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).  
  
 Poniższy kod przedstawia składnię generowania **zestawu danych** za pomocą tego narzędzia.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 W `/d` tej składni, dyrektywa informuje narzędzie do wygenerowania **zestawu danych**, a także `/l:` informuje narzędzie o języku, który ma być używany (na przykład C# lub Visual Basic .NET). Opcjonalna `/eld` dyrektywa określa, że można użyć LINQ to DataSet do wykonywania zapytań względem wygenerowanego **zestawu danych.** Ta opcja jest używana, `/d` Jeśli określono również opcję. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących wpisanych zestawów danych](../querying-typed-datasets.md). Opcjonalna `/n:` dyrektywa informuje narzędzie, aby wygenerowało również przestrzeń nazw dla **zestawu danych** o nazwie **XSDSchema. Namespace**. Dane wyjściowe polecenia to XSDSchemaFileName.cs, które mogą być kompilowane i używane w aplikacji ADO.NET. Wygenerowany kod można skompilować jako bibliotekę lub moduł.  
  
 Poniższy kod przedstawia składnię kompilowania wygenerowanego kodu jako biblioteki przy użyciu C# kompilatora (CSC. exe).  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 Dyrektywa informuje narzędzie do skompilowania do biblioteki, `/r:` a dyrektywy określają zależne biblioteki wymagane do skompilowania. `/t:` Dane wyjściowe polecenia to XSDSchemaFileName. dll, które mogą być przekazywane do kompilatora podczas kompilowania aplikacji ADO.NET z `/r:` dyrektywą.  
  
 Poniższy kod przedstawia składnię dostępu do przestrzeni nazw przekazaną do pliku XSD. exe w aplikacji ADO.NET.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 Poniższy przykład kodu używa określonego **zestawu danych** o nazwie **CustomerDataSet** , aby załadować listę klientów z bazy danych **Northwind** . Gdy dane zostaną załadowane przy użyciu metody **Fill** , przykład przeprowadzi pętlę przez każdego klienta w tabeli **Customers** przy użyciu określonego obiektu **CustomersRow** (**DataRow**). Zapewnia to bezpośredni dostęp do kolumny **CustomerID** , w przeciwieństwie do za pośrednictwem elementu **DataColumnCollection**.  
  
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
  
 Poniżej znajduje się schemat XML użyty dla przykładu.  
  
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
- [Typizowane elementy DataSet](typed-datasets.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
