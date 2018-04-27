---
title: 'Porady: Generowanie modelu obiektów w Visual Basic lub C#'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 77d7020a985abb8ed56af4fdd9f50a98bfc478c4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="0cec9-102">Porady: Generowanie modelu obiektów w Visual Basic lub C#</span><span class="sxs-lookup"><span data-stu-id="0cec9-102">How to: Generate the Object Model in Visual Basic or C#</span></span> #
<span data-ttu-id="0cec9-103">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], model obiektowy w języku programowania jest mapowany na relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0cec9-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="0cec9-104">Dwa narzędzia są dostępne do automatycznego generowania modelu kodu języka Visual Basic lub C# z istniejącej bazy danych metadanych.</span><span class="sxs-lookup"><span data-stu-id="0cec9-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
-   <span data-ttu-id="0cec9-105">Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do wygenerowania modelu typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="0cec9-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to generate an object model.</span></span> <span data-ttu-id="0cec9-106">[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Oferuje interfejs użytkownika zaawansowanych, aby wygenerować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektu modelu.</span><span class="sxs-lookup"><span data-stu-id="0cec9-106">The [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="0cec9-107">Aby uzyskać więcej informacji, zobacz [składnika Linq to SQL narzędzia w programie Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="0cec9-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
-   <span data-ttu-id="0cec9-108">SQLMetal narzędzie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0cec9-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="0cec9-109">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="0cec9-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0cec9-110">Jeśli nie masz istniejącej bazy danych, aby utworzyć model obiektowy, można utworzyć modelu obiektu przy użyciu kodu edytora i <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cec9-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="0cec9-111">Aby uzyskać więcej informacji, zobacz [porady: dynamiczne tworzenie bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="0cec9-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="0cec9-112">Dokumentacja [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] przykłady sposobu generowania modelu obiektu języka Visual Basic lub C# przy użyciu [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0cec9-112">Documentation for the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides examples of how to generate a Visual Basic or C# object model by using the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span></span> <span data-ttu-id="0cec9-113">Poniższe informacje zawierają przykłady sposobów użycia narzędzia wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="0cec9-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="0cec9-114">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="0cec9-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cec9-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0cec9-115">Example</span></span>  
 <span data-ttu-id="0cec9-116">Wiersz polecenia SQLMetal pokazano w poniższym przykładzie tworzy kod Visual Basic jako model obiektu na podstawie atrybutów przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0cec9-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="0cec9-117">Procedury składowane i funkcje także są renderowane.</span><span class="sxs-lookup"><span data-stu-id="0cec9-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="0cec9-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="0cec9-118">Example</span></span>  
 <span data-ttu-id="0cec9-119">Wiersz polecenia SQLMetal pokazano w poniższym przykładzie generuje kod w języku C# jako model obiektu na podstawie atrybutów przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0cec9-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="0cec9-120">Procedury składowane i funkcje są również wyświetlane, a nazwy tabeli są automatycznie pluralized.</span><span class="sxs-lookup"><span data-stu-id="0cec9-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cec9-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cec9-121">See Also</span></span>  
 [<span data-ttu-id="0cec9-122">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="0cec9-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [<span data-ttu-id="0cec9-123">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0cec9-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="0cec9-124">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="0cec9-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="0cec9-125">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="0cec9-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [<span data-ttu-id="0cec9-126">Mapowanie oparte na atrybutach</span><span class="sxs-lookup"><span data-stu-id="0cec9-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="0cec9-127">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="0cec9-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="0cec9-128">Mapowanie zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="0cec9-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="0cec9-129">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="0cec9-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="0cec9-130">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="0cec9-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
