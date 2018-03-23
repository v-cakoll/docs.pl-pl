---
title: -filealign
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26ff29f00f00d3ea5dbbd0bbf01df4d7858771d0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-filealign"></a><span data-ttu-id="7c1c8-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="7c1c8-102">-filealign</span></span>
<span data-ttu-id="7c1c8-103">Określa lokalizację były wyrównane w sekcjach pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c1c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c1c8-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="7c1c8-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7c1c8-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="7c1c8-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-106">Required.</span></span> <span data-ttu-id="7c1c8-107">Wartość, która określa sposób wyrównania sekcji w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="7c1c8-108">Prawidłowe wartości to 512, 1024, 2048, 4096 do 8192.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="7c1c8-109">Te wartości są w bajtach.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c1c8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c1c8-110">Remarks</span></span>  
 <span data-ttu-id="7c1c8-111">Można użyć `-filealign` opcję, aby określić wyrównanie sekcji w pliku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="7c1c8-112">Sekcje są bloków pamięci ciągłej w pliku przenośnym plikiem wykonawczym (PE), który zawiera kod lub dane.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="7c1c8-113">`-filealign` Opcja umożliwia kompilowanie aplikacji przy użyciu niestandardowych wyrównanie; większość deweloperów nie trzeba używać tej opcji.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="7c1c8-114">Każda sekcja jest wyrównany na granicy, która jest wielokrotnością liczby `-filealign` wartość.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="7c1c8-115">Nie jest domyślnie stałym.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-115">There is no fixed default.</span></span> <span data-ttu-id="7c1c8-116">Jeśli `-filealign` nie zostanie określony, kompilator wybiera domyślny, w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="7c1c8-117">Określając rozmiar sekcji, można zmienić rozmiar pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="7c1c8-118">Modyfikowanie rozmiar sekcji mogą być przydatne dla programów uruchamianych na mniejsze urządzenia.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c1c8-119">`-filealign` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="7c1c8-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c1c8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c1c8-120">See Also</span></span>  
 [<span data-ttu-id="7c1c8-121">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c1c8-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
