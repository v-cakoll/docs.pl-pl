---
title: -recurse (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606739"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="61c93-102">-recurse (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="61c93-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="61c93-103">Opcja -recurse umożliwia kompilowanie plików kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu (dir) lub katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="61c93-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61c93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61c93-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="61c93-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="61c93-105">Arguments</span></span>  
 <span data-ttu-id="61c93-106">`dir` (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="61c93-106">`dir` (optional)</span></span>  
 <span data-ttu-id="61c93-107">Katalog, w którym ma się rozpocząć wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="61c93-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="61c93-108">Jeśli nie zostanie to określone, wyszukiwanie rozpoczyna się w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="61c93-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="61c93-109">Pliki do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="61c93-109">The file(s) to search for.</span></span> <span data-ttu-id="61c93-110">Znaki wieloznaczne są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="61c93-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61c93-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61c93-111">Remarks</span></span>  
 <span data-ttu-id="61c93-112">Opcja **-recurse** umożliwia kompilowanie plików kodu źródłowego we wszystkich katalogach`dir`podrzędnych określonego katalogu ( ) lub katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="61c93-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="61c93-113">Symboli wieloznacznych w nazwie pliku można skompilować wszystkie pasujące pliki w katalogu projektu bez użycia **-recurse**.</span><span class="sxs-lookup"><span data-stu-id="61c93-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="61c93-114">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="61c93-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61c93-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="61c93-115">Example</span></span>  
 <span data-ttu-id="61c93-116">Kompiluje wszystkie pliki C# w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="61c93-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="61c93-117">Kompiluje wszystkie pliki C# w katalogu dir1\dir2 i wszystkie katalogi poniżej i generuje dir2.dll:</span><span class="sxs-lookup"><span data-stu-id="61c93-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="61c93-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61c93-118">See also</span></span>

- [<span data-ttu-id="61c93-119">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="61c93-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="61c93-120">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="61c93-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
