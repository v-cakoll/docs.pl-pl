---
title: '#odwołanie do C# wiersza'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: b4ac4fd3277fb53251e87321500d1b8007458037
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608534"
---
# <a name="line-c-reference"></a><span data-ttu-id="5d9de-102">#line (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5d9de-102">#line (C# Reference)</span></span>

<span data-ttu-id="5d9de-103">`#line`umożliwia zmodyfikowanie numeracji linii kompilatora oraz (opcjonalnie) dane wyjściowe nazwy pliku dla błędów i ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="5d9de-103">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="5d9de-104">Poniższy przykład pokazuje, jak zgłosić dwa ostrzeżenia skojarzone z numerami wierszy.</span><span class="sxs-lookup"><span data-stu-id="5d9de-104">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="5d9de-105">Dyrektywa wymusza numer następnego wiersza do 200 (mimo że wartość domyślna to #6), a do następnej `#line` dyrektywy nazwa pliku będzie raportowana jako "Specjalna". `#line 200`</span><span class="sxs-lookup"><span data-stu-id="5d9de-105">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="5d9de-106">`#line default` Dyrektywa zwraca numery wierszy do domyślnej numeracji, która zlicza wiersze, które zostały zmienione przez poprzednią dyrektywę.</span><span class="sxs-lookup"><span data-stu-id="5d9de-106">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

<span data-ttu-id="5d9de-107">Kompilacja generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="5d9de-107">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="5d9de-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d9de-108">Remarks</span></span>

<span data-ttu-id="5d9de-109">Dyrektywa `#line` może być używana w automatycznym, pośrednim etapie procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5d9de-109">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="5d9de-110">Na przykład jeśli z oryginalnego pliku kodu źródłowego zostały usunięte wiersze, ale kompilator nadal ma generować dane wyjściowe na podstawie oryginalnego numerowania wierszy w pliku, możesz usunąć wiersze i zasymulować oryginalne numerowanie za pomocą dyrektywy `#line`.</span><span class="sxs-lookup"><span data-stu-id="5d9de-110">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="5d9de-111">Dyrektywa `#line hidden` ukrywa kolejne wiersze przed debugerem, w taki sposób, że podczas wykonywania kodu przez dewelopera wszystkie wiersze między dyrektywą `#line hidden` a następną dyrektywą `#line` (przy założeniu, że nie będzie to kolejna dyrektywa `#line hidden`) zostaną pominięte.</span><span class="sxs-lookup"><span data-stu-id="5d9de-111">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="5d9de-112">Ta opcja pozwala także platformie ASP.NET odróżnić kod zdefiniowany przez użytkownika od kodu wygenerowanego maszynowo.</span><span class="sxs-lookup"><span data-stu-id="5d9de-112">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="5d9de-113">Mimo że funkcja ta jest używana głównie w ASP.NET, to prawdopodobne jest, że będzie z niej korzystać więcej generatorów kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5d9de-113">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="5d9de-114">Dyrektywa `#line hidden` nie wpływa na nazwy plików ani numery wierszy w raportowaniu błędów.</span><span class="sxs-lookup"><span data-stu-id="5d9de-114">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="5d9de-115">Oznacza to, że w przypadku napotkania błędu w ukrytym bloku kompilator zgłosi obecną nazwę pliku oraz numer wiersza, w którym wystąpił błąd.</span><span class="sxs-lookup"><span data-stu-id="5d9de-115">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="5d9de-116">Dyrektywa `#line filename` określa nazwę pliku, która ma być wyświetlana w danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5d9de-116">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="5d9de-117">Domyślnie używana jest rzeczywista nazwa pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5d9de-117">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="5d9de-118">Nazwa pliku musi być ujęta w podwójny cudzysłów ("") oraz musi być poprzedzona numerem wiersza.</span><span class="sxs-lookup"><span data-stu-id="5d9de-118">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="5d9de-119">Plik kodu źródłowego może mieć dowolną liczbę wystąpeń dyrektywy `#line`.</span><span class="sxs-lookup"><span data-stu-id="5d9de-119">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="5d9de-120">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="5d9de-120">Example 1</span></span>

<span data-ttu-id="5d9de-121">W poniższym przykładzie pokazano, jak debuger ignoruje ukryte wiersze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5d9de-121">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="5d9de-122">Po uruchomieniu przykładu zostaną wyświetlone trzy wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="5d9de-122">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="5d9de-123">Jednak gdy ustawisz punkt przerwania (jak pokazano w przykładzie) i naciśniesz klawisz F10, aby wykonywać kod krokowo, zobaczysz, że debuger zignoruje ukryty wiersz.</span><span class="sxs-lookup"><span data-stu-id="5d9de-123">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="5d9de-124">Nawet jeśli ustawisz punkt przerwania w ukrytym wierszu, debuger go zignoruje.</span><span class="sxs-lookup"><span data-stu-id="5d9de-124">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5d9de-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d9de-125">See also</span></span>

- [<span data-ttu-id="5d9de-126">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5d9de-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5d9de-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5d9de-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5d9de-128">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="5d9de-128">C# Preprocessor Directives</span></span>](./index.md)
