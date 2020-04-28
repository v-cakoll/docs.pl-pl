---
title: Main () i argumenty wiersza polecenia — Przewodnik programowania w języku C#
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
ms.openlocfilehash: 190216b01ea416aedbca270a6d7a5acbf0c2e797
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200122"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="7045b-102">Main () i argumenty wiersza polecenia (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="7045b-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="7045b-103">`Main` Metoda jest punktem wejścia aplikacji języka C#.</span><span class="sxs-lookup"><span data-stu-id="7045b-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="7045b-104">(Biblioteki i usługi nie wymagają `Main` metody jako punktu wejścia.) Gdy aplikacja jest uruchomiona, `Main` jest to pierwsza metoda wywoływana.</span><span class="sxs-lookup"><span data-stu-id="7045b-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="7045b-105">W programie w języku C# może istnieć tylko jeden punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="7045b-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="7045b-106">Jeśli masz więcej niż jedną klasę, która ma `Main` metodę, musisz skompilować program z opcją kompilatora **/Main** , aby określić, która `Main` Metoda ma być używana jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="7045b-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="7045b-107">Aby uzyskać więcej informacji, zobacz [— Main (opcje kompilatora C#)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7045b-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="7045b-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="7045b-108">Overview</span></span>

- <span data-ttu-id="7045b-109">`Main` Metoda jest punktem wejścia programu wykonywalnego; jest to miejsce, w którym kontrola programu zaczyna się i skończy.</span><span class="sxs-lookup"><span data-stu-id="7045b-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="7045b-110">`Main`jest zadeklarowany wewnątrz klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="7045b-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="7045b-111">`Main`musi być [statyczna](../../language-reference/keywords/static.md) i nie musi być [publiczny](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="7045b-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="7045b-112">(W poprzednim przykładzie otrzymuje on domyślny dostęp do [prywatnego](../../language-reference/keywords/private.md)). Otaczająca Klasa lub struktura nie musi być statyczna.</span><span class="sxs-lookup"><span data-stu-id="7045b-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="7045b-113">`Main``void`może mieć parametr `int`,, lub, zaczynając od języka C# 7,1 `Task`lub `Task<int>` typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="7045b-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="7045b-114">Jeśli i tylko wtedy `Main` , gdy `Task` zwraca `Task<int>`lub, deklaracja `Main` może zawierać [`async`](../../language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="7045b-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="7045b-115">Należy zauważyć, że ta `async void Main` Metoda nie wyklucza metody.</span><span class="sxs-lookup"><span data-stu-id="7045b-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="7045b-116">`Main` Metodę można zadeklarować z parametrem zawierającym `string[]` argumenty wiersza polecenia lub bez niego.</span><span class="sxs-lookup"><span data-stu-id="7045b-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="7045b-117">Korzystając z programu Visual Studio do tworzenia aplikacji systemu Windows, można dodać parametr ręcznie lub użyć <xref:System.Environment.GetCommandLineArgs> metody do uzyskania [argumentów wiersza polecenia](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="7045b-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="7045b-118">Parametry są odczytywane jako argumenty wiersza polecenia indeksowane przez zero.</span><span class="sxs-lookup"><span data-stu-id="7045b-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="7045b-119">W przeciwieństwie do języka C i C++, nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia w `args` tablicy, ale jest to pierwszy element <xref:System.Environment.GetCommandLineArgs> metody.</span><span class="sxs-lookup"><span data-stu-id="7045b-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="7045b-120">Poniżej znajduje się lista prawidłowych `Main` podpisów:</span><span class="sxs-lookup"><span data-stu-id="7045b-120">The following is a list of valid `Main` signatures:</span></span>

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

<span data-ttu-id="7045b-121">Powyższe przykłady używają modyfikatora Public akcesor.</span><span class="sxs-lookup"><span data-stu-id="7045b-121">The preceding examples all use the public accessor modifier.</span></span> <span data-ttu-id="7045b-122">Jest to typowy, ale nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="7045b-122">That is typical, but not required.</span></span>

<span data-ttu-id="7045b-123">Dodawanie `async` `Task`i, `Task<int>` typy zwracane upraszczają kod programu, gdy aplikacje konsolowe muszą rozpoczynać pracę `await` i asynchroniczne operacje `Main`w programie.</span><span class="sxs-lookup"><span data-stu-id="7045b-123">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7045b-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7045b-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7045b-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7045b-125">See also</span></span>

- [<span data-ttu-id="7045b-126">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="7045b-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="7045b-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7045b-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7045b-128">Metody</span><span class="sxs-lookup"><span data-stu-id="7045b-128">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="7045b-129">Wewnątrz programu C#</span><span class="sxs-lookup"><span data-stu-id="7045b-129">Inside a C# Program</span></span>](../inside-a-program/index.md)
