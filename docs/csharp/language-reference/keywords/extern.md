---
title: "extern (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 106ceb6a4acf57daa01919acb38e4245655fca2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="extern-c-reference"></a><span data-ttu-id="a9203-102">extern (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a9203-102">extern (C# Reference)</span></span>
<span data-ttu-id="a9203-103">`extern` Modyfikator służy do deklarowania metodę, która jest zaimplementowana zewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="a9203-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="a9203-104">Typowym zastosowaniem `extern` modyfikator jest z `DllImport` atrybutu podczas korzystania z międzyoperacyjnego usług do wywołania do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a9203-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="a9203-105">W tym przypadku metoda również musi być zadeklarowany jako `static`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a9203-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>  
  
```  
[DllImport("avifil32.dll")]  
private static extern void AVIFileInit();  
```  
  
 <span data-ttu-id="a9203-106">`extern` — Słowo kluczowe można również zdefiniować aliasu zewnętrznego zestawu, dzięki czemu można odwoływać się różne wersje tego samego składnika od w jednym zestawie.</span><span class="sxs-lookup"><span data-stu-id="a9203-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="a9203-107">Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](../../../csharp/language-reference/keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="a9203-107">For more information, see [extern alias](../../../csharp/language-reference/keywords/extern-alias.md).</span></span>  
  
 <span data-ttu-id="a9203-108">Jest błędem [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md) i `extern` Modyfikatory ze sobą, aby zmodyfikować tego samego członka.</span><span class="sxs-lookup"><span data-stu-id="a9203-108">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="a9203-109">Przy użyciu `extern` modyfikator oznacza, że metoda jest wykonywane poza kodu C# natomiast przy użyciu `abstract` modyfikator oznacza, że implementacja metody nie jest dostępny w klasie.</span><span class="sxs-lookup"><span data-stu-id="a9203-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>  
  
 <span data-ttu-id="a9203-110">Użycie słowa kluczowego extern podlega większym ograniczeniom w języku C# niż w języku C++.</span><span class="sxs-lookup"><span data-stu-id="a9203-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="a9203-111">Aby porównać to słowo kluczowe w języku C# z wersją w języku C++, zobacz temat „Używanie słowa kluczowego extern w celu określenia powiązania” w dokumentacji języka C++.</span><span class="sxs-lookup"><span data-stu-id="a9203-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9203-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9203-112">Example</span></span>  
 <span data-ttu-id="a9203-113">**Przykład 1.**</span><span class="sxs-lookup"><span data-stu-id="a9203-113">**Example 1.**</span></span> <span data-ttu-id="a9203-114">W tym przykładzie program odbiera ciąg od użytkownika i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a9203-114">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="a9203-115">Program używa `MessageBox` zaimportowany z biblioteki User32.dll metody.</span><span class="sxs-lookup"><span data-stu-id="a9203-115">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="a9203-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9203-116">Example</span></span>  
 <span data-ttu-id="a9203-117">**Przykład 2.**</span><span class="sxs-lookup"><span data-stu-id="a9203-117">**Example 2.**</span></span> <span data-ttu-id="a9203-118">W tym przykładzie przedstawiono program C#, który odwołuje się do biblioteki C (natywnej biblioteki DLL).</span><span class="sxs-lookup"><span data-stu-id="a9203-118">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>  
  
 1. <span data-ttu-id="a9203-119">Utworzyć następującego pliku C i nadaj mu nazwę `cmdll.c`:</span><span class="sxs-lookup"><span data-stu-id="a9203-119">Create the following C file and name it `cmdll.c`:</span></span>  
  
```  
// cmdll.c  
// Compile with: /LD  
int __declspec(dllexport) SampleMethod(int i)  
{  
   return i*10;  
}  
```  
  
## <a name="example"></a><span data-ttu-id="a9203-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9203-120">Example</span></span>  
 2. <span data-ttu-id="a9203-121">Otwórz okno Wiersz polecenia narzędzi natywnego x64 (lub x32) programu Visual Studio z poziomu katalogu instalacyjnego programu Visual Studio i skompilować `cmdll.c` pliku, wpisując **cl /LD cmdll.c** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a9203-121">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl /LD cmdll.c** at the command prompt.</span></span>  
  
 3. <span data-ttu-id="a9203-122">W tym samym katalogu, należy utworzyć następującego pliku C# i nadaj jej nazwę `cm.cs`:</span><span class="sxs-lookup"><span data-stu-id="a9203-122">In the same directory, create the following C# file and name it `cm.cs`:</span></span>  
  
```  
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
  
## <a name="example"></a><span data-ttu-id="a9203-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9203-123">Example</span></span>  
 3. <span data-ttu-id="a9203-124">Otwórz okno Wiersz polecenia narzędzi natywnego x64 (lub x32) programu Visual Studio z poziomu katalogu instalacyjnego programu Visual Studio i skompilować `cm.cs` pliku, wpisz:</span><span class="sxs-lookup"><span data-stu-id="a9203-124">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>  
  
> <span data-ttu-id="a9203-125">**CSC cm.cs** (dla x64 wiersza polecenia)</span><span class="sxs-lookup"><span data-stu-id="a9203-125">**csc cm.cs** (for the x64 command prompt)</span></span>   
>  <span data-ttu-id="a9203-126">—lub—</span><span class="sxs-lookup"><span data-stu-id="a9203-126">—or—</span></span>  
> <span data-ttu-id="a9203-127">**CSC — x 86 cm.cs** (dla x32 wiersza polecenia)</span><span class="sxs-lookup"><span data-stu-id="a9203-127">**csc /platform:x86 cm.cs** (for the x32 command prompt)</span></span>  
  
 <span data-ttu-id="a9203-128">Spowoduje to utworzenie pliku wykonywalnego `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="a9203-128">This will create the executable file `cm.exe`.</span></span>  
  
 4. <span data-ttu-id="a9203-129">Run `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="a9203-129">Run `cm.exe`.</span></span> <span data-ttu-id="a9203-130">`SampleMethod` Metoda przekazuje wartość 5 do pliku DLL, która zwraca wartość pomnożona przez 10.</span><span class="sxs-lookup"><span data-stu-id="a9203-130">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="a9203-131">Program tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a9203-131">The program produces the following output:</span></span>  
  
```  
SampleMethod() returns 50.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="a9203-132">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a9203-132">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a9203-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9203-133">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
 [<span data-ttu-id="a9203-134">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a9203-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a9203-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a9203-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a9203-136">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a9203-136">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a9203-137">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="a9203-137">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
