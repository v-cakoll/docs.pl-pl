---
title: '#wiersz - Odwołanie do języka C#'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 79033fa652af62c76d54737fbf0a0b47cf3aae99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712497"
---
# <a name="line-c-reference"></a><span data-ttu-id="ab159-102">#line (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ab159-102">#line (C# Reference)</span></span>

<span data-ttu-id="ab159-103">`#line`umożliwia modyfikowanie numeracji wiersza kompilatora i (opcjonalnie) danych wyjściowych nazwy pliku dla błędów i ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="ab159-103">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="ab159-104">W poniższym przykładzie pokazano, jak zgłosić dwa ostrzeżenia skojarzone z numerami linii.</span><span class="sxs-lookup"><span data-stu-id="ab159-104">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="ab159-105">Dyrektywa `#line 200` wymusza numer następnego wiersza na 200 (chociaż wartość domyślna `#line` jest #6), a do następnej dyrektywy nazwa pliku będzie zgłaszana jako "Specjalna".</span><span class="sxs-lookup"><span data-stu-id="ab159-105">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="ab159-106">Dyrektywa `#line default` zwraca numeracji wiersza do jego domyślnej numeracji, która zlicza wiersze, które zostały ponownie numerowane przez poprzednią dyrektywę.</span><span class="sxs-lookup"><span data-stu-id="ab159-106">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

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

<span data-ttu-id="ab159-107">Kompilacja daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ab159-107">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="ab159-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab159-108">Remarks</span></span>

<span data-ttu-id="ab159-109">Dyrektywa `#line` może być używana w zautomatyzowanym, pośrednim kroku w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ab159-109">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="ab159-110">Na przykład jeśli wiersze zostały usunięte z oryginalnego pliku kodu źródłowego, ale nadal chcesz, aby kompilator generował dane wyjściowe na `#line`podstawie oryginalnej numeracji wierszy w pliku, można usunąć wiersze, a następnie symulować oryginalną numeracz wiersza z .</span><span class="sxs-lookup"><span data-stu-id="ab159-110">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="ab159-111">Dyrektywa `#line hidden` ukrywa kolejne wiersze z debugera, tak aby podczas kroków dewelopera `#line hidden` za `#line` pośrednictwem kodu, wszelkie `#line hidden` wiersze między a i następnej dyrektywy (przy założeniu, że nie jest to inna dyrektywa) zostanie nadepnięcie.</span><span class="sxs-lookup"><span data-stu-id="ab159-111">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="ab159-112">Ta opcja może również służyć do umożliwienia ASP.NET rozróżniania kodu zdefiniowanego przez użytkownika i wygenerowanego maszynowo.</span><span class="sxs-lookup"><span data-stu-id="ab159-112">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="ab159-113">Mimo że ASP.NET jest głównym konsumentem tej funkcji, jest prawdopodobne, że więcej generatorów źródłowych będzie z niej korzystać.</span><span class="sxs-lookup"><span data-stu-id="ab159-113">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="ab159-114">Dyrektywa `#line hidden` nie ma wpływu na nazwy plików ani numery wierszy w raportowaniu błędów.</span><span class="sxs-lookup"><span data-stu-id="ab159-114">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="ab159-115">Oznacza to, że jeśli wystąpi błąd w ukrytym bloku, kompilator zgłosi bieżącą nazwę pliku i numer wiersza błędu.</span><span class="sxs-lookup"><span data-stu-id="ab159-115">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="ab159-116">Dyrektywa `#line filename` określa nazwę pliku, który ma być wyświetlany w danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ab159-116">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="ab159-117">Domyślnie używana jest rzeczywista nazwa pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="ab159-117">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="ab159-118">Nazwa pliku musi być w podwójnych cudzysłowie ("") i musi być poprzedzona numerem wiersza.</span><span class="sxs-lookup"><span data-stu-id="ab159-118">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="ab159-119">Plik kodu źródłowego może `#line` mieć dowolną liczbę dyrektyw.</span><span class="sxs-lookup"><span data-stu-id="ab159-119">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="ab159-120">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="ab159-120">Example 1</span></span>

<span data-ttu-id="ab159-121">W poniższym przykładzie pokazano, jak debuger ignoruje ukryte wiersze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ab159-121">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="ab159-122">Po uruchomieniu przykładu wyświetli się trzy wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="ab159-122">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="ab159-123">Jednak po ustawieniu punktu przerwania, jak pokazano w przykładzie i naciśnij F10 krok po kroku kodu, można zauważyć, że debuger ignoruje ukryty wiersz.</span><span class="sxs-lookup"><span data-stu-id="ab159-123">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="ab159-124">Należy również zauważyć, że nawet jeśli ustawisz punkt przerwania w ukrytym wierszu, debuger nadal będzie go ignorować.</span><span class="sxs-lookup"><span data-stu-id="ab159-124">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ab159-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab159-125">See also</span></span>

- [<span data-ttu-id="ab159-126">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="ab159-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ab159-127">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="ab159-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ab159-128">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="ab159-128">C# Preprocessor Directives</span></span>](./index.md)
