---
title: Argumenty Main() i command-line — Przewodnik programowania C#
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
ms.openlocfilehash: 0571ec6dbc42f103ec922a6b2b13a52510640a78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75700604"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="36080-102">Argumenty Main() i command-line (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="36080-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="36080-103">Metoda `Main` jest punktem wejścia aplikacji C#.</span><span class="sxs-lookup"><span data-stu-id="36080-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="36080-104">(Biblioteki i usługi nie `Main` wymagają metody jako punktu wejścia). Po uruchomieniu aplikacji `Main` metoda jest pierwszą metodą, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="36080-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="36080-105">W programie C# może być tylko jeden punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="36080-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="36080-106">Jeśli masz więcej niż jedną `Main` klasę, która ma metodę, należy skompilować program `Main` z **/main** kompilator opcji, aby określić metodę do użycia jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="36080-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="36080-107">Aby uzyskać więcej informacji, zobacz [-main (Opcje kompilatora C#)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="36080-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="36080-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="36080-108">Overview</span></span>

- <span data-ttu-id="36080-109">Metoda `Main` jest punktem wejścia programu wykonywalnego; to jest miejsce, w którym rozpoczyna się i kończy kontrolka programu.</span><span class="sxs-lookup"><span data-stu-id="36080-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="36080-110">`Main`jest zadeklarowana wewnątrz klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="36080-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="36080-111">`Main`musi być [statyczny](../../language-reference/keywords/static.md) i nie musi być [publiczny.](../../language-reference/keywords/public.md)</span><span class="sxs-lookup"><span data-stu-id="36080-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="36080-112">(We wcześniejszym przykładzie otrzymuje domyślny dostęp [prywatnych](../../language-reference/keywords/private.md).) Otaczającej klasy lub struktury nie jest wymagane, aby być statyczne.</span><span class="sxs-lookup"><span data-stu-id="36080-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="36080-113">`Main`może mieć `void`, `int`lub, począwszy od C `Task`# `Task<int>` 7.1, lub typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="36080-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="36080-114">Jeśli i `Main` tylko `Task` wtedy, gdy zwraca `Task<int>`lub , deklaracja `Main` może zawierać [`async`](../../language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="36080-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="36080-115">Należy zauważyć, że to `async void Main` wyraźnie wyklucza metodę.</span><span class="sxs-lookup"><span data-stu-id="36080-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="36080-116">Metodę `Main` można zadeklarować z `string[]` parametrem lub bez, który zawiera argumenty wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="36080-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="36080-117">Korzystając z programu Visual Studio do tworzenia aplikacji systemu Windows, można dodać parametr ręcznie lub użyć <xref:System.Environment.GetCommandLineArgs> tej metody do uzyskania [argumentów wiersza polecenia](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="36080-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="36080-118">Parametry są odczytywane jako argumenty wiersza polecenia indeksowane zero.</span><span class="sxs-lookup"><span data-stu-id="36080-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="36080-119">W przeciwieństwie do C i C++, nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia w `args` tablicy, ale jest pierwszym elementem <xref:System.Environment.GetCommandLineArgs> metody.</span><span class="sxs-lookup"><span data-stu-id="36080-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="36080-120">Poniżej znajduje się lista `Main` prawidłowych podpisów:</span><span class="sxs-lookup"><span data-stu-id="36080-120">The following is a list of valid `Main` signatures:</span></span>

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

<span data-ttu-id="36080-121">Dodawanie `async` i `Task`, `Task<int>` zwraca typy upraszcza kod programu, gdy aplikacje konsoli trzeba uruchomić i `await` operacji asynchronicznych w `Main`programie .</span><span class="sxs-lookup"><span data-stu-id="36080-121">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="36080-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="36080-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="36080-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36080-123">See also</span></span>

- [<span data-ttu-id="36080-124">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="36080-124">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="36080-125">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="36080-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="36080-126">Metody</span><span class="sxs-lookup"><span data-stu-id="36080-126">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="36080-127">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="36080-127">Inside a C# Program</span></span>](../inside-a-program/index.md)
