---
title: Generowanie silnie Typizowane zbiory danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 95bb536416a043fc392d0c4e94378239ae3ee37f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="generating-strongly-typed-datasets"></a>Generowanie silnie Typizowane zbiory danych
Podany schemat XML, który jest zgodny ze schematu XML definicji języka (XSD) standard, można wygenerować silnie typizowaną <xref:System.Data.DataSet> przy użyciu dostarczonego z narzędzia XSD.exe [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].  
  
 (Aby utworzyć xsd z tabel bazy danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Praca z zestawami danych w programie Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).  
  
 Poniższy kod przedstawia składnię generowania **zestawu danych** za pomocą tego narzędzia.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 W tej składni `/d` dyrektywy informuje narzędzie do generowania **DataSet**i `/l:` informuje narzędzie język do użycia (na przykład C# i Visual Basic .NET). Opcjonalny `/eld` dyrektywa określa, czy możesz używać [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] do zapytania dotyczącego wygenerowany **zestawu danych.** Ta opcja jest używana podczas `/d` jest także określona opcja. Aby uzyskać więcej informacji, zobacz [zapytań wpisanych zestawów danych](../../../../../docs/framework/data/adonet/querying-typed-datasets.md). Opcjonalny `/n:` dyrektywy informuje narzędzie do generowania również przestrzeń nazw dla **DataSet** o nazwie **XSDSchema.Namespace**. Dane wyjściowe polecenia jest XSDSchemaFileName.cs, który może być skompilowany i używane w aplikacji ADO.NET. Wygenerowany kod, mogą być kompilowane jako modułu lub biblioteki.  
  
 Poniższy kod przedstawia składnię kompilowania wygenerowanego kodu jako bibliotekę przy użyciu kompilatora C# (csc.exe).  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` Dyrektywy informuje narzędzie do kompilowania w bibliotece i `/r:` dyrektywy Określ zależnej biblioteki wymagane do kompilacji. Dane wyjściowe polecenia jest XSDSchemaFileName.dll, które mogą zostać przekazane do kompilatora podczas kompilowania aplikacji ADO.NET z `/r:` dyrektywy.  
  
 Poniższy kod przedstawia składnię do uzyskiwania dostępu do aplikacji ADO.NET przekazano XSD.exe przestrzeni nazw.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 Poniższy przykład kodu wykorzystuje maszynowy **DataSet** o nazwie **CustomerDataSet** można załadować listy klientów z **Northwind** bazy danych. Po załadowaniu danych przy użyciu **wypełnienia** metody przykładzie pętli każdego klienta w **klientów** tabeli, używając wpisanego **CustomersRow** ( **Element DataRow**) obiektu. To zapewnia bezpośredni dostęp do **CustomerID** kolumny, w przeciwieństwie do za pomocą **DataColumnCollection**.  
  
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
  
 Poniżej znajduje się schematu XML używanego w przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [Typizowane elementy DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
