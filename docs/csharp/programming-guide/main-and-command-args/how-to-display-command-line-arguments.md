---
title: 'Porady: wyświetlanie argumentów wiersza poleceń (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 7b9e488e84c78c8fdbf64431f42ea5797fdca916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334139"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="694e6-102">Porady: wyświetlanie argumentów wiersza poleceń (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="694e6-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="694e6-103">Argumenty przekazane do pliku wykonywalnego w wierszu polecenia są dostępne za pośrednictwem opcjonalny parametr do `Main`.</span><span class="sxs-lookup"><span data-stu-id="694e6-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="694e6-104">Argumenty są udostępniane w formie tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="694e6-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="694e6-105">Każdy element tablicy zawiera jeden argument.</span><span class="sxs-lookup"><span data-stu-id="694e6-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="694e6-106">Odstępu między argumentami zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="694e6-106">White-space between arguments is removed.</span></span> <span data-ttu-id="694e6-107">Rozważmy na przykład tych wywołań wiersza polecenia fikcyjne pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="694e6-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="694e6-108">Wprowadź w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="694e6-108">Input on Command-line</span></span>|<span data-ttu-id="694e6-109">Tablica ciągów przekazana dla metody Main</span><span class="sxs-lookup"><span data-stu-id="694e6-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="694e6-110">**executable.exe b c**</span><span class="sxs-lookup"><span data-stu-id="694e6-110">**executable.exe a b c**</span></span>|<span data-ttu-id="694e6-111">""</span><span class="sxs-lookup"><span data-stu-id="694e6-111">"a"</span></span><br /><br /> <span data-ttu-id="694e6-112">"b"</span><span class="sxs-lookup"><span data-stu-id="694e6-112">"b"</span></span><br /><br /> <span data-ttu-id="694e6-113">"c"</span><span class="sxs-lookup"><span data-stu-id="694e6-113">"c"</span></span>|  
|<span data-ttu-id="694e6-114">**executable.exe jeden dwa**</span><span class="sxs-lookup"><span data-stu-id="694e6-114">**executable.exe one two**</span></span>|<span data-ttu-id="694e6-115">"jeden"</span><span class="sxs-lookup"><span data-stu-id="694e6-115">"one"</span></span><br /><br /> <span data-ttu-id="694e6-116">"dwa"</span><span class="sxs-lookup"><span data-stu-id="694e6-116">"two"</span></span>|  
|<span data-ttu-id="694e6-117">**executable.exe "jeden dwa" trzy**</span><span class="sxs-lookup"><span data-stu-id="694e6-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="694e6-118">„one two”</span><span class="sxs-lookup"><span data-stu-id="694e6-118">"one two"</span></span><br /><br /> <span data-ttu-id="694e6-119">"3"</span><span class="sxs-lookup"><span data-stu-id="694e6-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="694e6-120">Po uruchomieniu aplikacji w programie Visual Studio, można określić argumentów wiersza polecenia w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="694e6-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="694e6-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="694e6-121">Example</span></span>  
 <span data-ttu-id="694e6-122">W tym przykładzie wyświetlono argumenty wiersza polecenia przekazywane do wiersza polecenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="694e6-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="694e6-123">Dane wyjściowe pokazano to pierwszy wpisu w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="694e6-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="694e6-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="694e6-124">See Also</span></span>  
 [<span data-ttu-id="694e6-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="694e6-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="694e6-126">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="694e6-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="694e6-127">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="694e6-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="694e6-128">Instrukcje: uzyskiwanie dostępu do argumentów wiersza polecenia za pomocą instrukcji foreach</span><span class="sxs-lookup"><span data-stu-id="694e6-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [<span data-ttu-id="694e6-129">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="694e6-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
