---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: 3877757185030b0dba914a79d8c760fb8033ae5f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408650"
---
# <a name="-filealign"></a><span data-ttu-id="79677-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="79677-102">-filealign</span></span>
<span data-ttu-id="79677-103">Określa, gdzie mają być wyrównane sekcje pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="79677-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79677-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="79677-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="79677-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="79677-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="79677-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="79677-106">Required.</span></span> <span data-ttu-id="79677-107">Wartość określająca wyrównanie sekcji w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="79677-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="79677-108">Prawidłowe wartości to 512, 1024, 2048, 4096 i 8192.</span><span class="sxs-lookup"><span data-stu-id="79677-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="79677-109">Te wartości są w bajtach.</span><span class="sxs-lookup"><span data-stu-id="79677-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79677-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79677-110">Remarks</span></span>  
 <span data-ttu-id="79677-111">Możesz użyć opcji, `-filealign` Aby określić wyrównanie sekcji w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="79677-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="79677-112">Sekcje to bloki ciągłej pamięci w przenośnym pliku wykonywalnym (PE), który zawiera kod lub dane.</span><span class="sxs-lookup"><span data-stu-id="79677-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="79677-113">`-filealign`Opcja umożliwia skompilowanie aplikacji z niestandardowym wyrównaniem; większość deweloperów nie musi używać tej opcji.</span><span class="sxs-lookup"><span data-stu-id="79677-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="79677-114">Każda sekcja jest wyrównana na granicy, która jest wielokrotnością `-filealign` wartości.</span><span class="sxs-lookup"><span data-stu-id="79677-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="79677-115">Nie ma żadnych stałych ustawień domyślnych.</span><span class="sxs-lookup"><span data-stu-id="79677-115">There is no fixed default.</span></span> <span data-ttu-id="79677-116">Jeśli `-filealign` nie jest określony, kompilator wybiera wartość domyślną w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="79677-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="79677-117">Określając rozmiar sekcji, można zmienić rozmiar pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="79677-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="79677-118">Modyfikowanie rozmiaru sekcji może być przydatne w przypadku programów, które będą uruchamiane na mniejszych urządzeniach.</span><span class="sxs-lookup"><span data-stu-id="79677-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79677-119">`-filealign`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="79677-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79677-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79677-120">See also</span></span>

- [<span data-ttu-id="79677-121">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="79677-121">Visual Basic Command-Line Compiler</span></span>](index.md)
