---
title: 'Instrukcje: Wyświetlanie argumentów wiersza polecenia — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 948ff6e752b3f5cce870b483340cbbf9f4e78b01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607718"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="72296-102">Instrukcje: Wyświetlanie argumentów wiersza poleceń (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="72296-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="72296-103">Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pośrednictwem opcjonalny parametr do `Main`.</span><span class="sxs-lookup"><span data-stu-id="72296-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="72296-104">Argumenty są udostępniane w formie tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="72296-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="72296-105">Każdy element tablicy zawiera jeden argument.</span><span class="sxs-lookup"><span data-stu-id="72296-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="72296-106">Odstępy między argumentami zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="72296-106">White-space between arguments is removed.</span></span> <span data-ttu-id="72296-107">Na przykład należy wziąć pod uwagę te wywołania wiersza polecenia fikcyjne pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="72296-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="72296-108">Dane wejściowe w wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="72296-108">Input on Command-line</span></span>|<span data-ttu-id="72296-109">Tablica ciągów przekazywane dla metody Main</span><span class="sxs-lookup"><span data-stu-id="72296-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="72296-110">**executable.exe b c.**</span><span class="sxs-lookup"><span data-stu-id="72296-110">**executable.exe a b c**</span></span>|<span data-ttu-id="72296-111">""</span><span class="sxs-lookup"><span data-stu-id="72296-111">"a"</span></span><br /><br /> <span data-ttu-id="72296-112">"b"</span><span class="sxs-lookup"><span data-stu-id="72296-112">"b"</span></span><br /><br /> <span data-ttu-id="72296-113">"c"</span><span class="sxs-lookup"><span data-stu-id="72296-113">"c"</span></span>|  
|<span data-ttu-id="72296-114">**executable.exe jeden dwa**</span><span class="sxs-lookup"><span data-stu-id="72296-114">**executable.exe one two**</span></span>|<span data-ttu-id="72296-115">"jeden"</span><span class="sxs-lookup"><span data-stu-id="72296-115">"one"</span></span><br /><br /> <span data-ttu-id="72296-116">"dwóch"</span><span class="sxs-lookup"><span data-stu-id="72296-116">"two"</span></span>|  
|<span data-ttu-id="72296-117">**executable.exe "jeden dwa" trzy**</span><span class="sxs-lookup"><span data-stu-id="72296-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="72296-118">„one two”</span><span class="sxs-lookup"><span data-stu-id="72296-118">"one two"</span></span><br /><br /> <span data-ttu-id="72296-119">"trzy"</span><span class="sxs-lookup"><span data-stu-id="72296-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="72296-120">Po uruchomieniu aplikacji w programie Visual Studio, można określić argumenty wiersza poleceń w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="72296-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72296-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="72296-121">Example</span></span>  
 <span data-ttu-id="72296-122">Ten przykład wyświetla argumenty wiersza polecenia przekazywane do wiersza polecenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72296-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="72296-123">Jest wyświetlone dane wyjściowe do pierwszej pozycji w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="72296-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="72296-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72296-124">See also</span></span>

- [<span data-ttu-id="72296-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="72296-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="72296-126">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="72296-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="72296-127">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="72296-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="72296-128">Instrukcje: Dostęp do argumentów wiersza polecenia za pomocą foreach</span><span class="sxs-lookup"><span data-stu-id="72296-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
- [<span data-ttu-id="72296-129">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="72296-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
