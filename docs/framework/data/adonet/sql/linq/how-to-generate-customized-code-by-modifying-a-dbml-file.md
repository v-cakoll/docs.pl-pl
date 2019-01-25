---
title: 'Instrukcje: Generowanie kodu dostosowane przez zmodyfikowanie pliku DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: b17743f20cf9fcb01cdd39dc7afc3f6b4419ebff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499096"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="02c33-102">Instrukcje: Generowanie kodu dostosowane przez zmodyfikowanie pliku DBML</span><span class="sxs-lookup"><span data-stu-id="02c33-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="02c33-103">Można wygenerować kodu języka Visual Basic lub C# źródła kodu z pliku metadanych bazy danych markup language (dbml).</span><span class="sxs-lookup"><span data-stu-id="02c33-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="02c33-104">To podejście oferuje możliwość dostosowywania domyślnego pliku dbml przed wygenerowaniem kodu mapowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="02c33-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="02c33-105">Jest to zaawansowana funkcja.</span><span class="sxs-lookup"><span data-stu-id="02c33-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="02c33-106">Kroki w ramach tego procesu są następujące:</span><span class="sxs-lookup"><span data-stu-id="02c33-106">The steps in this process are as follows:</span></span>  
  
1.  <span data-ttu-id="02c33-107">Generuje plik dbml.</span><span class="sxs-lookup"><span data-stu-id="02c33-107">Generate a .dbml file.</span></span>  
  
2.  <span data-ttu-id="02c33-108">Użyj edytora do modyfikowania pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="02c33-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="02c33-109">Należy zauważyć, że plik dbml musi przeprowadzić walidacji względem pliku (XSD) definicji schematu dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dbml, pliki.</span><span class="sxs-lookup"><span data-stu-id="02c33-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="02c33-110">Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="02c33-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3.  <span data-ttu-id="02c33-111">Generowanie języka Visual Basic lub C# kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="02c33-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="02c33-112">W poniższych przykładach używane jest narzędzie wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="02c33-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="02c33-113">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="02c33-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02c33-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="02c33-114">Example</span></span>  
 <span data-ttu-id="02c33-115">Poniższy kod generuje plik dbml z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="02c33-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="02c33-116">Jako źródło dla metadanych bazy danych można użyć nazwy bazy danych lub nazwę pliku MDF.</span><span class="sxs-lookup"><span data-stu-id="02c33-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="02c33-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="02c33-117">Example</span></span>  
 <span data-ttu-id="02c33-118">Poniższy kod generuje języka Visual Basic lub C# pliku kodu źródłowego, na podstawie pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="02c33-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="02c33-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02c33-119">See also</span></span>
- [<span data-ttu-id="02c33-120">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="02c33-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="02c33-121">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="02c33-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="02c33-122">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="02c33-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
