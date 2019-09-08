---
title: 'Instrukcje: Generowanie kodu dostosowane przez zmodyfikowanie pliku DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 01890e6b899db6b70049e2d6b8193e5b0f4095fb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781984"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="bbafc-102">Instrukcje: Generowanie kodu dostosowane przez zmodyfikowanie pliku DBML</span><span class="sxs-lookup"><span data-stu-id="bbafc-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="bbafc-103">Można generować Visual Basic lub C# kod źródłowy z pliku metadanych języka DBML (Database Markup Language).</span><span class="sxs-lookup"><span data-stu-id="bbafc-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="bbafc-104">Takie podejście umożliwia dostosowanie domyślnego pliku DBML przed wygenerowaniem kodu mapowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbafc-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="bbafc-105">Jest to funkcja zaawansowana.</span><span class="sxs-lookup"><span data-stu-id="bbafc-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="bbafc-106">Kroki w tym procesie są następujące:</span><span class="sxs-lookup"><span data-stu-id="bbafc-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="bbafc-107">Generuj plik. dbml.</span><span class="sxs-lookup"><span data-stu-id="bbafc-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="bbafc-108">Zmodyfikuj plik DBML za pomocą edytora.</span><span class="sxs-lookup"><span data-stu-id="bbafc-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="bbafc-109">Należy pamiętać, że plik. dbml musi sprawdzać poprawność pliku definicji schematu (XSD [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ) dla plików. dbml.</span><span class="sxs-lookup"><span data-stu-id="bbafc-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="bbafc-110">Aby uzyskać więcej informacji, zobacz [generowanie kodu w LINQ to SQL](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bbafc-110">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="bbafc-111">Generuj Visual Basic lub C# kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="bbafc-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="bbafc-112">W poniższych przykładach użyto narzędzia wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="bbafc-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="bbafc-113">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="bbafc-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbafc-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbafc-114">Example</span></span>  
 <span data-ttu-id="bbafc-115">Poniższy kod generuje plik. dbml z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="bbafc-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="bbafc-116">Jako źródło metadanych bazy danych można użyć nazwy bazy danych lub nazwy pliku MDF.</span><span class="sxs-lookup"><span data-stu-id="bbafc-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="bbafc-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbafc-117">Example</span></span>  
 <span data-ttu-id="bbafc-118">Poniższy kod generuje Visual Basic lub C# plik kodu źródłowego z pliku. dbml.</span><span class="sxs-lookup"><span data-stu-id="bbafc-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbafc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbafc-119">See also</span></span>

- [<span data-ttu-id="bbafc-120">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bbafc-120">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="bbafc-121">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="bbafc-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="bbafc-122">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="bbafc-122">Creating the Object Model</span></span>](creating-the-object-model.md)
