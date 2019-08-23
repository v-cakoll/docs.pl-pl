---
title: 'Instrukcje: Wyświetlanie argumentów wiersza polecenia — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: ba732930d08c74433d6ea7b38e7dc3a9fddf594c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923864"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="e4bb8-102">Instrukcje: Wyświetlanie argumentów wiersza polecenia (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="e4bb8-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="e4bb8-103">Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pomocą opcjonalnego parametru do `Main`.</span><span class="sxs-lookup"><span data-stu-id="e4bb8-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="e4bb8-104">Argumenty są podane w postaci tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="e4bb8-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="e4bb8-105">Każdy element tablicy zawiera jeden argument.</span><span class="sxs-lookup"><span data-stu-id="e4bb8-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="e4bb8-106">Odstęp między argumentami jest usuwany.</span><span class="sxs-lookup"><span data-stu-id="e4bb8-106">White-space between arguments is removed.</span></span> <span data-ttu-id="e4bb8-107">Rozważmy na przykład następujące wywołania wiersza polecenia fikcyjnego pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="e4bb8-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="e4bb8-108">Dane wejściowe w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="e4bb8-108">Input on Command-line</span></span>|<span data-ttu-id="e4bb8-109">Tablica ciągów przeniesiona do głównej</span><span class="sxs-lookup"><span data-stu-id="e4bb8-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="e4bb8-110">**plik wykonywalny. exe a b c**</span><span class="sxs-lookup"><span data-stu-id="e4bb8-110">**executable.exe a b c**</span></span>|<span data-ttu-id="e4bb8-111">z</span><span class="sxs-lookup"><span data-stu-id="e4bb8-111">"a"</span></span><br /><br /> <span data-ttu-id="e4bb8-112">b</span><span class="sxs-lookup"><span data-stu-id="e4bb8-112">"b"</span></span><br /><br /> <span data-ttu-id="e4bb8-113">s</span><span class="sxs-lookup"><span data-stu-id="e4bb8-113">"c"</span></span>|  
|<span data-ttu-id="e4bb8-114">**plik wykonywaln. exe 1 2**</span><span class="sxs-lookup"><span data-stu-id="e4bb8-114">**executable.exe one two**</span></span>|<span data-ttu-id="e4bb8-115">je</span><span class="sxs-lookup"><span data-stu-id="e4bb8-115">"one"</span></span><br /><br /> <span data-ttu-id="e4bb8-116">tymi</span><span class="sxs-lookup"><span data-stu-id="e4bb8-116">"two"</span></span>|  
|<span data-ttu-id="e4bb8-117">**wykonywalny. exe "1 2" trzy**</span><span class="sxs-lookup"><span data-stu-id="e4bb8-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="e4bb8-118">„one two”</span><span class="sxs-lookup"><span data-stu-id="e4bb8-118">"one two"</span></span><br /><br /> <span data-ttu-id="e4bb8-119">trzecim</span><span class="sxs-lookup"><span data-stu-id="e4bb8-119">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e4bb8-120">W przypadku uruchamiania aplikacji w programie Visual Studio, można określić argumenty wiersza polecenia na [stronie debugowanie, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="e4bb8-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4bb8-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4bb8-121">Example</span></span>  
 <span data-ttu-id="e4bb8-122">Ten przykład wyświetla argumenty wiersza polecenia przekazane do aplikacji wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e4bb8-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="e4bb8-123">Wyświetlane dane wyjściowe dotyczą pierwszego wpisu w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e4bb8-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e4bb8-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4bb8-124">See also</span></span>

- [<span data-ttu-id="e4bb8-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e4bb8-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e4bb8-126">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="e4bb8-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="e4bb8-127">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e4bb8-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="e4bb8-128">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="e4bb8-128">Main() Return Values</span></span>](./main-return-values.md)
