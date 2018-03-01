---
title: "Porady: wyświetlanie argumentów wiersza poleceń (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6ae495eef227c6e4d9fb9ca0d4d0c031163fd52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="c0215-102">Porady: wyświetlanie argumentów wiersza poleceń (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c0215-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="c0215-103">Argumenty przekazane do pliku wykonywalnego w wierszu polecenia są dostępne za pośrednictwem opcjonalny parametr do `Main`.</span><span class="sxs-lookup"><span data-stu-id="c0215-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="c0215-104">Argumenty są udostępniane w formie tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="c0215-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="c0215-105">Każdy element tablicy zawiera jeden argument.</span><span class="sxs-lookup"><span data-stu-id="c0215-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="c0215-106">Odstępu między argumentami zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="c0215-106">White-space between arguments is removed.</span></span> <span data-ttu-id="c0215-107">Rozważmy na przykład tych wywołań wiersza polecenia fikcyjne pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="c0215-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="c0215-108">Wprowadź w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="c0215-108">Input on Command-line</span></span>|<span data-ttu-id="c0215-109">Tablica ciągów przekazana dla metody Main</span><span class="sxs-lookup"><span data-stu-id="c0215-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="c0215-110">**executable.exe b c**</span><span class="sxs-lookup"><span data-stu-id="c0215-110">**executable.exe a b c**</span></span>|<span data-ttu-id="c0215-111">""</span><span class="sxs-lookup"><span data-stu-id="c0215-111">"a"</span></span><br /><br /> <span data-ttu-id="c0215-112">"b"</span><span class="sxs-lookup"><span data-stu-id="c0215-112">"b"</span></span><br /><br /> <span data-ttu-id="c0215-113">"c"</span><span class="sxs-lookup"><span data-stu-id="c0215-113">"c"</span></span>|  
|<span data-ttu-id="c0215-114">**executable.exe jeden dwa**</span><span class="sxs-lookup"><span data-stu-id="c0215-114">**executable.exe one two**</span></span>|<span data-ttu-id="c0215-115">"jeden"</span><span class="sxs-lookup"><span data-stu-id="c0215-115">"one"</span></span><br /><br /> <span data-ttu-id="c0215-116">"dwa"</span><span class="sxs-lookup"><span data-stu-id="c0215-116">"two"</span></span>|  
|<span data-ttu-id="c0215-117">**executable.exe "jeden dwa" trzy**</span><span class="sxs-lookup"><span data-stu-id="c0215-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="c0215-118">„one two”</span><span class="sxs-lookup"><span data-stu-id="c0215-118">"one two"</span></span><br /><br /> <span data-ttu-id="c0215-119">"3"</span><span class="sxs-lookup"><span data-stu-id="c0215-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c0215-120">Po uruchomieniu aplikacji w programie Visual Studio, można określić argumentów wiersza polecenia w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="c0215-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0215-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="c0215-121">Example</span></span>  
 <span data-ttu-id="c0215-122">W tym przykładzie wyświetlono argumenty wiersza polecenia przekazywane do wiersza polecenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0215-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="c0215-123">Dane wyjściowe pokazano to pierwszy wpisu w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c0215-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c0215-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0215-124">See Also</span></span>  
 [<span data-ttu-id="c0215-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c0215-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c0215-126">Za pomocą wiersza polecenia z csc.exe</span><span class="sxs-lookup"><span data-stu-id="c0215-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="c0215-127">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c0215-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="c0215-128">Porady: za pomocą argumentów wiersza polecenia dostępu instrukcji foreach</span><span class="sxs-lookup"><span data-stu-id="c0215-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [<span data-ttu-id="c0215-129">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="c0215-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
