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
# <a name="line-c-reference"></a><span data-ttu-id="ef941-102">#line (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ef941-102">#line (C# Reference)</span></span>
<span data-ttu-id="ef941-103">`#line`Umożliwia modyfikowanie kompilatora numer wiersza i (opcjonalnie) Nazwa plik wyjściowy błędów i ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="ef941-103">`#line` lets you modify the compiler's line number and (optionally) the file name output for errors and warnings.</span></span> <span data-ttu-id="ef941-104">W tym przykładzie przedstawiono sposób raportu dwóch ostrzeżenia skojarzony z numerów wierszy.</span><span class="sxs-lookup"><span data-stu-id="ef941-104">This example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="ef941-105">`#line 200` Dyrektywy wymusza numer wiersza jako 200 (mimo że wartość domyślna to #7), a do czasu następnego dyrektywy #line, nazwa pliku będą raportowane jako "Special".</span><span class="sxs-lookup"><span data-stu-id="ef941-105">The `#line 200` directive forces the line number to be 200 (although the default is #7) and until the next #line directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="ef941-106">#Line — dyrektywa domyślne zwraca numerowanie do jego numerowanie domyślne wierszy, które zlicza wiersze, które zostały oznaczenie w poprzedniej dyrektywie.</span><span class="sxs-lookup"><span data-stu-id="ef941-106">The #line default directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="ef941-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef941-107">Remarks</span></span>  
 <span data-ttu-id="ef941-108">`#line` Dyrektywy mogą być używane w automatycznych, pośredniego kroku w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ef941-108">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="ef941-109">Na przykład, jeśli wiersze zostały usunięte z oryginalnego pliku kodu źródłowego, ale nadal potrzebujesz kompilatorowi Generowanie danych wyjściowych na podstawie wiersza oryginalnej numerowanie w pliku, możesz można usunąć wiersze i następnie symulować oryginalnego numerowania wierszy z `#line`.</span><span class="sxs-lookup"><span data-stu-id="ef941-109">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>  
  
 <span data-ttu-id="ef941-110">`#line hidden` Dyrektywy ukrywa z kolejnych wierszy debugera, w taki sposób, że deweloper przechodzi przez kod, po dowolnej linii między `#line hidden` Następna `#line` — dyrektywa (przy założeniu, że nie jest on inny `#line hidden` dyrektywy) oparta na.</span><span class="sxs-lookup"><span data-stu-id="ef941-110">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="ef941-111">Tej opcji można również umożliwić ASP.NET w celu rozróżnienia kod użytkownika i wygenerowane maszynowo.</span><span class="sxs-lookup"><span data-stu-id="ef941-111">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="ef941-112">Mimo że program ASP.NET konsumenta podstawowej tej funkcji, najprawdopodobniej z niego korzystać więcej źródło, które wprowadzi generatory.</span><span class="sxs-lookup"><span data-stu-id="ef941-112">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>  
  
 <span data-ttu-id="ef941-113">A `#line hidden` dyrektywy nie wpływa na nazwy plików lub numerów linii w raportowaniu błędów.</span><span class="sxs-lookup"><span data-stu-id="ef941-113">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="ef941-114">Oznacza to w przypadku napotkania błędu w bloku ukryte, kompilator będzie zgłaszać bieżącego pliku nazwa i wiersz numer błędu.</span><span class="sxs-lookup"><span data-stu-id="ef941-114">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>  
  
 <span data-ttu-id="ef941-115">`#line filename` Dyrektywa określa nazwę pliku, która ma być wyświetlana w danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ef941-115">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="ef941-116">Domyślnie używany jest rzeczywistą nazwą pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="ef941-116">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="ef941-117">Nazwa pliku musi być w podwójny cudzysłów ("") i musi być poprzedzona numer wiersza.</span><span class="sxs-lookup"><span data-stu-id="ef941-117">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>  
  
 <span data-ttu-id="ef941-118">Pliku kodu źródłowego może mieć dowolną liczbę `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="ef941-118">A source code file can have any number of `#line` directives.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="ef941-119">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="ef941-119">Example 1</span></span>  
 <span data-ttu-id="ef941-120">W poniższym przykładzie pokazano, jak debuger ignoruje ukryte wiersze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ef941-120">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="ef941-121">Po uruchomieniu przykładzie wyświetli trzy wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="ef941-121">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="ef941-122">Jednak gdy ustawić punkt przerwania, jak pokazano w przykładzie i trafień F10, aby wykonywać krokowo kodu, można zauważyć, że debuger ignoruje ukryte wiersza.</span><span class="sxs-lookup"><span data-stu-id="ef941-122">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="ef941-123">Należy zauważyć, że nawet w przypadku ustawienia punktu przerwania w wierszu ukryte, debuger nadal zignoruje.</span><span class="sxs-lookup"><span data-stu-id="ef941-123">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef941-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef941-124">See Also</span></span>  
 [<span data-ttu-id="ef941-125">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="ef941-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ef941-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ef941-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ef941-127">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="ef941-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
