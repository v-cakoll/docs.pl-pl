---
title: 'Instrukcje: Generowanie kodu dostosowane przez zmodyfikowanie pliku DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: c3fa4d9db4076309ab7d6066cc7072797eaead54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877347"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="41ebd-102">Instrukcje: Generowanie kodu dostosowane przez zmodyfikowanie pliku DBML</span><span class="sxs-lookup"><span data-stu-id="41ebd-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="41ebd-103">Można wygenerować kodu języka Visual Basic lub C# źródła kodu z pliku metadanych bazy danych markup language (dbml).</span><span class="sxs-lookup"><span data-stu-id="41ebd-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="41ebd-104">To podejście oferuje możliwość dostosowywania domyślnego pliku dbml przed wygenerowaniem kodu mapowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41ebd-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="41ebd-105">Jest to zaawansowana funkcja.</span><span class="sxs-lookup"><span data-stu-id="41ebd-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="41ebd-106">Kroki w ramach tego procesu są następujące:</span><span class="sxs-lookup"><span data-stu-id="41ebd-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="41ebd-107">Generuje plik dbml.</span><span class="sxs-lookup"><span data-stu-id="41ebd-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="41ebd-108">Użyj edytora do modyfikowania pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="41ebd-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="41ebd-109">Należy zauważyć, że plik dbml musi przeprowadzić walidacji względem pliku (XSD) definicji schematu dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dbml, pliki.</span><span class="sxs-lookup"><span data-stu-id="41ebd-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="41ebd-110">Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="41ebd-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="41ebd-111">Generowanie języka Visual Basic lub C# kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="41ebd-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="41ebd-112">W poniższych przykładach używane jest narzędzie wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="41ebd-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="41ebd-113">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="41ebd-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="41ebd-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="41ebd-114">Example</span></span>  
 <span data-ttu-id="41ebd-115">Poniższy kod generuje plik dbml z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="41ebd-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="41ebd-116">Jako źródło dla metadanych bazy danych można użyć nazwy bazy danych lub nazwę pliku MDF.</span><span class="sxs-lookup"><span data-stu-id="41ebd-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="41ebd-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="41ebd-117">Example</span></span>  
 <span data-ttu-id="41ebd-118">Poniższy kod generuje języka Visual Basic lub C# pliku kodu źródłowego, na podstawie pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="41ebd-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="41ebd-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41ebd-119">See also</span></span>

- [<span data-ttu-id="41ebd-120">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="41ebd-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="41ebd-121">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="41ebd-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="41ebd-122">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="41ebd-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
