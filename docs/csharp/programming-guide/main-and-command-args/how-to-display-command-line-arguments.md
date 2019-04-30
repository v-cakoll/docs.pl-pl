---
title: 'Instrukcje: Wyświetlanie argumentów wiersza polecenia — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: b7018afa1272f4ae092863de6b7f9ef783001244
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710930"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="e0f01-102">Instrukcje: Wyświetlanie argumentów wiersza poleceń (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e0f01-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="e0f01-103">Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pośrednictwem opcjonalny parametr do `Main`.</span><span class="sxs-lookup"><span data-stu-id="e0f01-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="e0f01-104">Argumenty są udostępniane w formie tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="e0f01-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="e0f01-105">Każdy element tablicy zawiera jeden argument.</span><span class="sxs-lookup"><span data-stu-id="e0f01-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="e0f01-106">Odstępy między argumentami zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="e0f01-106">White-space between arguments is removed.</span></span> <span data-ttu-id="e0f01-107">Na przykład należy wziąć pod uwagę te wywołania wiersza polecenia fikcyjne pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="e0f01-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="e0f01-108">Dane wejściowe w wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e0f01-108">Input on Command-line</span></span>|<span data-ttu-id="e0f01-109">Tablica ciągów przekazywane dla metody Main</span><span class="sxs-lookup"><span data-stu-id="e0f01-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="e0f01-110">**executable.exe b c.**</span><span class="sxs-lookup"><span data-stu-id="e0f01-110">**executable.exe a b c**</span></span>|<span data-ttu-id="e0f01-111">""</span><span class="sxs-lookup"><span data-stu-id="e0f01-111">"a"</span></span><br /><br /> <span data-ttu-id="e0f01-112">"b"</span><span class="sxs-lookup"><span data-stu-id="e0f01-112">"b"</span></span><br /><br /> <span data-ttu-id="e0f01-113">"c"</span><span class="sxs-lookup"><span data-stu-id="e0f01-113">"c"</span></span>|  
|<span data-ttu-id="e0f01-114">**executable.exe jeden dwa**</span><span class="sxs-lookup"><span data-stu-id="e0f01-114">**executable.exe one two**</span></span>|<span data-ttu-id="e0f01-115">"jeden"</span><span class="sxs-lookup"><span data-stu-id="e0f01-115">"one"</span></span><br /><br /> <span data-ttu-id="e0f01-116">"dwóch"</span><span class="sxs-lookup"><span data-stu-id="e0f01-116">"two"</span></span>|  
|<span data-ttu-id="e0f01-117">**executable.exe "jeden dwa" trzy**</span><span class="sxs-lookup"><span data-stu-id="e0f01-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="e0f01-118">„one two”</span><span class="sxs-lookup"><span data-stu-id="e0f01-118">"one two"</span></span><br /><br /> <span data-ttu-id="e0f01-119">"trzy"</span><span class="sxs-lookup"><span data-stu-id="e0f01-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e0f01-120">Po uruchomieniu aplikacji w programie Visual Studio, można określić argumenty wiersza poleceń w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="e0f01-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0f01-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0f01-121">Example</span></span>  
 <span data-ttu-id="e0f01-122">Ten przykład wyświetla argumenty wiersza polecenia przekazywane do wiersza polecenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e0f01-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="e0f01-123">Jest wyświetlone dane wyjściowe do pierwszej pozycji w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e0f01-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e0f01-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0f01-124">See also</span></span>

- [<span data-ttu-id="e0f01-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e0f01-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e0f01-126">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="e0f01-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="e0f01-127">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e0f01-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="e0f01-128">Instrukcje: Dostęp do argumentów wiersza polecenia za pomocą foreach</span><span class="sxs-lookup"><span data-stu-id="e0f01-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
- [<span data-ttu-id="e0f01-129">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="e0f01-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
