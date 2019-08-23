---
title: 'Instrukcje: Generowanie modelu obiektu w języku Visual Basic lub C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 5f2c2f99a5efeb3463ecf5bf401a6cf654845bb2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911969"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="cfbd1-102">Instrukcje: Generuj model obiektów w Visual Basic lub C\#</span><span class="sxs-lookup"><span data-stu-id="cfbd1-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="cfbd1-103">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie model obiektów w własnym języku programowania jest mapowany na relacyjną bazę danych.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="cfbd1-104">Dostępne są dwa narzędzia do automatycznego generowania Visual Basic lub C# modelu z metadanych istniejącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="cfbd1-105">W przypadku korzystania z programu Visual Studio można wygenerować model obiektów przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="cfbd1-106">Projektant o/R udostępnia rozbudowany interfejs użytkownika ułatwiający generowanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="cfbd1-107">Aby uzyskać więcej informacji, zobacz [Narzędzia LINQ to SQL w programie Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="cfbd1-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="cfbd1-108">Narzędzie wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="cfbd1-109">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="cfbd1-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cfbd1-110">Jeśli nie masz istniejącej bazy danych i chcesz utworzyć ją na podstawie modelu obiektów, możesz utworzyć model obiektu za pomocą edytora kodu i <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="cfbd1-111">Aby uzyskać więcej informacji, zobacz [jak: Dynamiczne tworzenie bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="cfbd1-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="cfbd1-112">Dokumentacja projektanta O/R zawiera przykłady sposobu generowania Visual Basic lub C# modelu obiektów przy użyciu projektanta o/r.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="cfbd1-113">Poniższe informacje zawierają przykłady użycia narzędzia wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="cfbd1-114">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="cfbd1-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfbd1-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfbd1-115">Example</span></span>  
 <span data-ttu-id="cfbd1-116">Wiersz polecenia SQLMetal przedstawiony w poniższym przykładzie generuje kod Visual Basic jako model obiektów opartych na atrybutach przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="cfbd1-117">Procedury składowane i funkcje są również renderowane.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="cfbd1-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfbd1-118">Example</span></span>  
 <span data-ttu-id="cfbd1-119">Wiersz polecenia SQLMetal przedstawiony w poniższym przykładzie generuje C# kod jako model obiektu oparty na atrybutach przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="cfbd1-120">Procedury składowane i funkcje są również renderowane, a nazwy tabel są automatycznie umieszczane w liczbie.</span><span class="sxs-lookup"><span data-stu-id="cfbd1-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfbd1-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfbd1-121">See also</span></span>

- [<span data-ttu-id="cfbd1-122">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="cfbd1-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [<span data-ttu-id="cfbd1-123">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cfbd1-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="cfbd1-124">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="cfbd1-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="cfbd1-125">Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu</span><span class="sxs-lookup"><span data-stu-id="cfbd1-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="cfbd1-126">Mapowanie oparte na atrybutach</span><span class="sxs-lookup"><span data-stu-id="cfbd1-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="cfbd1-127">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="cfbd1-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="cfbd1-128">Mapowanie zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="cfbd1-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [<span data-ttu-id="cfbd1-129">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="cfbd1-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="cfbd1-130">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="cfbd1-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
