---
title: egzterzolog - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: c121d810e64b5fa27f105f814253c0752e028a95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713540"
---
# <a name="extern-c-reference"></a><span data-ttu-id="1926e-102">extern (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1926e-102">extern (C# Reference)</span></span>

<span data-ttu-id="1926e-103">Modyfikator `extern` jest używany do deklarowania metody, która jest implementowana zewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="1926e-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="1926e-104">Typowe użycie modyfikatora `extern` `DllImport` jest z atrybutem, gdy używasz usług Interop wywołać do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="1926e-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="1926e-105">W takim przypadku metoda musi być `static`również zadeklarowana jako , jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1926e-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="1926e-106">Słowo `extern` kluczowe można również zdefiniować alias złożenia zewnętrznego, co umożliwia odwoływanie się do różnych wersji tego samego komponentu z poziomu jednego zestawu.</span><span class="sxs-lookup"><span data-stu-id="1926e-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="1926e-107">Aby uzyskać więcej informacji, zobacz [alias extern](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="1926e-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="1926e-108">Jest to błąd, aby `extern` użyć [abstrakcyjne](abstract.md) i modyfikatory razem do modyfikowania tego samego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1926e-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="1926e-109">Za `extern` pomocą modyfikatora oznacza, że metoda jest implementowana `abstract` poza kodem C#, podczas gdy przy użyciu modyfikatora oznacza, że implementacja metody nie jest dostępna w klasie.</span><span class="sxs-lookup"><span data-stu-id="1926e-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="1926e-110">Użycie słowa kluczowego extern podlega większym ograniczeniom w języku C# niż w języku C++.</span><span class="sxs-lookup"><span data-stu-id="1926e-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="1926e-111">Aby porównać to słowo kluczowe w języku C# z wersją w języku C++, zobacz temat „Używanie słowa kluczowego extern w celu określenia powiązania” w dokumentacji języka C++.</span><span class="sxs-lookup"><span data-stu-id="1926e-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="1926e-112">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="1926e-112">Example 1</span></span>

<span data-ttu-id="1926e-113">W tym przykładzie program odbiera ciąg od użytkownika i wyświetla go wewnątrz okna komunikatu.</span><span class="sxs-lookup"><span data-stu-id="1926e-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="1926e-114">Program używa `MessageBox` metody zaimportowanej z biblioteki User32.dll.</span><span class="sxs-lookup"><span data-stu-id="1926e-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="1926e-115">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="1926e-115">Example 2</span></span>

<span data-ttu-id="1926e-116">W tym przykładzie przedstawiono program C#, który wywołuje do biblioteki C (natywnej biblioteki DLL).</span><span class="sxs-lookup"><span data-stu-id="1926e-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="1926e-117">Utwórz następujący plik C `cmdll.c`i nawadom go nas:</span><span class="sxs-lookup"><span data-stu-id="1926e-117">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="1926e-118">Otwórz okno wiersza polecenia programu Visual Studio x64 (lub x32) Z `cmdll.c` katalogu instalacyjnego programu Visual Studio i skompiluj plik, wpisując cl **-LD cmdll.c** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="1926e-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="1926e-119">W tym samym katalogu utwórz następujący plik `cm.cs`Języka C# i najmiej nazwę:</span><span class="sxs-lookup"><span data-stu-id="1926e-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

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

4. <span data-ttu-id="1926e-120">Otwórz okno wiersza polecenia programu Visual Studio x64 (lub x32) Z `cm.cs` katalogu instalacyjnego programu Visual Studio i skompiluj plik, wpisując:</span><span class="sxs-lookup"><span data-stu-id="1926e-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="1926e-121">**csc cm.cs** (dla wiersza polecenia x64) —lub — **csc -platform:x86 cm.cs** (dla wiersza polecenia x32)</span><span class="sxs-lookup"><span data-stu-id="1926e-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="1926e-122">Spowoduje to utworzenie pliku `cm.exe`wykonywalnego .</span><span class="sxs-lookup"><span data-stu-id="1926e-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="1926e-123">Uruchom polecenie `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="1926e-123">Run `cm.exe`.</span></span> <span data-ttu-id="1926e-124">Metoda `SampleMethod` przekazuje wartość 5 do pliku DLL, który zwraca wartość pomnożoną przez 10.</span><span class="sxs-lookup"><span data-stu-id="1926e-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="1926e-125">Program generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1926e-125">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="1926e-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1926e-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1926e-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1926e-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="1926e-128">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="1926e-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1926e-129">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="1926e-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1926e-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1926e-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1926e-131">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="1926e-131">Modifiers</span></span>](index.md)
