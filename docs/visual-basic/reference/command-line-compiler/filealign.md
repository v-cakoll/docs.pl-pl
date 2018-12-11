---
title: -filealign —
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: db70749f28592ae6711b6d9544f8704af9416490
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128170"
---
# <a name="-filealign"></a><span data-ttu-id="29715-102">-filealign —</span><span class="sxs-lookup"><span data-stu-id="29715-102">-filealign</span></span>
<span data-ttu-id="29715-103">Określa, gdzie należy wyrównać sekcje pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="29715-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29715-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29715-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="29715-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="29715-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="29715-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="29715-106">Required.</span></span> <span data-ttu-id="29715-107">Wartość, która określa wyrównanie sekcji w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="29715-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="29715-108">Prawidłowe wartości to 512, 1024, 2048, 4096 i 8192.</span><span class="sxs-lookup"><span data-stu-id="29715-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="29715-109">Te wartości są w bajtach.</span><span class="sxs-lookup"><span data-stu-id="29715-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29715-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29715-110">Remarks</span></span>  
 <span data-ttu-id="29715-111">Możesz użyć `-filealign` opcję, aby określić wyrównanie sekcji w pliku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="29715-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="29715-112">Sekcje są bloków pamięci ciągłej w pliku przenośny plik wykonywalny (PE), który zawiera kod lub danych.</span><span class="sxs-lookup"><span data-stu-id="29715-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="29715-113">`-filealign` Opcja umożliwia kompilowanie aplikacji za pomocą niestandardowych wyrównanie; Większość programistów nie potrzebuje do użycia tej opcji.</span><span class="sxs-lookup"><span data-stu-id="29715-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="29715-114">Każda sekcja jest wyrównany na granicy, która jest wielokrotnością liczby `-filealign` wartość.</span><span class="sxs-lookup"><span data-stu-id="29715-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="29715-115">Nie jest stałą domyślnie.</span><span class="sxs-lookup"><span data-stu-id="29715-115">There is no fixed default.</span></span> <span data-ttu-id="29715-116">Jeśli `-filealign` nie zostanie określony, kompilator wybiera domyślny w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="29715-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="29715-117">Określając rozmiar sekcji, możesz zmienić rozmiar pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="29715-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="29715-118">Modyfikowanie sekcji rozmiaru może być przydatne w przypadku programów, które będą uruchamiane w mniejszych urządzeniach.</span><span class="sxs-lookup"><span data-stu-id="29715-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29715-119">`-filealign` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="29715-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29715-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29715-120">See Also</span></span>  
 [<span data-ttu-id="29715-121">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29715-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
