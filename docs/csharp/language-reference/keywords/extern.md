---
title: extern — modyfikator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: d860f1a3c6917238a529093672dc5f2abc5ae066
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620200"
---
# <a name="extern-c-reference"></a><span data-ttu-id="41bd9-102">extern (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="41bd9-102">extern (C# Reference)</span></span>

<span data-ttu-id="41bd9-103">`extern` Modyfikator jest używany do deklarowania metody implementowanej zewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="41bd9-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="41bd9-104">Typowym zastosowaniem `extern` jest modyfikator `DllImport` atrybutu podczas korzystania z usług międzyoperacyjnych w celu wywołania kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="41bd9-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="41bd9-105">W tym przypadku metoda musi być także zadeklarowana jako `static`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="41bd9-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="41bd9-106">`extern` — Słowo kluczowe może także definiować alias zestawu zewnętrznego, który sprawia, że można odwoływać się do różnych wersji jednego składnika z poziomu jednego zestawu.</span><span class="sxs-lookup"><span data-stu-id="41bd9-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="41bd9-107">Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="41bd9-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="41bd9-108">Jest to błąd, aby użyć [abstrakcyjne](abstract.md) i `extern` Modyfikatory ze sobą, aby zmodyfikować tego samego członka.</span><span class="sxs-lookup"><span data-stu-id="41bd9-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="41bd9-109">Za pomocą `extern` modyfikator oznacza, że metoda jest zaimplementowana poza kodu C#, natomiast przy użyciu `abstract` modyfikator oznacza, że implementacja metody nie znajduje się w klasie.</span><span class="sxs-lookup"><span data-stu-id="41bd9-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="41bd9-110">Użycie słowa kluczowego extern podlega większym ograniczeniom w języku C# niż w języku C++.</span><span class="sxs-lookup"><span data-stu-id="41bd9-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="41bd9-111">Aby porównać to słowo kluczowe w języku C# z wersją w języku C++, zobacz temat „Używanie słowa kluczowego extern w celu określenia powiązania” w dokumentacji języka C++.</span><span class="sxs-lookup"><span data-stu-id="41bd9-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="41bd9-112">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="41bd9-112">Example 1</span></span>

<span data-ttu-id="41bd9-113">W tym przykładzie program odbiera ciąg od użytkownika i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="41bd9-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="41bd9-114">Program używa `MessageBox` metoda zaimportowany z biblioteki User32.dll.</span><span class="sxs-lookup"><span data-stu-id="41bd9-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="41bd9-115">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="41bd9-115">Example 2</span></span>

<span data-ttu-id="41bd9-116">Ten przykład ilustruje program C#, który wywołuje bibliotekę języka C (natywna Biblioteka DLL).</span><span class="sxs-lookup"><span data-stu-id="41bd9-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="41bd9-117">Utwórz następujący plik języka C i nadaj mu `cmdll.c`:</span><span class="sxs-lookup"><span data-stu-id="41bd9-117">Create the following C file and name it `cmdll.c`:</span></span>

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. <span data-ttu-id="41bd9-118">Otwórz okno Wiersz polecenia narzędzi Native Tools x64 (lub x32) programu Visual Studio w katalogu instalacyjnym programu Visual Studio i skompiluj `cmdll.c` pliku, wpisując **cl -LD cmdll.c** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="41bd9-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="41bd9-119">W tym samym katalogu Utwórz następujący plik języka C# i nadaj jej nazwę `cm.cs`:</span><span class="sxs-lookup"><span data-stu-id="41bd9-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

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

4. <span data-ttu-id="41bd9-120">Otwórz okno Wiersz polecenia narzędzi Native Tools x64 (lub x32) programu Visual Studio w katalogu instalacyjnym programu Visual Studio i skompiluj `cm.cs` pliku, wpisując:</span><span class="sxs-lookup"><span data-stu-id="41bd9-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

> <span data-ttu-id="41bd9-121">**CSC cm.cs** (x64 wiersza polecenia) — lub — **csc-platform: x 86 cm.cs** (dla x32 wiersza polecenia)</span><span class="sxs-lookup"><span data-stu-id="41bd9-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

<span data-ttu-id="41bd9-122">Spowoduje to utworzenie pliku wykonywalnego `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="41bd9-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="41bd9-123">Uruchom `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="41bd9-123">Run `cm.exe`.</span></span> <span data-ttu-id="41bd9-124">`SampleMethod` Metoda przekazuje wartość 5 do pliku DLL, który zwraca tę wartość pomnożoną przez 10.</span><span class="sxs-lookup"><span data-stu-id="41bd9-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="41bd9-125">Program generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="41bd9-125">The program produces the following output:</span></span>

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a><span data-ttu-id="41bd9-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="41bd9-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="41bd9-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41bd9-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="41bd9-128">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="41bd9-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="41bd9-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="41bd9-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="41bd9-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="41bd9-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="41bd9-131">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="41bd9-131">Modifiers</span></span>](modifiers.md)
