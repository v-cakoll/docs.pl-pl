---
title: Main() i argumenty wiersza poleceń (C# Programming Guide)
ms.date: 08/02/2017
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
ms.openlocfilehash: 144d03edf28464717430bd0ae83db637578d8296
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698594"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="9c8a3-102">Main() i argumenty wiersza poleceń (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="9c8a3-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="9c8a3-103">`Main` Metodą jest punkt wejścia aplikacji w języku C#.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="9c8a3-104">(Biblioteki i usługi nie wymagają `Main` metodę jako punkt wejścia.) Po uruchomieniu aplikacji `Main` metodą jest pierwsza metoda, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="9c8a3-105">Może istnieć tylko jeden punkt wejścia w programie C#.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="9c8a3-106">Jeśli masz więcej niż jedną klasę, która ma `Main` metody, należy skompilować program jest połączony z **/main** opcję kompilatora, aby określić, które `Main` metoda do użycia jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="9c8a3-107">Aby uzyskać więcej informacji, zobacz [/main (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="9c8a3-107">For more information, see [/main (C# Compiler Options)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span></span>

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a><span data-ttu-id="9c8a3-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="9c8a3-108">Overview</span></span>

- <span data-ttu-id="9c8a3-109">`Main` Metodą jest punkt wejścia programu wykonywalnego; gdzie kontrolę nad programem rozpoczyna i kończy.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="9c8a3-110">`Main` jest zadeklarowana wewnątrz klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="9c8a3-111">`Main` musi być [statyczne](../../../csharp/language-reference/keywords/static.md) i nie muszą być [publicznych](../../../csharp/language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="9c8a3-111">`Main` must be [static](../../../csharp/language-reference/keywords/static.md) and it need not be [public](../../../csharp/language-reference/keywords/public.md).</span></span> <span data-ttu-id="9c8a3-112">(We wcześniejszym przykładzie otrzymuje dostęp do domyślnej [prywatnej](../../../csharp/language-reference/keywords/private.md).) Otaczającej klasy lub struktury nie musi być statyczna.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-112">(In the earlier example, it receives the default access of [private](../../../csharp/language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="9c8a3-113">`Main` można albo mieć `void`, `int`, lub rozpocząć budowanie C# 7.1 `Task`, lub `Task<int>` typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="9c8a3-114">Tylko wtedy, gdy `Main` zwraca `Task` lub `Task<int>`, deklaracja `Main` mogą obejmować [ `async` ](../../language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="9c8a3-115">Należy zauważyć, że specjalnie nie obejmuje to `async void Main` metody.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="9c8a3-116">`Main` Metody mogą być deklarowane z lub bez `string[]` parametr, który zawiera argumenty wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="9c8a3-117">Przy użyciu programu Visual Studio do tworzenia aplikacji Windows, użytkownik może ręcznie dodaj parametr — w przeciwnym razie użyj <xref:System.Environment> klasy w celu uzyskiwania argumentów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="9c8a3-118">Parametry są odczytywane jako argumenty wiersza polecenia o indeksie zero.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="9c8a3-119">W przeciwieństwie do C i C++ nazwę programu, nie jest traktowana jako pierwszy argument wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-119">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="9c8a3-120">Dodanie `async` i `Task`, `Task<int>` zwraca typy upraszcza kod programu, gdy aplikacje konsoli, musisz uruchomić i `await` operacji asynchronicznych w `Main`.</span><span class="sxs-lookup"><span data-stu-id="9c8a3-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9c8a3-121">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9c8a3-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9c8a3-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c8a3-122">See Also</span></span>

- [<span data-ttu-id="9c8a3-123">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="9c8a3-123">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [<span data-ttu-id="9c8a3-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9c8a3-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9c8a3-125">Metody</span><span class="sxs-lookup"><span data-stu-id="9c8a3-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [<span data-ttu-id="9c8a3-126">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="9c8a3-126">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
