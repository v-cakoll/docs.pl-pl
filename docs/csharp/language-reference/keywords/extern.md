---
title: modyfikator extern — C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: c121d810e64b5fa27f105f814253c0752e028a95
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713540"
---
# <a name="extern-c-reference"></a><span data-ttu-id="928e4-102">extern (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="928e4-102">extern (C# Reference)</span></span>

<span data-ttu-id="928e4-103">Modyfikator `extern` jest używany do deklarowania metody, która jest implementowana zewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="928e4-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="928e4-104">Typowym zastosowaniem modyfikatora `extern` jest z atrybutem `DllImport`, gdy używasz usług międzyoperacyjnych do wywoływania kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="928e4-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="928e4-105">W takim przypadku metoda musi być również zadeklarowana jako `static`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="928e4-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="928e4-106">Za pomocą słowa kluczowego `extern` można także zdefiniować zewnętrzny alias zestawu, który umożliwia odwoływanie się do różnych wersji tego samego składnika z poziomu jednego zestawu.</span><span class="sxs-lookup"><span data-stu-id="928e4-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="928e4-107">Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="928e4-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="928e4-108">Nie można użyć modyfikatorów [abstrakcyjnych](abstract.md) i `extern`, aby zmodyfikować ten sam element członkowski.</span><span class="sxs-lookup"><span data-stu-id="928e4-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="928e4-109">Użycie modyfikatora `extern` oznacza, że metoda jest implementowana poza C# kodem, podczas gdy użycie modyfikatora `abstract` oznacza, że implementacja metody nie jest podana w klasie.</span><span class="sxs-lookup"><span data-stu-id="928e4-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="928e4-110">Użycie słowa kluczowego extern podlega większym ograniczeniom w języku C# niż w języku C++.</span><span class="sxs-lookup"><span data-stu-id="928e4-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="928e4-111">Aby porównać to słowo kluczowe w języku C# z wersją w języku C++, zobacz temat „Używanie słowa kluczowego extern w celu określenia powiązania” w dokumentacji języka C++.</span><span class="sxs-lookup"><span data-stu-id="928e4-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="928e4-112">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="928e4-112">Example 1</span></span>

<span data-ttu-id="928e4-113">W tym przykładzie program odbiera ciąg od użytkownika i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="928e4-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="928e4-114">Program używa metody `MessageBox` zaimportowanej z biblioteki User32. dll.</span><span class="sxs-lookup"><span data-stu-id="928e4-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="928e4-115">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="928e4-115">Example 2</span></span>

<span data-ttu-id="928e4-116">Ten przykład ilustruje C# program wywoływany do biblioteki języka C (NATYWNEJ biblioteki dll).</span><span class="sxs-lookup"><span data-stu-id="928e4-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="928e4-117">Utwórz następujący plik C i nadaj mu nazwę `cmdll.c`:</span><span class="sxs-lookup"><span data-stu-id="928e4-117">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="928e4-118">Otwórz okno wiersza polecenia narzędzi Visual Studio x64 (lub x32) Native Tools z katalogu instalacyjnego programu Visual Studio i skompiluj plik `cmdll.c`, wpisując **CL-LD cmdll. c** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="928e4-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="928e4-119">W tym samym katalogu Utwórz następujący C# plik i nadaj mu nazwę `cm.cs`:</span><span class="sxs-lookup"><span data-stu-id="928e4-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

    ```csharp
    // cm.cs
    using System;
    using System.Runtime.InteropServices;
    public class MainClass
    {
        [DllImport("Cmdll.dll")]
          public static extern int SampleMethod(int x);

        static void Main()
        {
            Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
        }
    }
    ```

4. <span data-ttu-id="928e4-120">Otwórz okno wiersza polecenia narzędzi Visual Studio x64 (lub x32) Native Tools z katalogu instalacyjnego programu Visual Studio i skompiluj plik `cm.cs`, wpisując:</span><span class="sxs-lookup"><span data-stu-id="928e4-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="928e4-121">**csc cm.cs** (wiersz polecenia x64) — lub — **CSC-platform: x86 cm.cs** (dla wiersza polecenia x32)</span><span class="sxs-lookup"><span data-stu-id="928e4-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="928e4-122">Spowoduje to utworzenie pliku wykonywalnego `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="928e4-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="928e4-123">Uruchom polecenie `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="928e4-123">Run `cm.exe`.</span></span> <span data-ttu-id="928e4-124">Metoda `SampleMethod` przekazuje wartość 5 do pliku DLL, który zwraca wartość pomnożoną przez 10.</span><span class="sxs-lookup"><span data-stu-id="928e4-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="928e4-125">Program tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="928e4-125">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="928e4-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="928e4-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="928e4-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="928e4-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="928e4-128">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="928e4-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="928e4-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="928e4-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="928e4-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="928e4-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="928e4-131">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="928e4-131">Modifiers</span></span>](index.md)
