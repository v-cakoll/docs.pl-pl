---
title: Implementowanie metody DisposeAsync
description: ''
ms.date: 06/02/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: c4f541d5a4f5b5fd31b344a299789d86cd78424c
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2020
ms.locfileid: "84311015"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="37714-102">Implementowanie metody DisposeAsync</span><span class="sxs-lookup"><span data-stu-id="37714-102">Implement a DisposeAsync method</span></span>

<span data-ttu-id="37714-103"><xref:System.IAsyncDisposable?displayProperty=nameWithType>Interfejs został wprowadzony jako część języka C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="37714-103">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="37714-104">Metodę należy zaimplementować <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> , gdy trzeba przeprowadzić Oczyszczanie zasobów, tak jak podczas [implementowania metody Dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="37714-104">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="37714-105">Jedną z najważniejszych różnic jest jednak to, że ta implementacja umożliwia asynchroniczne czyszczenie operacji.</span><span class="sxs-lookup"><span data-stu-id="37714-105">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="37714-106"><xref:System.IAsyncDisposable.DisposeAsync>Zwraca wartość <xref:System.Threading.Tasks.ValueTask> reprezentującą asynchroniczną operację Dispose.</span><span class="sxs-lookup"><span data-stu-id="37714-106">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="37714-107">Typowo, że podczas implementowania <xref:System.IAsyncDisposable> interfejsu, klasy również implementują <xref:System.IDisposable> interfejs.</span><span class="sxs-lookup"><span data-stu-id="37714-107">It is typical that when implementing the <xref:System.IAsyncDisposable> interface, classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="37714-108">Dobry wzorzec implementacji <xref:System.IAsyncDisposable> interfejsu jest przygotowany do synchronicznej lub asynchronicznej operacji Dispose.</span><span class="sxs-lookup"><span data-stu-id="37714-108">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous, or asynchronous dispose.</span></span> <span data-ttu-id="37714-109">Wszystkie wskazówki dotyczące implementacji wzorca Dispose dotyczą implementacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="37714-109">All of the guidance for implementing the dispose pattern applies to the asynchronous implementation.</span></span> <span data-ttu-id="37714-110">W tym artykule założono, że wiesz już, jak [zaimplementować metodę Dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="37714-110">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="37714-111">DisposeAsync () i DisposeAsyncCore ()</span><span class="sxs-lookup"><span data-stu-id="37714-111">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="37714-112"><xref:System.IAsyncDisposable>Interfejs deklaruje pojedynczą metodę bez parametrów, <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="37714-112">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="37714-113">Każda Klasa Niezapieczętowana powinna mieć dodatkową `DisposeAsyncCore()` metodę, która również zwraca wartość <xref:System.Threading.Tasks.ValueTask> .</span><span class="sxs-lookup"><span data-stu-id="37714-113">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="37714-114">`public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> Implementacja, która nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="37714-114">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="37714-115">`protected virtual ValueTask DisposeAsyncCore()`Metoda, której sygnatura:</span><span class="sxs-lookup"><span data-stu-id="37714-115">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

```csharp
protected virtual ValueTask DisposeAsyncCore()
{
}
```

<span data-ttu-id="37714-116">`DisposeAsyncCore()`Metoda polega na `virtual` tym, że klasy pochodne mogą definiować dodatkowe czyszczenie w ich zastąpień.</span><span class="sxs-lookup"><span data-stu-id="37714-116">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

### <a name="the-disposeasync-method"></a><span data-ttu-id="37714-117">DisposeAsync () — Metoda</span><span class="sxs-lookup"><span data-stu-id="37714-117">The DisposeAsync() method</span></span>

<span data-ttu-id="37714-118">`public` `DisposeAsync()` Metoda bez parametrów jest wywoływana niejawnie w `await using` instrukcji i jej celem jest zwolnienie niezarządzanych zasobów, wykonanie ogólnego oczyszczenia i wskazanie, że finalizator, jeśli taki istnieje, nie musi.</span><span class="sxs-lookup"><span data-stu-id="37714-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, needn't run.</span></span> <span data-ttu-id="37714-119">Zwalnianie pamięci skojarzonej z zarządzanym obiektem jest zawsze domeną [modułu wyrzucania elementów bezużytecznych](index.md).</span><span class="sxs-lookup"><span data-stu-id="37714-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="37714-120">Z tego powodu ma standardową implementację:</span><span class="sxs-lookup"><span data-stu-id="37714-120">Because of this, it has a standard implementation:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of managed resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> <span data-ttu-id="37714-121">Podstawowa różnica w asynchronicznym wzorcu usuwania w porównaniu do wzorca Dispose polega na tym, że wywołanie z <xref:System.IAsyncDisposable.DisposeAsync> `Dispose(bool)` metody przeciążenia jest podawane `false` jako argument.</span><span class="sxs-lookup"><span data-stu-id="37714-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="37714-122">Podczas implementowania <xref:System.IDisposable.Dispose?displayProperty=nameWithType> metody, jednak `true` zamiast tego jest przesyłane.</span><span class="sxs-lookup"><span data-stu-id="37714-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however; `true` is passed instead.</span></span> <span data-ttu-id="37714-123">Dzięki temu można zapewnić równoważność funkcjonalną z synchronicznym wzorcem usuwania, a dodatkowo zapewnić, że ścieżki kodu finalizatora nadal są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="37714-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="37714-124">Innymi słowy, `DisposeAsyncCore()` Metoda usunie zarządzane zasoby asynchronicznie, więc nie ma potrzeby ich synchronicznego usuwania.</span><span class="sxs-lookup"><span data-stu-id="37714-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="37714-125">W związku `Dispose(false)` z tym zamiast `Dispose(true)` .</span><span class="sxs-lookup"><span data-stu-id="37714-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="37714-126">Implementowanie wzorca usuwania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="37714-126">Implement the async dispose pattern</span></span>

<span data-ttu-id="37714-127">Wszystkie niezapieczętowane klasy należy traktować jako potencjalną klasę bazową, ponieważ mogą one być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="37714-127">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="37714-128">W przypadku zaimplementowania wzorca usuwania asynchronicznego dla dowolnej potencjalnej klasy podstawowej należy podać `protected virtual ValueTask DisposeAsyncCore()` metodę.</span><span class="sxs-lookup"><span data-stu-id="37714-128">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="37714-129">Oto Przykładowa implementacja asynchronicznego wzorca Dispose, który używa <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="37714-129">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="37714-130">W poprzednim przykładzie użyto <xref:System.Text.Json.Utf8JsonWriter> , aby uzyskać więcej informacji na temat `System.Text.Json` , zobacz [Migrowanie z Newtonsoft. JSON do System. Text. JSON](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="37714-130">The previous example used the <xref:System.Text.Json.Utf8JsonWriter>, for more information on `System.Text.Json`, see, [migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="37714-131">Korzystanie z asynchronicznej operacji jednorazowej</span><span class="sxs-lookup"><span data-stu-id="37714-131">Using async disposable</span></span>

<span data-ttu-id="37714-132">Aby prawidłowo korzystać z obiektu, który implementuje <xref:System.IAsyncDisposable> interfejs, należy użyć słów kluczowych [await](../../csharp/language-reference/operators/await.md)i [using](../../csharp/language-reference/keywords/using.md) .</span><span class="sxs-lookup"><span data-stu-id="37714-132">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md), and [using](../../csharp/language-reference/keywords/using.md) keywords together.</span></span> <span data-ttu-id="37714-133">Rozważmy poniższy przykład, w którym `ExampleAsyncDisposable` tworzona jest instancja klasy, a następnie zawinięte w `await using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="37714-133">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated, then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="37714-134">Użyj <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> metody rozszerzenia <xref:System.IAsyncDisposable> interfejsu, aby skonfigurować sposób przyprowadzenia zadania do jego oryginalnego kontekstu lub harmonogramu.</span><span class="sxs-lookup"><span data-stu-id="37714-134">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="37714-135">Aby uzyskać więcej informacji na temat `ConfigureAwait` , zobacz temat [ConfigureAwait — często zadawane pytania](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span><span class="sxs-lookup"><span data-stu-id="37714-135">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="37714-136">W sytuacjach, gdy użycie `ConfigureAwait` nie jest wymagane, `await using` instrukcja może być uproszczona w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="37714-136">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="37714-137">Ponadto można napisać, aby użyć niejawnego zakresu [deklaracji using](../../csharp/whats-new/csharp-8.md#using-declarations).</span><span class="sxs-lookup"><span data-stu-id="37714-137">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="37714-138">Stos użycia</span><span class="sxs-lookup"><span data-stu-id="37714-138">Stacked usings</span></span>

<span data-ttu-id="37714-139">W sytuacjach, gdy tworzysz i używasz wielu obiektów, które implementują <xref:System.IAsyncDisposable> , możliwe jest, aby `using` instrukcje stosujące w warunkach errant mogły uniemożliwić wywoływanie <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="37714-139">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="37714-140">Aby zapobiec potencjalnym problemom, należy unikać tworzenia stosów, a zamiast tego postępować zgodnie z poniższym przykładowym wzorcem:</span><span class="sxs-lookup"><span data-stu-id="37714-140">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="37714-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37714-141">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
