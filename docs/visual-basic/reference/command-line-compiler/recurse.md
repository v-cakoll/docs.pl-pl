---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: fc8dfe41ea56531ff34cd5e551ef24d636227e47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400503"
---
# <a name="-recurse"></a><span data-ttu-id="59b4f-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="59b4f-102">-recurse</span></span>
<span data-ttu-id="59b4f-103">Kompiluje pliki kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu lub katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="59b4f-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59b4f-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="59b4f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="59b4f-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="59b4f-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="59b4f-106">Optional.</span></span> <span data-ttu-id="59b4f-107">Katalog, w którym ma zostać rozpoczęte wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="59b4f-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="59b4f-108">Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="59b4f-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="59b4f-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="59b4f-109">Required.</span></span> <span data-ttu-id="59b4f-110">Pliki do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="59b4f-110">The file(s) to search for.</span></span> <span data-ttu-id="59b4f-111">Symbole wieloznaczne są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="59b4f-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59b4f-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59b4f-112">Remarks</span></span>  
 <span data-ttu-id="59b4f-113">W nazwie pliku można użyć symboli wieloznacznych, aby skompilować wszystkie zgodne pliki w katalogu projektu bez użycia `-recurse` .</span><span class="sxs-lookup"><span data-stu-id="59b4f-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="59b4f-114">Jeśli nazwa pliku wyjściowego nie zostanie określona, kompilator opiera się na nazwie pliku wyjściowego w pierwszym przetworzonym pliku wejściowym.</span><span class="sxs-lookup"><span data-stu-id="59b4f-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="59b4f-115">Zwykle jest to pierwszy plik na liście plików skompilowanych podczas wyświetlania alfabetycznie.</span><span class="sxs-lookup"><span data-stu-id="59b4f-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="59b4f-116">Z tego powodu najlepiej określić plik wyjściowy przy użyciu `-out` opcji.</span><span class="sxs-lookup"><span data-stu-id="59b4f-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59b4f-117">`-recurse`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="59b4f-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59b4f-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="59b4f-118">Example</span></span>  
 <span data-ttu-id="59b4f-119">Poniższe polecenie kompiluje wszystkie pliki Visual Basic w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="59b4f-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="59b4f-120">Poniższe polecenie kompiluje wszystkie pliki Visual Basic w `Test\ABC` katalogu i wszystkie znajdujące się w nim katalogi, a następnie generuje `Test.ABC.dll` .</span><span class="sxs-lookup"><span data-stu-id="59b4f-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="59b4f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59b4f-121">See also</span></span>

- [<span data-ttu-id="59b4f-122">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59b4f-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="59b4f-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59b4f-123">-out (Visual Basic)</span></span>](out.md)
- [<span data-ttu-id="59b4f-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="59b4f-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
