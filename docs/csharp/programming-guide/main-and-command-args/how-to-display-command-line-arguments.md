---
title: 'Instrukcje: Wyświetlanie argumentów wiersza polecenia — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 030fd2bd3286bd4f25513e26b3de9e87eaee9029
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588897"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="0c754-102">Instrukcje: Wyświetlanie argumentów wiersza polecenia (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="0c754-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="0c754-103">Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pomocą opcjonalnego parametru do `Main`.</span><span class="sxs-lookup"><span data-stu-id="0c754-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="0c754-104">Argumenty są podane w postaci tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="0c754-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="0c754-105">Każdy element tablicy zawiera jeden argument.</span><span class="sxs-lookup"><span data-stu-id="0c754-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="0c754-106">Odstęp między argumentami jest usuwany.</span><span class="sxs-lookup"><span data-stu-id="0c754-106">White-space between arguments is removed.</span></span> <span data-ttu-id="0c754-107">Rozważmy na przykład następujące wywołania wiersza polecenia fikcyjnego pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="0c754-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="0c754-108">Dane wejściowe w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="0c754-108">Input on Command-line</span></span>|<span data-ttu-id="0c754-109">Tablica ciągów przeniesiona do głównej</span><span class="sxs-lookup"><span data-stu-id="0c754-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="0c754-110">**plik wykonywalny. exe a b c**</span><span class="sxs-lookup"><span data-stu-id="0c754-110">**executable.exe a b c**</span></span>|<span data-ttu-id="0c754-111">z</span><span class="sxs-lookup"><span data-stu-id="0c754-111">"a"</span></span><br /><br /> <span data-ttu-id="0c754-112">b</span><span class="sxs-lookup"><span data-stu-id="0c754-112">"b"</span></span><br /><br /> <span data-ttu-id="0c754-113">s</span><span class="sxs-lookup"><span data-stu-id="0c754-113">"c"</span></span>|  
|<span data-ttu-id="0c754-114">**plik wykonywaln. exe 1 2**</span><span class="sxs-lookup"><span data-stu-id="0c754-114">**executable.exe one two**</span></span>|<span data-ttu-id="0c754-115">je</span><span class="sxs-lookup"><span data-stu-id="0c754-115">"one"</span></span><br /><br /> <span data-ttu-id="0c754-116">tymi</span><span class="sxs-lookup"><span data-stu-id="0c754-116">"two"</span></span>|  
|<span data-ttu-id="0c754-117">**wykonywalny. exe "1 2" trzy**</span><span class="sxs-lookup"><span data-stu-id="0c754-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="0c754-118">„one two”</span><span class="sxs-lookup"><span data-stu-id="0c754-118">"one two"</span></span><br /><br /> <span data-ttu-id="0c754-119">trzecim</span><span class="sxs-lookup"><span data-stu-id="0c754-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0c754-120">W przypadku uruchamiania aplikacji w programie Visual Studio, można określić argumenty wiersza polecenia na [stronie debugowanie, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="0c754-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c754-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c754-121">Example</span></span>  
 <span data-ttu-id="0c754-122">Ten przykład wyświetla argumenty wiersza polecenia przekazane do aplikacji wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0c754-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="0c754-123">Wyświetlane dane wyjściowe dotyczą pierwszego wpisu w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0c754-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="0c754-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c754-124">See also</span></span>

- [<span data-ttu-id="0c754-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0c754-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0c754-126">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="0c754-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="0c754-127">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="0c754-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="0c754-128">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="0c754-128">Main() Return Values</span></span>](./main-return-values.md)
