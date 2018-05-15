---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd5dde46cdea67825b14a6f5fa96a82c8bab8d3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-recurse"></a><span data-ttu-id="26dce-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="26dce-102">-recurse</span></span>
<span data-ttu-id="26dce-103">Kompiluje pliki kodu źródłowego we wszystkich katalogach podrzędnych katalogu określonego lub katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="26dce-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26dce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26dce-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="26dce-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="26dce-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="26dce-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="26dce-106">Optional.</span></span> <span data-ttu-id="26dce-107">Katalog, w którym ma rozpocząć wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="26dce-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="26dce-108">Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="26dce-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="26dce-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="26dce-109">Required.</span></span> <span data-ttu-id="26dce-110">Pliki do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="26dce-110">The file(s) to search for.</span></span> <span data-ttu-id="26dce-111">Symbole wieloznaczne są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="26dce-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26dce-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26dce-112">Remarks</span></span>  
 <span data-ttu-id="26dce-113">Symbole wieloznaczne w nazwie pliku służy do Kompiluj wszystkie zgodne pliki w katalogu projektu bez użycia `-recurse`.</span><span class="sxs-lookup"><span data-stu-id="26dce-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="26dce-114">Jeśli nazwa pliku wyjściowego, nie zostanie określona, kompilator Określa nazwę pliku wyjściowego na pierwszy plik wejściowy przetworzone.</span><span class="sxs-lookup"><span data-stu-id="26dce-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="26dce-115">Zwykle jest to pierwszy plik listy plików skompilowanych widzianego alfabetycznie.</span><span class="sxs-lookup"><span data-stu-id="26dce-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="26dce-116">Z tego powodu najlepiej określić plik danych wyjściowych za pomocą `-out` opcji.</span><span class="sxs-lookup"><span data-stu-id="26dce-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26dce-117">`-recurse` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="26dce-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26dce-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="26dce-118">Example</span></span>  
 <span data-ttu-id="26dce-119">Poniższe polecenie kompiluje wszystkie pliki Visual Basic w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="26dce-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="26dce-120">Poniższe polecenie kompiluje wszystkie pliki Visual Basic w `Test\ABC` katalogu i wszystkie jego katalogów, a następnie generuje `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="26dce-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="26dce-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26dce-121">See Also</span></span>  
 [<span data-ttu-id="26dce-122">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26dce-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="26dce-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26dce-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="26dce-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="26dce-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
