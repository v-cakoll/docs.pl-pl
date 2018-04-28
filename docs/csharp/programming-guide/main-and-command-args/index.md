---
title: Main() i argumenty wiersza poleceń (C# przewodnik programowania w języku)
ms.date: 08/02/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 75610174fdc91e4a29f17dc5563a7298c56a44e2
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="1072a-102">Main() i argumenty wiersza poleceń (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="1072a-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="1072a-103">`Main` Metoda jest punkt wejścia aplikacji C#.</span><span class="sxs-lookup"><span data-stu-id="1072a-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="1072a-104">(Bibliotek, usług i nie wymagają `Main` metody jako punkt wejścia.) Po uruchomieniu aplikacji `Main` pierwsza metoda wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="1072a-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="1072a-105">Może istnieć tylko jeden punkt wejścia w programie C#.</span><span class="sxs-lookup"><span data-stu-id="1072a-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="1072a-106">Jeśli masz więcej niż jedną klasę, która ma `Main` metody, należy skompilować programu z **/main** opcję kompilatora, aby określić, które `Main` metoda do użycia jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="1072a-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="1072a-107">Aby uzyskać więcej informacji, zobacz [/main (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1072a-107">For more information, see [/main (C# Compiler Options)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span></span>

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a><span data-ttu-id="1072a-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="1072a-108">Overview</span></span>

- <span data-ttu-id="1072a-109">`Main` Metody jest punkt wejścia programu wykonywalnego, a gdzie formantu programu początkowej i końcowej.</span><span class="sxs-lookup"><span data-stu-id="1072a-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="1072a-110">`Main` jest zadeklarowana w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="1072a-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="1072a-111">`Main` musi być [statycznych](../../../csharp/language-reference/keywords/static.md) i nie muszą być [publicznego](../../../csharp/language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="1072a-111">`Main` must be [static](../../../csharp/language-reference/keywords/static.md) and it need not be [public](../../../csharp/language-reference/keywords/public.md).</span></span> <span data-ttu-id="1072a-112">(W poprzedniego przykładu, otrzymuje dostęp do domyślnej z [prywatnej](../../../csharp/language-reference/keywords/private.md).) Otaczającej klasy lub struktury nie musi być statyczna.</span><span class="sxs-lookup"><span data-stu-id="1072a-112">(In the earlier example, it receives the default access of [private](../../../csharp/language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="1072a-113">`Main` może posiadać `void`, `int`, lub w programie C# 7.1, `Task`, lub `Task<int>` typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="1072a-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="1072a-114">Tylko wtedy, gdy `Main` zwraca `Task` lub `Task<int>`, deklaracja `Main` mogą obejmować [ `async` ](../../language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="1072a-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="1072a-115">Należy pamiętać, że jest to wyraźnie wyklucza `async void Main` metody.</span><span class="sxs-lookup"><span data-stu-id="1072a-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="1072a-116">`Main` Metody mogą być deklarowane z lub bez `string[]` parametr, który zawiera argumenty wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1072a-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="1072a-117">Przy użyciu programu Visual Studio do tworzenia aplikacji systemu Windows, użytkownik może ręcznie dodaj parametr w przeciwnym razie użyj <xref:System.Environment> klasy uzyskanie argumenty wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1072a-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="1072a-118">Parametry są odczytywane jako indeksie zero argumentów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1072a-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="1072a-119">W przeciwieństwie do C i C++ nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1072a-119">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="1072a-120">Dodanie `async` i `Task`, `Task<int>` zwracać typów upraszcza kodu programu, gdy konieczne uruchomienie aplikacji konsoli i `await` operacji asynchronicznych w `Main`.</span><span class="sxs-lookup"><span data-stu-id="1072a-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1072a-121">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1072a-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1072a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1072a-122">See also</span></span>
[<span data-ttu-id="1072a-123">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="1072a-123">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
[<span data-ttu-id="1072a-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1072a-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="1072a-125">Metody</span><span class="sxs-lookup"><span data-stu-id="1072a-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
[<span data-ttu-id="1072a-126">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="1072a-126">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
