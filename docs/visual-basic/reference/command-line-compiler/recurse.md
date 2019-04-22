---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2fe1834c3e92c3eff016ffd7857a0473eb2e8b3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816424"
---
# <a name="-recurse"></a><span data-ttu-id="37bd7-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="37bd7-102">-recurse</span></span>
<span data-ttu-id="37bd7-103">Kompiluje pliki kodu źródłowego we wszystkich katalogach podrzędnych w określonym katalogu lub katalog projektu.</span><span class="sxs-lookup"><span data-stu-id="37bd7-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37bd7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37bd7-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="37bd7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="37bd7-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="37bd7-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="37bd7-106">Optional.</span></span> <span data-ttu-id="37bd7-107">Katalog, w którym chcesz rozpocząć wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="37bd7-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="37bd7-108">Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="37bd7-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="37bd7-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="37bd7-109">Required.</span></span> <span data-ttu-id="37bd7-110">Pliki do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="37bd7-110">The file(s) to search for.</span></span> <span data-ttu-id="37bd7-111">Symbole wieloznaczne są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="37bd7-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37bd7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37bd7-112">Remarks</span></span>  
 <span data-ttu-id="37bd7-113">Można używać symboli wieloznacznych w nazwach plików do kompilacji wszystkie odpowiednie pliki w katalogu projektu bez użycia `-recurse`.</span><span class="sxs-lookup"><span data-stu-id="37bd7-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="37bd7-114">Jeśli nazwa pliku wyjściowego nie jest określony, kompilator Określa nazwę pliku wyjściowego na pierwszego pliku wejściowego przetworzone.</span><span class="sxs-lookup"><span data-stu-id="37bd7-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="37bd7-115">Zwykle jest to pierwszy plik listy plików skompilowany podczas wyświetlania w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="37bd7-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="37bd7-116">Z tego powodu najlepiej określić przy użyciu pliku wyjściowego jest `-out` opcji.</span><span class="sxs-lookup"><span data-stu-id="37bd7-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37bd7-117">`-recurse` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="37bd7-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37bd7-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="37bd7-118">Example</span></span>  
 <span data-ttu-id="37bd7-119">Poniższe polecenie kompiluje wszystkie pliki języka Visual Basic w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="37bd7-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="37bd7-120">Poniższe polecenie kompiluje wszystkie pliki języka Visual Basic w `Test\ABC` katalog i wszystkie jego katalogów, a następnie generuje `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="37bd7-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="37bd7-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37bd7-121">See also</span></span>

- [<span data-ttu-id="37bd7-122">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="37bd7-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="37bd7-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37bd7-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)
- [<span data-ttu-id="37bd7-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="37bd7-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
