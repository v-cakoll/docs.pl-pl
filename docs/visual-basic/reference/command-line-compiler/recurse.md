---
title: /recurse
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb69c7c44dcc2e8da5eb8a76f7d22f936a6d948f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="recurse"></a><span data-ttu-id="5a8d2-102">/recurse</span><span class="sxs-lookup"><span data-stu-id="5a8d2-102">/recurse</span></span>
<span data-ttu-id="5a8d2-103">Kompiluje pliki kodu źródłowego we wszystkich katalogach podrzędnych katalogu określonego lub katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a8d2-104">Syntax</span></span>  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="5a8d2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5a8d2-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="5a8d2-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-106">Optional.</span></span> <span data-ttu-id="5a8d2-107">Katalog, w którym ma rozpocząć wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="5a8d2-108">Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="5a8d2-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-109">Required.</span></span> <span data-ttu-id="5a8d2-110">Pliki do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-110">The file(s) to search for.</span></span> <span data-ttu-id="5a8d2-111">Symbole wieloznaczne są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a8d2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a8d2-112">Remarks</span></span>  
 <span data-ttu-id="5a8d2-113">Symbole wieloznaczne w nazwie pliku służy do Kompiluj wszystkie zgodne pliki w katalogu projektu bez użycia `/recurse`.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-113">You can use wildcards in a file name to compile all matching files in the project directory without using `/recurse`.</span></span> <span data-ttu-id="5a8d2-114">Jeśli nazwa pliku wyjściowego, nie zostanie określona, kompilator Określa nazwę pliku wyjściowego na pierwszy plik wejściowy przetworzone.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="5a8d2-115">Zwykle jest to pierwszy plik listy plików skompilowanych widzianego alfabetycznie.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="5a8d2-116">Z tego powodu najlepiej określić plik danych wyjściowych za pomocą `/out` opcji.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-116">For this reason, it is best to specify an output file using the `/out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a8d2-117">`/recurse` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-117">The `/recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a8d2-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a8d2-118">Example</span></span>  
 <span data-ttu-id="5a8d2-119">Poniższy kod kompiluje wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] plików w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-119">The following code compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory.</span></span>  
  
```  
vbc *.vb  
```  
  
 <span data-ttu-id="5a8d2-120">Poniższy kod kompiluje wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] plików `Test\ABC` katalogu i wszystkie jego katalogów, a następnie generuje `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="5a8d2-120">The following code compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a8d2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a8d2-121">See Also</span></span>  
 [<span data-ttu-id="5a8d2-122">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a8d2-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5a8d2-123">/ out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a8d2-123">/out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="5a8d2-124">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="5a8d2-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
