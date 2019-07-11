---
title: 'Instrukcje: Generowanie modelu obiektu w języku Visual Basic lub C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 24b48b4962ac207f0c6a50456797ff588a97082d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743313"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="d37a7-102">Instrukcje: Generowanie modelu obiektu w języku Visual Basic lub C\#</span><span class="sxs-lookup"><span data-stu-id="d37a7-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="d37a7-103">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], model obiektów w języku programowania jest mapowany w relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="d37a7-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="d37a7-104">Dwa narzędzia są dostępne dla automatycznego generowania języka Visual Basic lub C# modelu z metadanych istniejącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d37a7-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="d37a7-105">Jeśli używasz programu Visual Studio umożliwia Object Relational Designer Generowanie modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="d37a7-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="d37a7-106">O/R Designer udostępnia interfejs użytkownika zaawansowanych, które ułatwiają pozyskanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="d37a7-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="d37a7-107">Aby uzyskać więcej informacji, zobacz [Linq to SQL Tools w programie Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="d37a7-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="d37a7-108">Narzędzie wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="d37a7-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="d37a7-109">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d37a7-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d37a7-110">Jeśli nie masz istniejącej bazy danych, aby utworzyć ją z modelu obiektów, można utworzyć modelu obiektu przy użyciu kodu edytora i <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="d37a7-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="d37a7-111">Aby uzyskać więcej informacji, zobacz [jak: Dynamiczne tworzenie bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="d37a7-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="d37a7-112">Dokumentacja O/R Designer zawiera przykłady sposobu generowania języka Visual Basic lub C# modelu obiektów za pomocą Projektanta obiektów relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="d37a7-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="d37a7-113">Poniższe informacje zawierają przykłady dotyczące używania narzędzia wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="d37a7-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="d37a7-114">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d37a7-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d37a7-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="d37a7-115">Example</span></span>  
 <span data-ttu-id="d37a7-116">Pokazano w poniższym przykładzie wiersza polecenia SQLMetal tworzy kod języka Visual Basic jako model opartych na atrybutach obiektu w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d37a7-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="d37a7-117">Procedur przechowywanych i funkcji również są renderowane.</span><span class="sxs-lookup"><span data-stu-id="d37a7-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="d37a7-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d37a7-118">Example</span></span>  
 <span data-ttu-id="d37a7-119">Pokazano w poniższym przykładzie wiersza polecenia SQLMetal generuje C# kod jako model opartych na atrybutach obiektu w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d37a7-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="d37a7-120">Procedur przechowywanych i funkcji również są renderowane, a nazwy tabel są automatycznie pluralized.</span><span class="sxs-lookup"><span data-stu-id="d37a7-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="d37a7-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d37a7-121">See also</span></span>

- [<span data-ttu-id="d37a7-122">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="d37a7-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [<span data-ttu-id="d37a7-123">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d37a7-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="d37a7-124">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="d37a7-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="d37a7-125">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="d37a7-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="d37a7-126">Mapowanie oparte na atrybutach</span><span class="sxs-lookup"><span data-stu-id="d37a7-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="d37a7-127">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="d37a7-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="d37a7-128">Mapowanie zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="d37a7-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [<span data-ttu-id="d37a7-129">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="d37a7-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="d37a7-130">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="d37a7-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
