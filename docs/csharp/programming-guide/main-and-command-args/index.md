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
ms.openlocfilehash: 723884dd448232777ae2cfeac5bfcf5ea24363b0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007744"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="23752-102">Main () i argumenty wiersza polecenia (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="23752-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="23752-103">`Main`Metoda jest punktem wejścia aplikacji języka C#.</span><span class="sxs-lookup"><span data-stu-id="23752-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="23752-104">(Biblioteki i usługi nie wymagają `Main` metody jako punktu wejścia.) Gdy aplikacja jest uruchomiona, jest to `Main` Pierwsza metoda wywoływana.</span><span class="sxs-lookup"><span data-stu-id="23752-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

<span data-ttu-id="23752-105">W programie w języku C# może istnieć tylko jeden punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="23752-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="23752-106">Jeśli masz więcej niż jedną klasę, która ma `Main` metodę, musisz skompilować program z `-main` opcją kompilatora, aby określić, która `Main` Metoda ma być używana jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="23752-106">If you have more than one class that has a `Main` method, you must compile your program with the `-main` compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="23752-107">Aby uzyskać więcej informacji, zobacz [— Main (opcje kompilatora C#)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="23752-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="23752-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="23752-108">Overview</span></span>

- <span data-ttu-id="23752-109">`Main`Metoda jest punktem wejścia programu wykonywalnego; jest to miejsce, w którym kontrola programu zaczyna się i skończy.</span><span class="sxs-lookup"><span data-stu-id="23752-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="23752-110">`Main`jest zadeklarowany wewnątrz klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="23752-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="23752-111">`Main`musi być [statyczna](../../language-reference/keywords/static.md) i nie musi być [publiczny](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="23752-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="23752-112">(W poprzednim przykładzie otrzymuje on domyślny dostęp do [prywatnego](../../language-reference/keywords/private.md)). Otaczająca Klasa lub struktura nie musi być statyczna.</span><span class="sxs-lookup"><span data-stu-id="23752-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="23752-113">`Main`może mieć parametr `void` , `int` , lub, zaczynając od języka C# 7,1 `Task` lub `Task<int>` typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="23752-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="23752-114">Jeśli i tylko wtedy `Main` , gdy zwraca `Task` lub `Task<int>` , deklaracja `Main` może zawierać [`async`](../../language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="23752-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="23752-115">Należy zauważyć, że ta metoda nie wyklucza `async void Main` metody.</span><span class="sxs-lookup"><span data-stu-id="23752-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="23752-116">`Main`Metodę można zadeklarować z `string[]` parametrem zawierającym argumenty wiersza polecenia lub bez niego.</span><span class="sxs-lookup"><span data-stu-id="23752-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="23752-117">Korzystając z programu Visual Studio do tworzenia aplikacji systemu Windows, można dodać parametr ręcznie lub użyć <xref:System.Environment.GetCommandLineArgs> metody do uzyskania [argumentów wiersza polecenia](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="23752-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="23752-118">Parametry są odczytywane jako argumenty wiersza polecenia indeksowane przez zero.</span><span class="sxs-lookup"><span data-stu-id="23752-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="23752-119">W przeciwieństwie do języka C i C++, nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia w `args` tablicy, ale jest to pierwszy element <xref:System.Environment.GetCommandLineArgs> metody.</span><span class="sxs-lookup"><span data-stu-id="23752-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="23752-120">Poniżej znajduje się lista prawidłowych `Main` podpisów:</span><span class="sxs-lookup"><span data-stu-id="23752-120">The following is a list of valid `Main` signatures:</span></span>

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

<span data-ttu-id="23752-121">Powyższe przykłady używają modyfikatora Public akcesor.</span><span class="sxs-lookup"><span data-stu-id="23752-121">The preceding examples all use the public accessor modifier.</span></span> <span data-ttu-id="23752-122">Jest to typowy, ale nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="23752-122">That is typical, but not required.</span></span>

<span data-ttu-id="23752-123">Dodawanie `async` i `Task` , `Task<int>` typy zwracane upraszczają kod programu, gdy aplikacje konsolowe muszą rozpoczynać pracę i `await` asynchroniczne operacje w programie `Main` .</span><span class="sxs-lookup"><span data-stu-id="23752-123">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="23752-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="23752-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="23752-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23752-125">See also</span></span>

- [<span data-ttu-id="23752-126">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="23752-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="23752-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="23752-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="23752-128">Metody</span><span class="sxs-lookup"><span data-stu-id="23752-128">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="23752-129">Wewnątrz programu C#</span><span class="sxs-lookup"><span data-stu-id="23752-129">Inside a C# Program</span></span>](../inside-a-program/index.md)
