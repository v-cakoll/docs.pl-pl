---
title: 'Porady: generowanie kodu dostosowane przez zmodyfikowanie pliku DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 806d0ebc0e9ce970e144d80dbbd4910f9d271e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="4438c-102">Porady: generowanie kodu dostosowane przez zmodyfikowanie pliku DBML</span><span class="sxs-lookup"><span data-stu-id="4438c-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="4438c-103">Można wygenerować kodu źródłowego języka Visual Basic lub C# z pliku metadanych bazy danych markup language (.dbml).</span><span class="sxs-lookup"><span data-stu-id="4438c-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="4438c-104">Takie podejście umożliwia dostosować domyślny plik .dbml, aby wygenerować kod mapowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4438c-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="4438c-105">Jest to zaawansowana funkcja.</span><span class="sxs-lookup"><span data-stu-id="4438c-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="4438c-106">Kroki tego procesu są następujące:</span><span class="sxs-lookup"><span data-stu-id="4438c-106">The steps in this process are as follows:</span></span>  
  
1.  <span data-ttu-id="4438c-107">Wygeneruj plik .dbml.</span><span class="sxs-lookup"><span data-stu-id="4438c-107">Generate a .dbml file.</span></span>  
  
2.  <span data-ttu-id="4438c-108">Edytor do zmodyfikowania pliku: .dbml.</span><span class="sxs-lookup"><span data-stu-id="4438c-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="4438c-109">Należy pamiętać, że plik .dbml musi sprawdzania poprawności schematu pliku definicji (XSD) dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml plików.</span><span class="sxs-lookup"><span data-stu-id="4438c-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="4438c-110">Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4438c-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3.  <span data-ttu-id="4438c-111">Generowanie kodu źródłowego języka Visual Basic lub C#.</span><span class="sxs-lookup"><span data-stu-id="4438c-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="4438c-112">Poniższe przykłady użyć narzędzia wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="4438c-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="4438c-113">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="4438c-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4438c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="4438c-114">Example</span></span>  
 <span data-ttu-id="4438c-115">Poniższy kod generuje plik .dbml z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="4438c-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="4438c-116">Jako źródło dla metadanych bazy danych można użyć nazwy bazy danych lub nazwa pliku MDF.</span><span class="sxs-lookup"><span data-stu-id="4438c-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="4438c-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="4438c-117">Example</span></span>  
 <span data-ttu-id="4438c-118">Poniższy kod generuje Visual Basic lub C# pliku kodu źródłowego z pliku .dbml.</span><span class="sxs-lookup"><span data-stu-id="4438c-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="4438c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4438c-119">See Also</span></span>  
 [<span data-ttu-id="4438c-120">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4438c-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="4438c-121">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="4438c-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="4438c-122">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="4438c-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
