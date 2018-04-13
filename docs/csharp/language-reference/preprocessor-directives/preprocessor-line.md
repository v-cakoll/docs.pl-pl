---
title: '#wiersz (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d2f42915d214349eebff40949482d7f603c0c2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="line-c-reference"></a><span data-ttu-id="a2310-102">#line (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a2310-102">#line (C# Reference)</span></span>
<span data-ttu-id="a2310-103">Dyrektywa `#line` umożliwia modyfikowanie numerów wierszy kompilatora i (opcjonalnie) danych wyjściowych nazw plików pod kątem błędów i ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="a2310-103">`#line` lets you modify the compiler's line number and (optionally) the file name output for errors and warnings.</span></span> <span data-ttu-id="a2310-104">W tym przykładzie przedstawiono sposób zgłaszania dwóch ostrzeżeń skojarzonych z numerami wierszy.</span><span class="sxs-lookup"><span data-stu-id="a2310-104">This example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="a2310-105">Dyrektywa `#line 200` wymusza numer wiersza o wartości 200 (mimo że wartość domyślna to #7), przez co do momentu aktywowania następnej dyrektywy #line zgłaszaną nazwą pliku będzie „Special”.</span><span class="sxs-lookup"><span data-stu-id="a2310-105">The `#line 200` directive forces the line number to be 200 (although the default is #7) and until the next #line directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="a2310-106">Dyrektywa #line domyślnie zwraca numerowanie wierszy w wersji domyślnej, czyli zlicza wiersze, które zostały ponumerowane przez poprzednią dyrektywę.</span><span class="sxs-lookup"><span data-stu-id="a2310-106">The #line default directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="a2310-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2310-107">Remarks</span></span>  
 <span data-ttu-id="a2310-108">Dyrektywa `#line` może być używana w automatycznym, pośrednim etapie procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a2310-108">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="a2310-109">Na przykład jeśli z oryginalnego pliku kodu źródłowego zostały usunięte wiersze, ale kompilator nadal ma generować dane wyjściowe na podstawie oryginalnego numerowania wierszy w pliku, możesz usunąć wiersze i zasymulować oryginalne numerowanie za pomocą dyrektywy `#line`.</span><span class="sxs-lookup"><span data-stu-id="a2310-109">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>  
  
 <span data-ttu-id="a2310-110">Dyrektywa `#line hidden` ukrywa kolejne wiersze przed debugerem, w taki sposób, że podczas wykonywania kodu przez dewelopera wszystkie wiersze między dyrektywą `#line hidden` a następną dyrektywą `#line` (przy założeniu, że nie będzie to kolejna dyrektywa `#line hidden`) zostaną pominięte.</span><span class="sxs-lookup"><span data-stu-id="a2310-110">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="a2310-111">Ta opcja pozwala także platformie ASP.NET odróżnić kod zdefiniowany przez użytkownika od kodu wygenerowanego maszynowo.</span><span class="sxs-lookup"><span data-stu-id="a2310-111">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="a2310-112">Mimo że funkcja ta jest używana głównie w ASP.NET, to prawdopodobne jest, że będzie z niej korzystać więcej generatorów kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a2310-112">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>  
  
 <span data-ttu-id="a2310-113">Dyrektywa `#line hidden` nie wpływa na nazwy plików ani numery wierszy w raportowaniu błędów.</span><span class="sxs-lookup"><span data-stu-id="a2310-113">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="a2310-114">Oznacza to, że w przypadku napotkania błędu w ukrytym bloku kompilator zgłosi obecną nazwę pliku oraz numer wiersza, w którym wystąpił błąd.</span><span class="sxs-lookup"><span data-stu-id="a2310-114">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>  
  
 <span data-ttu-id="a2310-115">Dyrektywa `#line filename` określa nazwę pliku, która ma być wyświetlana w danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a2310-115">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="a2310-116">Domyślnie używana jest rzeczywista nazwa pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a2310-116">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="a2310-117">Nazwa pliku musi być ujęta w podwójny cudzysłów ("") oraz musi być poprzedzona numerem wiersza.</span><span class="sxs-lookup"><span data-stu-id="a2310-117">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>  
  
 <span data-ttu-id="a2310-118">Plik kodu źródłowego może mieć dowolną liczbę wystąpeń dyrektywy `#line`.</span><span class="sxs-lookup"><span data-stu-id="a2310-118">A source code file can have any number of `#line` directives.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="a2310-119">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="a2310-119">Example 1</span></span>  
 <span data-ttu-id="a2310-120">W poniższym przykładzie pokazano, jak debuger ignoruje ukryte wiersze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a2310-120">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="a2310-121">Po uruchomieniu przykładu zostaną wyświetlone trzy wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="a2310-121">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="a2310-122">Jednak gdy ustawisz punkt przerwania (jak pokazano w przykładzie) i naciśniesz klawisz F10, aby wykonywać kod krokowo, zobaczysz, że debuger zignoruje ukryty wiersz.</span><span class="sxs-lookup"><span data-stu-id="a2310-122">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="a2310-123">Nawet jeśli ustawisz punkt przerwania w ukrytym wierszu, debuger go zignoruje.</span><span class="sxs-lookup"><span data-stu-id="a2310-123">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>  
  
```csharp
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2310-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2310-124">See Also</span></span>  
 [<span data-ttu-id="a2310-125">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a2310-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a2310-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a2310-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a2310-127">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="a2310-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
