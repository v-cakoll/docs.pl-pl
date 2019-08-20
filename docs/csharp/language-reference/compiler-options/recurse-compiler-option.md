---
title: -rekursywnie (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606739"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="64ebf-102">-rekursywnie (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="64ebf-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="64ebf-103">Opcja-rekursywnie umożliwia skompilowanie plików kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu (dir) lub katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="64ebf-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ebf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64ebf-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="64ebf-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="64ebf-105">Arguments</span></span>  
 <span data-ttu-id="64ebf-106">`dir`obowiązkowe</span><span class="sxs-lookup"><span data-stu-id="64ebf-106">`dir` (optional)</span></span>  
 <span data-ttu-id="64ebf-107">Katalog, w którym ma zostać rozpoczęte wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="64ebf-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="64ebf-108">Jeśli ta wartość nie jest określona, wyszukiwanie rozpoczyna się w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="64ebf-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="64ebf-109">Pliki do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="64ebf-109">The file(s) to search for.</span></span> <span data-ttu-id="64ebf-110">Symbole wieloznaczne są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="64ebf-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64ebf-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64ebf-111">Remarks</span></span>  
 <span data-ttu-id="64ebf-112">Opcja **-** rekursywnie umożliwia skompilowanie plików kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu (`dir`) lub katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="64ebf-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="64ebf-113">W nazwie pliku można użyć symboli wieloznacznych, aby skompilować wszystkie zgodne pliki w katalogu projektu bez użycia opcji **-** rekursywnie.</span><span class="sxs-lookup"><span data-stu-id="64ebf-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="64ebf-114">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="64ebf-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64ebf-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="64ebf-115">Example</span></span>  
 <span data-ttu-id="64ebf-116">Kompiluje wszystkie C# pliki w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="64ebf-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="64ebf-117">Kompiluje wszystkie pliki w C# katalogu dir1\dir2 i wszystkie znajdujące się w nim katalogi i generuje dir2. dll:</span><span class="sxs-lookup"><span data-stu-id="64ebf-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="64ebf-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64ebf-118">See also</span></span>

- [<span data-ttu-id="64ebf-119">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="64ebf-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="64ebf-120">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="64ebf-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
