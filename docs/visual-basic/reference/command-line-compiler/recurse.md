---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 4281c7bf5a7972d323e1e649aaef437c7ee901ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956265"
---
# <a name="-recurse"></a><span data-ttu-id="61779-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="61779-102">-recurse</span></span>
<span data-ttu-id="61779-103">Kompiluje pliki kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu lub katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="61779-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61779-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61779-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="61779-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="61779-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="61779-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="61779-106">Optional.</span></span> <span data-ttu-id="61779-107">Katalog, w którym ma zostać rozpoczęte wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="61779-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="61779-108">Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="61779-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="61779-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="61779-109">Required.</span></span> <span data-ttu-id="61779-110">Pliki do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="61779-110">The file(s) to search for.</span></span> <span data-ttu-id="61779-111">Symbole wieloznaczne są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="61779-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61779-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61779-112">Remarks</span></span>  
 <span data-ttu-id="61779-113">W nazwie pliku można użyć symboli wieloznacznych, aby skompilować wszystkie zgodne pliki w katalogu projektu bez użycia `-recurse`.</span><span class="sxs-lookup"><span data-stu-id="61779-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="61779-114">Jeśli nazwa pliku wyjściowego nie zostanie określona, kompilator opiera się na nazwie pliku wyjściowego w pierwszym przetworzonym pliku wejściowym.</span><span class="sxs-lookup"><span data-stu-id="61779-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="61779-115">Zwykle jest to pierwszy plik na liście plików skompilowanych podczas wyświetlania alfabetycznie.</span><span class="sxs-lookup"><span data-stu-id="61779-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="61779-116">Z tego powodu najlepiej określić plik wyjściowy przy użyciu `-out` opcji.</span><span class="sxs-lookup"><span data-stu-id="61779-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61779-117">`-recurse` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61779-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61779-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="61779-118">Example</span></span>  
 <span data-ttu-id="61779-119">Poniższe polecenie kompiluje wszystkie pliki Visual Basic w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="61779-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="61779-120">Poniższe polecenie kompiluje wszystkie pliki Visual Basic w `Test\ABC` katalogu i wszystkie znajdujące się w nim katalogi, a następnie generuje. `Test.ABC.dll`</span><span class="sxs-lookup"><span data-stu-id="61779-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="61779-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61779-121">See also</span></span>

- [<span data-ttu-id="61779-122">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61779-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="61779-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61779-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)
- [<span data-ttu-id="61779-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="61779-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
