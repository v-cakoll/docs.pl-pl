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
# <a name="implement-a-disposeasync-method"></a>Implementowanie metody DisposeAsync

<xref:System.IAsyncDisposable?displayProperty=nameWithType>Interfejs został wprowadzony jako część języka C# 8,0. Metodę należy zaimplementować <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> , gdy trzeba przeprowadzić Oczyszczanie zasobów, tak jak podczas [implementowania metody Dispose](implementing-dispose.md). Jedną z najważniejszych różnic jest jednak to, że ta implementacja umożliwia asynchroniczne czyszczenie operacji. <xref:System.IAsyncDisposable.DisposeAsync>Zwraca wartość <xref:System.Threading.Tasks.ValueTask> reprezentującą asynchroniczną operację Dispose.

Typowo, że podczas implementowania <xref:System.IAsyncDisposable> interfejsu, klasy również implementują <xref:System.IDisposable> interfejs. Dobry wzorzec implementacji <xref:System.IAsyncDisposable> interfejsu jest przygotowany do synchronicznej lub asynchronicznej operacji Dispose. Wszystkie wskazówki dotyczące implementacji wzorca Dispose dotyczą implementacji asynchronicznej. W tym artykule założono, że wiesz już, jak [zaimplementować metodę Dispose](implementing-dispose.md).

## <a name="disposeasync-and-disposeasynccore"></a>DisposeAsync () i DisposeAsyncCore ()

<xref:System.IAsyncDisposable>Interfejs deklaruje pojedynczą metodę bez parametrów, <xref:System.IAsyncDisposable.DisposeAsync> . Każda Klasa Niezapieczętowana powinna mieć dodatkową `DisposeAsyncCore()` metodę, która również zwraca wartość <xref:System.Threading.Tasks.ValueTask> .

- `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> Implementacja, która nie ma parametrów.
- `protected virtual ValueTask DisposeAsyncCore()`Metoda, której sygnatura:

```csharp
protected virtual ValueTask DisposeAsyncCore()
{
}
```

`DisposeAsyncCore()`Metoda polega na `virtual` tym, że klasy pochodne mogą definiować dodatkowe czyszczenie w ich zastąpień.

### <a name="the-disposeasync-method"></a>DisposeAsync () — Metoda

`public` `DisposeAsync()` Metoda bez parametrów jest wywoływana niejawnie w `await using` instrukcji i jej celem jest zwolnienie niezarządzanych zasobów, wykonanie ogólnego oczyszczenia i wskazanie, że finalizator, jeśli taki istnieje, nie musi. Zwalnianie pamięci skojarzonej z zarządzanym obiektem jest zawsze domeną [modułu wyrzucania elementów bezużytecznych](index.md). Z tego powodu ma standardową implementację:

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
> Podstawowa różnica w asynchronicznym wzorcu usuwania w porównaniu do wzorca Dispose polega na tym, że wywołanie z <xref:System.IAsyncDisposable.DisposeAsync> `Dispose(bool)` metody przeciążenia jest podawane `false` jako argument. Podczas implementowania <xref:System.IDisposable.Dispose?displayProperty=nameWithType> metody, jednak `true` zamiast tego jest przesyłane. Dzięki temu można zapewnić równoważność funkcjonalną z synchronicznym wzorcem usuwania, a dodatkowo zapewnić, że ścieżki kodu finalizatora nadal są wywoływane. Innymi słowy, `DisposeAsyncCore()` Metoda usunie zarządzane zasoby asynchronicznie, więc nie ma potrzeby ich synchronicznego usuwania. W związku `Dispose(false)` z tym zamiast `Dispose(true)` .

## <a name="implement-the-async-dispose-pattern"></a>Implementowanie wzorca usuwania asynchronicznego

Wszystkie niezapieczętowane klasy należy traktować jako potencjalną klasę bazową, ponieważ mogą one być dziedziczone. W przypadku zaimplementowania wzorca usuwania asynchronicznego dla dowolnej potencjalnej klasy podstawowej należy podać `protected virtual ValueTask DisposeAsyncCore()` metodę. Oto Przykładowa implementacja asynchronicznego wzorca Dispose, który używa <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

W poprzednim przykładzie użyto <xref:System.Text.Json.Utf8JsonWriter> , aby uzyskać więcej informacji na temat `System.Text.Json` , zobacz [Migrowanie z Newtonsoft. JSON do System. Text. JSON](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).

## <a name="using-async-disposable"></a>Korzystanie z asynchronicznej operacji jednorazowej

Aby prawidłowo korzystać z obiektu, który implementuje <xref:System.IAsyncDisposable> interfejs, należy użyć słów kluczowych [await](../../csharp/language-reference/operators/await.md)i [using](../../csharp/language-reference/keywords/using.md) . Rozważmy poniższy przykład, w którym `ExampleAsyncDisposable` tworzona jest instancja klasy, a następnie zawinięte w `await using` instrukcji.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> Użyj <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> metody rozszerzenia <xref:System.IAsyncDisposable> interfejsu, aby skonfigurować sposób przyprowadzenia zadania do jego oryginalnego kontekstu lub harmonogramu. Aby uzyskać więcej informacji na temat `ConfigureAwait` , zobacz temat [ConfigureAwait — często zadawane pytania](https://devblogs.microsoft.com/dotnet/configureawait-faq/).

W sytuacjach, gdy użycie `ConfigureAwait` nie jest wymagane, `await using` instrukcja może być uproszczona w następujący sposób:

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

Ponadto można napisać, aby użyć niejawnego zakresu [deklaracji using](../../csharp/whats-new/csharp-8.md#using-declarations).

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a>Stos użycia

W sytuacjach, gdy tworzysz i używasz wielu obiektów, które implementują <xref:System.IAsyncDisposable> , możliwe jest, aby `using` instrukcje stosujące w warunkach errant mogły uniemożliwić wywoływanie <xref:System.IAsyncDisposable.DisposeAsync> . Aby zapobiec potencjalnym problemom, należy unikać tworzenia stosów, a zamiast tego postępować zgodnie z poniższym przykładowym wzorcem:

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a>Zobacz też

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
