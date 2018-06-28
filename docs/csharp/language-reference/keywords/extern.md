---
title: extern — modyfikator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: aca1a9fa0b57e9b3b0a515a805039ade2fe0c2f1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027918"
---
# <a name="extern-c-reference"></a><span data-ttu-id="418ac-102">extern (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="418ac-102">extern (C# Reference)</span></span>

<span data-ttu-id="418ac-103">`extern` Modyfikator służy do deklarowania metodę, która jest zaimplementowana zewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="418ac-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="418ac-104">Typowym zastosowaniem `extern` modyfikator jest z `DllImport` atrybutu podczas korzystania z międzyoperacyjnego usług do wywołania do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="418ac-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="418ac-105">W tym przypadku metoda również musi być zadeklarowany jako `static`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="418ac-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="418ac-106">`extern` — Słowo kluczowe można również zdefiniować aliasu zewnętrznego zestawu, dzięki czemu można odwoływać się różne wersje tego samego składnika od w jednym zestawie.</span><span class="sxs-lookup"><span data-stu-id="418ac-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="418ac-107">Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="418ac-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="418ac-108">Jest błędem [abstrakcyjny](abstract.md) i `extern` Modyfikatory ze sobą, aby zmodyfikować tego samego członka.</span><span class="sxs-lookup"><span data-stu-id="418ac-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="418ac-109">Przy użyciu `extern` modyfikator oznacza, że metoda jest wykonywane poza kodu C# natomiast przy użyciu `abstract` modyfikator oznacza, że implementacja metody nie jest dostępny w klasie.</span><span class="sxs-lookup"><span data-stu-id="418ac-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="418ac-110">Użycie słowa kluczowego extern podlega większym ograniczeniom w języku C# niż w języku C++.</span><span class="sxs-lookup"><span data-stu-id="418ac-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="418ac-111">Aby porównać to słowo kluczowe w języku C# z wersją w języku C++, zobacz temat „Używanie słowa kluczowego extern w celu określenia powiązania” w dokumentacji języka C++.</span><span class="sxs-lookup"><span data-stu-id="418ac-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="418ac-112">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="418ac-112">Example 1</span></span>

<span data-ttu-id="418ac-113">W tym przykładzie program odbiera ciąg od użytkownika i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="418ac-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="418ac-114">Program używa `MessageBox` zaimportowany z biblioteki User32.dll metody.</span><span class="sxs-lookup"><span data-stu-id="418ac-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="418ac-115">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="418ac-115">Example 2</span></span>

<span data-ttu-id="418ac-116">W tym przykładzie przedstawiono program C#, który odwołuje się do biblioteki C (natywnej biblioteki DLL).</span><span class="sxs-lookup"><span data-stu-id="418ac-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="418ac-117">Utworzyć następującego pliku C i nadaj mu nazwę `cmdll.c`:</span><span class="sxs-lookup"><span data-stu-id="418ac-117">Create the following C file and name it `cmdll.c`:</span></span>

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. <span data-ttu-id="418ac-118">Otwórz okno Wiersz polecenia narzędzi natywnego x64 (lub x32) programu Visual Studio z poziomu katalogu instalacyjnego programu Visual Studio i skompilować `cmdll.c` pliku, wpisując **cl -LD cmdll.c** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="418ac-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="418ac-119">W tym samym katalogu, należy utworzyć następującego pliku C# i nadaj jej nazwę `cm.cs`:</span><span class="sxs-lookup"><span data-stu-id="418ac-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

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

4. <span data-ttu-id="418ac-120">Otwórz okno Wiersz polecenia narzędzi natywnego x64 (lub x32) programu Visual Studio z poziomu katalogu instalacyjnego programu Visual Studio i skompilować `cm.cs` pliku, wpisz:</span><span class="sxs-lookup"><span data-stu-id="418ac-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

> <span data-ttu-id="418ac-121">**CSC cm.cs** (dla x64 wiersza polecenia) — lub — **csc-platform: x 86 cm.cs** (dla x32 wiersza polecenia)</span><span class="sxs-lookup"><span data-stu-id="418ac-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

<span data-ttu-id="418ac-122">Spowoduje to utworzenie pliku wykonywalnego `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="418ac-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="418ac-123">Uruchom `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="418ac-123">Run `cm.exe`.</span></span> <span data-ttu-id="418ac-124">`SampleMethod` Metoda przekazuje wartość 5 do pliku DLL, która zwraca wartość pomnożona przez 10.</span><span class="sxs-lookup"><span data-stu-id="418ac-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="418ac-125">Program tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="418ac-125">The program produces the following output:</span></span>

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a><span data-ttu-id="418ac-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="418ac-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="418ac-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="418ac-127">See also</span></span>

<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
[<span data-ttu-id="418ac-128">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="418ac-128">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="418ac-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="418ac-129">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="418ac-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="418ac-130">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="418ac-131">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="418ac-131">Modifiers</span></span>](modifiers.md)  