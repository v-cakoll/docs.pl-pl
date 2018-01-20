---
title: -recurse (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b50454112bc7aee6c3e0f8fe674e8727ca9e49be
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="79cd2-102">-recurse (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="79cd2-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="79cd2-103">Recurse — opcja umożliwia skompilować plików kodu źródłowego we wszystkich katalogach podrzędnych albo określonego katalogu (dir) lub w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="79cd2-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79cd2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="79cd2-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="79cd2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="79cd2-105">Arguments</span></span>  
 <span data-ttu-id="79cd2-106">`dir`(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="79cd2-106">`dir` (optional)</span></span>  
 <span data-ttu-id="79cd2-107">Katalog, w którym ma rozpocząć wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="79cd2-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="79cd2-108">Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="79cd2-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="79cd2-109">Pliki do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="79cd2-109">The file(s) to search for.</span></span> <span data-ttu-id="79cd2-110">Symbole wieloznaczne są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="79cd2-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79cd2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79cd2-111">Remarks</span></span>  
 <span data-ttu-id="79cd2-112">**-Recurse** opcja umożliwia skompilować plików kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu (`dir`) lub w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="79cd2-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="79cd2-113">Symbole wieloznaczne w nazwie pliku służy do Kompiluj wszystkie zgodne pliki w katalogu projektu bez użycia **-recurse**.</span><span class="sxs-lookup"><span data-stu-id="79cd2-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="79cd2-114">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="79cd2-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79cd2-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="79cd2-115">Example</span></span>  
 <span data-ttu-id="79cd2-116">Kompiluje wszystkie pliki C# w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="79cd2-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="79cd2-117">Kompiluje wszystkie pliki C# w katalogu dir1\dir2 i wszystkie jego katalogów i generuje dir2.dll:</span><span class="sxs-lookup"><span data-stu-id="79cd2-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="79cd2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79cd2-118">See Also</span></span>  
 [<span data-ttu-id="79cd2-119">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="79cd2-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="79cd2-120">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="79cd2-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
