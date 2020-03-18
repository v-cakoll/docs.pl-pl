---
title: Jak wyświetlić argumenty wiersza polecenia - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712029"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="eb3b8-102">Jak wyświetlić argumenty wiersza polecenia (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="eb3b8-102">How to display command line arguments (C# Programming Guide)</span></span>
<span data-ttu-id="eb3b8-103">Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pośrednictwem opcjonalnego parametru . `Main`</span><span class="sxs-lookup"><span data-stu-id="eb3b8-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="eb3b8-104">Argumenty są dostarczane w postaci tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="eb3b8-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="eb3b8-105">Każdy element tablicy zawiera jeden argument.</span><span class="sxs-lookup"><span data-stu-id="eb3b8-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="eb3b8-106">Odstęp między argumentami jest usuwany.</span><span class="sxs-lookup"><span data-stu-id="eb3b8-106">White-space between arguments is removed.</span></span> <span data-ttu-id="eb3b8-107">Rozważmy na przykład te wywołania wiersza polecenia fikcyjnego pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="eb3b8-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="eb3b8-108">Wejście w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="eb3b8-108">Input on Command-line</span></span>|<span data-ttu-id="eb3b8-109">Tablica ciągów przekazywanych do Main</span><span class="sxs-lookup"><span data-stu-id="eb3b8-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="eb3b8-110">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="eb3b8-110">**executable.exe a b c**</span></span>|<span data-ttu-id="eb3b8-111">"a"</span><span class="sxs-lookup"><span data-stu-id="eb3b8-111">"a"</span></span><br /><br /> <span data-ttu-id="eb3b8-112">"b"</span><span class="sxs-lookup"><span data-stu-id="eb3b8-112">"b"</span></span><br /><br /> <span data-ttu-id="eb3b8-113">"c"</span><span class="sxs-lookup"><span data-stu-id="eb3b8-113">"c"</span></span>|  
|<span data-ttu-id="eb3b8-114">**executable.exe jeden dwa**</span><span class="sxs-lookup"><span data-stu-id="eb3b8-114">**executable.exe one two**</span></span>|<span data-ttu-id="eb3b8-115">"jeden"</span><span class="sxs-lookup"><span data-stu-id="eb3b8-115">"one"</span></span><br /><br /> <span data-ttu-id="eb3b8-116">"dwa"</span><span class="sxs-lookup"><span data-stu-id="eb3b8-116">"two"</span></span>|  
|<span data-ttu-id="eb3b8-117">**executable.exe "jeden dwa" trzy**</span><span class="sxs-lookup"><span data-stu-id="eb3b8-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="eb3b8-118">„one two”</span><span class="sxs-lookup"><span data-stu-id="eb3b8-118">"one two"</span></span><br /><br /> <span data-ttu-id="eb3b8-119">"trzy"</span><span class="sxs-lookup"><span data-stu-id="eb3b8-119">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="eb3b8-120">Podczas uruchamiania aplikacji w programie Visual Studio można określić argumenty wiersza polecenia na [stronie debugowania, projektancie projektów](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="eb3b8-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb3b8-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb3b8-121">Example</span></span>  
 <span data-ttu-id="eb3b8-122">W tym przykładzie wyświetlane są argumenty wiersza polecenia przekazane do aplikacji wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="eb3b8-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="eb3b8-123">Dane wyjściowe są dla pierwszego wpisu w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="eb3b8-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="eb3b8-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb3b8-124">See also</span></span>

- [<span data-ttu-id="eb3b8-125">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="eb3b8-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="eb3b8-126">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="eb3b8-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="eb3b8-127">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="eb3b8-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="eb3b8-128">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="eb3b8-128">Main() Return Values</span></span>](./main-return-values.md)
