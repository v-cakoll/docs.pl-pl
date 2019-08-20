---
title: Main () i argumenty wiersza polecenia — C# Przewodnik programowania
ms.custom: seodec18
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
ms.openlocfilehash: db4464cdd3d98103bbc61b824081b59cb1e01cb9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588906"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="897da-102">Main () i argumenty wiersza polecenia (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="897da-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="897da-103">Metoda jest punktem wejścia C# aplikacji. `Main`</span><span class="sxs-lookup"><span data-stu-id="897da-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="897da-104">(Biblioteki i usługi nie wymagają `Main` metody jako punktu wejścia.) Gdy aplikacja jest uruchomiona, `Main` jest to pierwsza metoda wywoływana.</span><span class="sxs-lookup"><span data-stu-id="897da-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="897da-105">W C# programie może istnieć tylko jeden punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="897da-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="897da-106">Jeśli masz więcej niż jedną klasę, która ma `Main` metodę, musisz skompilować program z opcją kompilatora **/Main** , aby określić, która `Main` Metoda ma być używana jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="897da-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="897da-107">Aby uzyskać więcej informacji, zobacz [/MainC# (opcje kompilatora)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="897da-107">For more information, see [/main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="897da-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="897da-108">Overview</span></span>

- <span data-ttu-id="897da-109">`Main` Metoda jest punktem wejścia programu wykonywalnego; jest to miejsce, w którym kontrola programu zaczyna się i skończy.</span><span class="sxs-lookup"><span data-stu-id="897da-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="897da-110">`Main`jest zadeklarowany wewnątrz klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="897da-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="897da-111">`Main`musi być [statyczna](../../language-reference/keywords/static.md) i nie musi być [publiczny](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="897da-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="897da-112">(W poprzednim przykładzie otrzymuje on domyślny dostęp do [prywatnego](../../language-reference/keywords/private.md)). Otaczająca Klasa lub struktura nie musi być statyczna.</span><span class="sxs-lookup"><span data-stu-id="897da-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="897da-113">`Main``void`może mieć, `int`, lub, zaczynając od C# 7,1, `Task`lub `Task<int>` typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="897da-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="897da-114">Jeśli i tylko wtedy `Main` , gdy `Task` zwraca `Task<int>` `Main` lub, deklaracja może zawierać [`async`](../../language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="897da-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="897da-115">Należy zauważyć, że ta `async void Main` Metoda nie wyklucza metody.</span><span class="sxs-lookup"><span data-stu-id="897da-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="897da-116">Metodę można zadeklarować z parametrem zawierającym argumenty wiersza polecenia lub bez niego `string[]`. `Main`</span><span class="sxs-lookup"><span data-stu-id="897da-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="897da-117">W przypadku tworzenia aplikacji systemu Windows przy użyciu programu Visual Studio można dodać parametr ręcznie lub użyć <xref:System.Environment> klasy w celu uzyskania argumentów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="897da-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="897da-118">Parametry są odczytywane jako argumenty wiersza polecenia indeksowane przez zero.</span><span class="sxs-lookup"><span data-stu-id="897da-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="897da-119">W przeciwieństwie do C++języka C i, nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="897da-119">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="897da-120">`async` Dodawanie i, `await` `Task` `Main`typy zwracane upraszczają kod programu, gdy aplikacje konsolowe muszą rozpoczynać pracę i asynchroniczne operacje w programie. `Task<int>`</span><span class="sxs-lookup"><span data-stu-id="897da-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="897da-121">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="897da-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="897da-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="897da-122">See also</span></span>

- [<span data-ttu-id="897da-123">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="897da-123">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="897da-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="897da-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="897da-125">Metody</span><span class="sxs-lookup"><span data-stu-id="897da-125">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="897da-126">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="897da-126">Inside a C# Program</span></span>](../inside-a-program/index.md)
