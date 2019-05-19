---
title: 'Instrukcje: Wyświetlanie argumentów wiersza polecenia — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: c88219d03d40c814338a1b09ccd37cfc03c2d577
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881015"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="e98a2-102">Instrukcje: Wyświetlanie argumentów wiersza poleceń (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e98a2-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="e98a2-103">Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pośrednictwem opcjonalny parametr do `Main`.</span><span class="sxs-lookup"><span data-stu-id="e98a2-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="e98a2-104">Argumenty są udostępniane w formie tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="e98a2-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="e98a2-105">Każdy element tablicy zawiera jeden argument.</span><span class="sxs-lookup"><span data-stu-id="e98a2-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="e98a2-106">Odstępy między argumentami zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="e98a2-106">White-space between arguments is removed.</span></span> <span data-ttu-id="e98a2-107">Na przykład należy wziąć pod uwagę te wywołania wiersza polecenia fikcyjne pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="e98a2-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="e98a2-108">Dane wejściowe w wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e98a2-108">Input on Command-line</span></span>|<span data-ttu-id="e98a2-109">Tablica ciągów przekazywane dla metody Main</span><span class="sxs-lookup"><span data-stu-id="e98a2-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="e98a2-110">**executable.exe b c.**</span><span class="sxs-lookup"><span data-stu-id="e98a2-110">**executable.exe a b c**</span></span>|<span data-ttu-id="e98a2-111">""</span><span class="sxs-lookup"><span data-stu-id="e98a2-111">"a"</span></span><br /><br /> <span data-ttu-id="e98a2-112">"b"</span><span class="sxs-lookup"><span data-stu-id="e98a2-112">"b"</span></span><br /><br /> <span data-ttu-id="e98a2-113">"c"</span><span class="sxs-lookup"><span data-stu-id="e98a2-113">"c"</span></span>|  
|<span data-ttu-id="e98a2-114">**executable.exe jeden dwa**</span><span class="sxs-lookup"><span data-stu-id="e98a2-114">**executable.exe one two**</span></span>|<span data-ttu-id="e98a2-115">"jeden"</span><span class="sxs-lookup"><span data-stu-id="e98a2-115">"one"</span></span><br /><br /> <span data-ttu-id="e98a2-116">"dwóch"</span><span class="sxs-lookup"><span data-stu-id="e98a2-116">"two"</span></span>|  
|<span data-ttu-id="e98a2-117">**executable.exe "jeden dwa" trzy**</span><span class="sxs-lookup"><span data-stu-id="e98a2-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="e98a2-118">„one two”</span><span class="sxs-lookup"><span data-stu-id="e98a2-118">"one two"</span></span><br /><br /> <span data-ttu-id="e98a2-119">"trzy"</span><span class="sxs-lookup"><span data-stu-id="e98a2-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e98a2-120">Po uruchomieniu aplikacji w programie Visual Studio, można określić argumenty wiersza poleceń w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="e98a2-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e98a2-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="e98a2-121">Example</span></span>  
 <span data-ttu-id="e98a2-122">Ten przykład wyświetla argumenty wiersza polecenia przekazywane do wiersza polecenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e98a2-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="e98a2-123">Jest wyświetlone dane wyjściowe do pierwszej pozycji w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e98a2-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e98a2-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e98a2-124">See also</span></span>

- [<span data-ttu-id="e98a2-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e98a2-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e98a2-126">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="e98a2-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="e98a2-127">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e98a2-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="e98a2-128">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="e98a2-128">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
