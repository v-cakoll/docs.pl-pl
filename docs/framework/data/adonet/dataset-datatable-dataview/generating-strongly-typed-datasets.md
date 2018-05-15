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
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="36ced-102">Generowanie silnie Typizowane zbiory danych</span><span class="sxs-lookup"><span data-stu-id="36ced-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="36ced-103">Podany schemat XML, który jest zgodny ze schematu XML definicji języka (XSD) standard, można wygenerować silnie typizowaną <xref:System.Data.DataSet> przy użyciu dostarczonego z narzędzia XSD.exe [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="36ced-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="36ced-104">(Aby utworzyć xsd z tabel bazy danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Praca z zestawami danych w programie Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span><span class="sxs-lookup"><span data-stu-id="36ced-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
 <span data-ttu-id="36ced-105">Poniższy kod przedstawia składnię generowania **zestawu danych** za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="36ced-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="36ced-106">W tej składni `/d` dyrektywy informuje narzędzie do generowania **DataSet**i `/l:` informuje narzędzie język do użycia (na przykład C# i Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="36ced-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="36ced-107">Opcjonalny `/eld` dyrektywa określa, czy możesz używać [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] do zapytania dotyczącego wygenerowany **zestawu danych.**</span><span class="sxs-lookup"><span data-stu-id="36ced-107">The optional `/eld` directive specifies that you can use [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] to query against the generated **DataSet.**</span></span> <span data-ttu-id="36ced-108">Ta opcja jest używana podczas `/d` jest także określona opcja.</span><span class="sxs-lookup"><span data-stu-id="36ced-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="36ced-109">Aby uzyskać więcej informacji, zobacz [zapytań wpisanych zestawów danych](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="36ced-109">For more information, see [Querying Typed DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="36ced-110">Opcjonalny `/n:` dyrektywy informuje narzędzie do generowania również przestrzeń nazw dla **DataSet** o nazwie **XSDSchema.Namespace**.</span><span class="sxs-lookup"><span data-stu-id="36ced-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="36ced-111">Dane wyjściowe polecenia jest XSDSchemaFileName.cs, który może być skompilowany i używane w aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="36ced-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="36ced-112">Wygenerowany kod, mogą być kompilowane jako modułu lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="36ced-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="36ced-113">Poniższy kod przedstawia składnię kompilowania wygenerowanego kodu jako bibliotekę przy użyciu kompilatora C# (csc.exe).</span><span class="sxs-lookup"><span data-stu-id="36ced-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="36ced-114">`/t:` Dyrektywy informuje narzędzie do kompilowania w bibliotece i `/r:` dyrektywy Określ zależnej biblioteki wymagane do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="36ced-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="36ced-115">Dane wyjściowe polecenia jest XSDSchemaFileName.dll, które mogą zostać przekazane do kompilatora podczas kompilowania aplikacji ADO.NET z `/r:` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="36ced-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="36ced-116">Poniższy kod przedstawia składnię do uzyskiwania dostępu do aplikacji ADO.NET przekazano XSD.exe przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="36ced-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="36ced-117">Poniższy przykład kodu wykorzystuje maszynowy **DataSet** o nazwie **CustomerDataSet** można załadować listy klientów z **Northwind** bazy danych.</span><span class="sxs-lookup"><span data-stu-id="36ced-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="36ced-118">Po załadowaniu danych przy użyciu **wypełnienia** metody przykładzie pętli każdego klienta w **klientów** tabeli, używając wpisanego **CustomersRow** ( **Element DataRow**) obiektu.</span><span class="sxs-lookup"><span data-stu-id="36ced-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="36ced-119">To zapewnia bezpośredni dostęp do **CustomerID** kolumny, w przeciwieństwie do za pomocą **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="36ced-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="36ced-120">Poniżej znajduje się schematu XML używanego w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="36ced-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36ced-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36ced-121">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="36ced-122">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="36ced-122">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="36ced-123">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="36ced-123">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="36ced-124">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="36ced-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
