---
title: Generowanie silnie typizowanych elementów DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 9accfb68c57384e12a59bae40ebe30a2d3e22877
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526491"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="8878f-102">Generowanie silnie typizowanych elementów DataSet</span><span class="sxs-lookup"><span data-stu-id="8878f-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="8878f-103">Biorąc pod uwagę schematu XML, który jest zgodny z języka definicji schematu XML (XSD) standard, możesz wygenerować silnie typizowaną <xref:System.Data.DataSet> korzystania z narzędzia XSD.exe dołączonym [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8878f-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="8878f-104">(Aby utworzyć xsd z tabel bazy danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Praca z zestawami danych w programie Visual Studio](https://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span><span class="sxs-lookup"><span data-stu-id="8878f-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](https://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
 <span data-ttu-id="8878f-105">Poniższy kod przedstawia składnię do generowania **DataSet** za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="8878f-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="8878f-106">W tej składni `/d` dyrektywy informuje narzędzie w celu wygenerowania **DataSet**i `/l:` nakazuje narzędziu język do użycia (na przykład w języku C# lub Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="8878f-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="8878f-107">Opcjonalny `/eld` dyrektywa określa, że można użyć [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] do wykonywania zapytań względem wygenerowany **zestawu danych.**</span><span class="sxs-lookup"><span data-stu-id="8878f-107">The optional `/eld` directive specifies that you can use [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] to query against the generated **DataSet.**</span></span> <span data-ttu-id="8878f-108">Ta opcja jest używana podczas `/d` jest także określona opcja.</span><span class="sxs-lookup"><span data-stu-id="8878f-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="8878f-109">Aby uzyskać więcej informacji, zobacz [zapytań wpisanych zestawów danych](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="8878f-109">For more information, see [Querying Typed DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="8878f-110">Opcjonalny `/n:` dyrektywy informuje o narzędzia można również wygenerować przestrzeni nazw **DataSet** o nazwie **XSDSchema.Namespace**.</span><span class="sxs-lookup"><span data-stu-id="8878f-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="8878f-111">Dane wyjściowe polecenia jest XSDSchemaFileName.cs, który zostanie skompilowany i używane w aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8878f-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="8878f-112">Wygenerowany kod może być kompilowane jako bibliotekę lub modułu.</span><span class="sxs-lookup"><span data-stu-id="8878f-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="8878f-113">Poniższy kod przedstawia składnię do kompilowania wygenerowanego kodu jako biblioteki za pomocą kompilatora C# (csc.exe).</span><span class="sxs-lookup"><span data-stu-id="8878f-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="8878f-114">`/t:` Dyrektywy informuje o narzędzia do kompilowania w bibliotece i `/r:` dyrektywy Określ zależne biblioteki wymaganego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="8878f-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="8878f-115">Dane wyjściowe polecenia jest XSDSchemaFileName.dll, które mogą być przekazywane do kompilator podczas kompilowania aplikacji ADO.NET za pomocą `/r:` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="8878f-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="8878f-116">Poniższy kod przedstawia składnię do uzyskiwania dostępu do przestrzeni nazw, przekazywane do XSD.exe w aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8878f-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="8878f-117">Poniższy przykład kodu wykorzystuje wpisane **DataSet** o nazwie **CustomerDataSet** załadować listę klientów z **Northwind** bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8878f-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="8878f-118">Po załadowaniu danych za pomocą **wypełnienia** metody przykład w pętli każdego klienta w **klientów** tabeli, używając wpisanego **CustomersRow** ( **DataRow**) obiektu.</span><span class="sxs-lookup"><span data-stu-id="8878f-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="8878f-119">To zapewnia bezpośredni dostęp do **CustomerID** kolumny, w przeciwieństwie do za pomocą **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="8878f-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="8878f-120">Poniżej przedstawiono schematu XML, używany dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="8878f-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8878f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8878f-121">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="8878f-122">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="8878f-122">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="8878f-123">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="8878f-123">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="8878f-124">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="8878f-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
