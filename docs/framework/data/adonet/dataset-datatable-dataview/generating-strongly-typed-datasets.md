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
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="4b544-102">Generowanie silnie typizowanych elementów DataSet</span><span class="sxs-lookup"><span data-stu-id="4b544-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="4b544-103">W przypadku schematu XML, który jest zgodny ze standardem XML schematu definicji języka (XSD), można wygenerować silnie wpisaną <xref:System.Data.DataSet> przy użyciu narzędzia XSD. exe dostępnego w zestawie Windows Software Development Kit (SDK).</span><span class="sxs-lookup"><span data-stu-id="4b544-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the Windows Software Development Kit (SDK).</span></span>  
  
 <span data-ttu-id="4b544-104">(Aby utworzyć XSD z tabel baz danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Working with datasetss in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span><span class="sxs-lookup"><span data-stu-id="4b544-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="4b544-105">Poniższy kod przedstawia składnię generowania **zestawu danych** za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="4b544-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="4b544-106">W `/d` tej składni, dyrektywa informuje narzędzie do wygenerowania **zestawu danych**, a także `/l:` informuje narzędzie o języku, który ma być używany (na przykład C# lub Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="4b544-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="4b544-107">Opcjonalna `/eld` dyrektywa określa, że można użyć LINQ to DataSet do wykonywania zapytań względem wygenerowanego **zestawu danych.**</span><span class="sxs-lookup"><span data-stu-id="4b544-107">The optional `/eld` directive specifies that you can use LINQ to DataSet to query against the generated **DataSet.**</span></span> <span data-ttu-id="4b544-108">Ta opcja jest używana, `/d` Jeśli określono również opcję.</span><span class="sxs-lookup"><span data-stu-id="4b544-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="4b544-109">Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących wpisanych zestawów danych](../querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="4b544-109">For more information, see [Querying Typed DataSets](../querying-typed-datasets.md).</span></span> <span data-ttu-id="4b544-110">Opcjonalna `/n:` dyrektywa informuje narzędzie, aby wygenerowało również przestrzeń nazw dla **zestawu danych** o nazwie **XSDSchema. Namespace**.</span><span class="sxs-lookup"><span data-stu-id="4b544-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="4b544-111">Dane wyjściowe polecenia to XSDSchemaFileName.cs, które mogą być kompilowane i używane w aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="4b544-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="4b544-112">Wygenerowany kod można skompilować jako bibliotekę lub moduł.</span><span class="sxs-lookup"><span data-stu-id="4b544-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="4b544-113">Poniższy kod przedstawia składnię kompilowania wygenerowanego kodu jako biblioteki przy użyciu C# kompilatora (CSC. exe).</span><span class="sxs-lookup"><span data-stu-id="4b544-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="4b544-114">Dyrektywa informuje narzędzie do skompilowania do biblioteki, `/r:` a dyrektywy określają zależne biblioteki wymagane do skompilowania. `/t:`</span><span class="sxs-lookup"><span data-stu-id="4b544-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="4b544-115">Dane wyjściowe polecenia to XSDSchemaFileName. dll, które mogą być przekazywane do kompilatora podczas kompilowania aplikacji ADO.NET z `/r:` dyrektywą.</span><span class="sxs-lookup"><span data-stu-id="4b544-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="4b544-116">Poniższy kod przedstawia składnię dostępu do przestrzeni nazw przekazaną do pliku XSD. exe w aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="4b544-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="4b544-117">Poniższy przykład kodu używa określonego **zestawu danych** o nazwie **CustomerDataSet** , aby załadować listę klientów z bazy danych **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="4b544-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="4b544-118">Gdy dane zostaną załadowane przy użyciu metody **Fill** , przykład przeprowadzi pętlę przez każdego klienta w tabeli **Customers** przy użyciu określonego obiektu **CustomersRow** (**DataRow**).</span><span class="sxs-lookup"><span data-stu-id="4b544-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="4b544-119">Zapewnia to bezpośredni dostęp do kolumny **CustomerID** , w przeciwieństwie do za pośrednictwem elementu **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="4b544-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="4b544-120">Poniżej znajduje się schemat XML użyty dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="4b544-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4b544-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b544-121">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="4b544-122">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="4b544-122">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="4b544-123">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="4b544-123">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="4b544-124">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4b544-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
