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
ms.openlocfilehash: 5de7e565560928b1867ba96c8937fd354c276806
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774122"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="73447-102">Main () i argumenty wiersza polecenia (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="73447-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="73447-103">Metoda `Main` jest punktem wejścia C# aplikacji.</span><span class="sxs-lookup"><span data-stu-id="73447-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="73447-104">(Biblioteki i usługi nie wymagają `Main` metody jako punktu wejścia.) Gdy aplikacja jest uruchomiona, Metoda `Main` jest pierwszą metodą, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="73447-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="73447-105">W C# programie może istnieć tylko jeden punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="73447-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="73447-106">Jeśli masz więcej niż jedną klasę, która ma metodę `Main`, musisz skompilować program z opcją kompilatora **/Main** , aby określić, która metoda `Main` ma być używana jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="73447-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="73447-107">Aby uzyskać więcej informacji, zobacz [— MainC# (opcje kompilatora)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="73447-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="73447-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="73447-108">Overview</span></span>

- <span data-ttu-id="73447-109">Metoda `Main` jest punktem wejścia programu wykonywalnego; jest to miejsce, w którym kontrola programu zaczyna się i skończy.</span><span class="sxs-lookup"><span data-stu-id="73447-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="73447-110">`Main` jest zadeklarowana wewnątrz klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="73447-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="73447-111">`Main` musi być [statyczna](../../language-reference/keywords/static.md) i nie musi być [publiczny](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="73447-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="73447-112">(W poprzednim przykładzie otrzymuje on domyślny dostęp do [prywatnego](../../language-reference/keywords/private.md)). Otaczająca Klasa lub struktura nie musi być statyczna.</span><span class="sxs-lookup"><span data-stu-id="73447-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="73447-113">`Main` może mieć `void`, `int` lub, zaczynając od C# 7,1, `Task` lub `Task<int>` typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="73447-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="73447-114">Jeśli i tylko wtedy, gdy `Main` zwraca `Task` lub `Task<int>`, deklaracja `Main` może zawierać modyfikator [`async`](../../language-reference/keywords/async.md) .</span><span class="sxs-lookup"><span data-stu-id="73447-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="73447-115">Należy zauważyć, że ta metoda nie wyklucza metody `async void Main`.</span><span class="sxs-lookup"><span data-stu-id="73447-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="73447-116">Metodę `Main` można zadeklarować z parametrem `string[]` zawierającym argumenty wiersza polecenia lub bez niego.</span><span class="sxs-lookup"><span data-stu-id="73447-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="73447-117">W przypadku tworzenia aplikacji systemu Windows przy użyciu programu Visual Studio można dodać parametr ręcznie lub użyć metody <xref:System.Environment.GetCommandLineArgs>, aby uzyskać [argumenty wiersza polecenia](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="73447-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="73447-118">Parametry są odczytywane jako argumenty wiersza polecenia indeksowane przez zero.</span><span class="sxs-lookup"><span data-stu-id="73447-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="73447-119">W przeciwieństwie do C++języka C, nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia w tablicy `args`, ale jest to pierwszy element metody <xref:System.Environment.GetCommandLineArgs>.</span><span class="sxs-lookup"><span data-stu-id="73447-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="73447-120">Dodanie `async` i `Task` `Task<int>` typy zwracane upraszcza kod programu, gdy aplikacje konsolowe muszą uruchamiać i `await` operacje asynchroniczne w `Main`.</span><span class="sxs-lookup"><span data-stu-id="73447-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="73447-121">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="73447-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="73447-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73447-122">See also</span></span>

- [<span data-ttu-id="73447-123">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="73447-123">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="73447-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="73447-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="73447-125">Metody</span><span class="sxs-lookup"><span data-stu-id="73447-125">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="73447-126">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="73447-126">Inside a C# Program</span></span>](../inside-a-program/index.md)
