---
title: 'Instrukcje: Wyświetlanie argumentów wiersza polecenia — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 9b09f5a1991ab5545ab31b1879f30c383a0e9a9f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236534"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="1fbc1-102">Instrukcje: Wyświetlanie argumentów wiersza poleceń (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="1fbc1-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="1fbc1-103">Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pośrednictwem opcjonalny parametr do `Main`.</span><span class="sxs-lookup"><span data-stu-id="1fbc1-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="1fbc1-104">Argumenty są udostępniane w formie tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="1fbc1-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="1fbc1-105">Każdy element tablicy zawiera jeden argument.</span><span class="sxs-lookup"><span data-stu-id="1fbc1-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="1fbc1-106">Odstępy między argumentami zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="1fbc1-106">White-space between arguments is removed.</span></span> <span data-ttu-id="1fbc1-107">Na przykład należy wziąć pod uwagę te wywołania wiersza polecenia fikcyjne pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="1fbc1-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="1fbc1-108">Dane wejściowe w wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="1fbc1-108">Input on Command-line</span></span>|<span data-ttu-id="1fbc1-109">Tablica ciągów przekazywane dla metody Main</span><span class="sxs-lookup"><span data-stu-id="1fbc1-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="1fbc1-110">**executable.exe b c.**</span><span class="sxs-lookup"><span data-stu-id="1fbc1-110">**executable.exe a b c**</span></span>|<span data-ttu-id="1fbc1-111">""</span><span class="sxs-lookup"><span data-stu-id="1fbc1-111">"a"</span></span><br /><br /> <span data-ttu-id="1fbc1-112">"b"</span><span class="sxs-lookup"><span data-stu-id="1fbc1-112">"b"</span></span><br /><br /> <span data-ttu-id="1fbc1-113">"c"</span><span class="sxs-lookup"><span data-stu-id="1fbc1-113">"c"</span></span>|  
|<span data-ttu-id="1fbc1-114">**executable.exe jeden dwa**</span><span class="sxs-lookup"><span data-stu-id="1fbc1-114">**executable.exe one two**</span></span>|<span data-ttu-id="1fbc1-115">"jeden"</span><span class="sxs-lookup"><span data-stu-id="1fbc1-115">"one"</span></span><br /><br /> <span data-ttu-id="1fbc1-116">"dwóch"</span><span class="sxs-lookup"><span data-stu-id="1fbc1-116">"two"</span></span>|  
|<span data-ttu-id="1fbc1-117">**executable.exe "jeden dwa" trzy**</span><span class="sxs-lookup"><span data-stu-id="1fbc1-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="1fbc1-118">„one two”</span><span class="sxs-lookup"><span data-stu-id="1fbc1-118">"one two"</span></span><br /><br /> <span data-ttu-id="1fbc1-119">"trzy"</span><span class="sxs-lookup"><span data-stu-id="1fbc1-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="1fbc1-120">Po uruchomieniu aplikacji w programie Visual Studio, można określić argumenty wiersza poleceń w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="1fbc1-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fbc1-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="1fbc1-121">Example</span></span>  
 <span data-ttu-id="1fbc1-122">Ten przykład wyświetla argumenty wiersza polecenia przekazywane do wiersza polecenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1fbc1-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="1fbc1-123">Jest wyświetlone dane wyjściowe do pierwszej pozycji w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1fbc1-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1fbc1-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1fbc1-124">See Also</span></span>

- [<span data-ttu-id="1fbc1-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1fbc1-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1fbc1-126">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="1fbc1-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [<span data-ttu-id="1fbc1-127">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="1fbc1-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [<span data-ttu-id="1fbc1-128">Instrukcje: Dostęp do argumentów wiersza polecenia za pomocą foreach</span><span class="sxs-lookup"><span data-stu-id="1fbc1-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
- [<span data-ttu-id="1fbc1-129">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="1fbc1-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
