---
title: Korzystanie z indeksatorów — Przewodnik programowania w języku C#
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: e742e4dd5ea92ec3baf37c915e024e713022b7b6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416242"
---
# <a name="using-indexers-c-programming-guide"></a>Używanie indeksatorów (Przewodnik programowania w języku C#)

Indeksatory to wygoda składni, która umożliwia tworzenie [klasy](../../language-reference/keywords/class.md), [struktury](../../language-reference/builtin-types/struct.md)lub [interfejsu](../../language-reference/keywords/interface.md) , do którego aplikacje klienckie mogą uzyskiwać dostęp jako tablica. Kompilator wygeneruje `Item` Właściwość (lub właściwość o nazwie Alternatywnie <xref:System.Runtime.CompilerServices.IndexerNameAttribute> , jeśli jest obecna) i odpowiednie metody dostępu. Indeksatory są najczęściej implementowane w typach, których głównym celem jest hermetyzacja wewnętrznej kolekcji lub tablicy. Załóżmy na przykład, że masz klasę `TempRecord` , która reprezentuje temperaturę w numerze Fahrenheita w ciągu 10 różnych razy w okresie 24 godzin. Klasa zawiera `temps` tablicę typu `float[]` do przechowywania wartości temperatury. Implementując indeksator w tej klasie, klienci mogą uzyskać dostęp do temperatury w `TempRecord` wystąpieniu jako `float temp = tempRecord[4]` zamiast `float temp = tempRecord.temps[4]` . Notacja indeksatora nie tylko upraszcza składnię aplikacji klienckich; sprawia również, że Klasa i jej cel są bardziej intuicyjne dla innych deweloperów do zrozumienia.

Aby zadeklarować indeksator dla klasy lub struktury, użyj słowa kluczowego [this](../../language-reference/keywords/this.md) , jak pokazano w poniższym przykładzie:

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> Deklarowanie indeksatora spowoduje automatyczne wygenerowanie właściwości o nazwie `Item` w obiekcie. `Item`Właściwość nie jest bezpośrednio dostępna z [wyrażenia dostępu do elementu członkowskiego](../../language-reference/operators/member-access-operators.md#member-access-expression-)wystąpienia. Ponadto, jeśli dodasz własną `Item` Właściwość do obiektu za pomocą indeksatora, otrzymasz [błąd kompilatora CS0102](../../misc/cs0102.md). Aby uniknąć tego błędu, użyj <xref:System.Runtime.CompilerServices.IndexerNameAttribute> nazwy indeksatora, jak pokazano poniżej.

## <a name="remarks"></a>Uwagi

Typ indeksatora i typ jego parametrów muszą być co najmniej tak samo samo jak indeksator. Aby uzyskać więcej informacji na temat poziomów ułatwień dostępu, zobacz [Modyfikatory dostępu](../../language-reference/keywords/access-modifiers.md).

Aby uzyskać więcej informacji na temat używania indeksatorów z interfejsem, zobacz [indeksatory interfejsów](./indexers-in-interfaces.md).

Podpis indeksatora składa się z liczby i typów jego parametrów formalnych. Nie zawiera typu indeksatora ani nazw parametrów formalnych. Jeśli zadeklarujesz więcej niż jeden indeksator w tej samej klasie, muszą mieć różne podpisy.

Wartość indeksatora nie została sklasyfikowana jako zmienna; w związku z tym nie można przekazać wartości indeksatora jako parametru [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) .

Aby podać indeksator przy użyciu nazwy, która może być używana przez inne języki, <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType> jak pokazano w poniższym przykładzie:

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

Ten indeksator będzie miał nazwę `TheItem` , ponieważ jest zastępowany przez atrybut nazwy indeksatora. Domyślnie nazwa indeksatora to `Item` .

## <a name="example-1"></a>Przykład 1

Poniższy przykład pokazuje, jak zadeklarować pole tablicy prywatnej, `temps` i indeksator. Indeksator umożliwia bezpośredni dostęp do wystąpienia `tempRecord[i]` . Alternatywą dla korzystania z indeksatora jest zadeklarowanie tablicy jako [publicznego](../../language-reference/keywords/public.md) elementu członkowskiego i dostęp do jej członków, `tempRecord.temps[i]` bezpośrednio.

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

Należy zauważyć, że gdy jest oceniany dostęp indeksatora, na przykład w `Console.Write` instrukcji metoda dostępu [Get](../../language-reference/keywords/get.md) jest wywoływana. W związku z tym, jeśli żadna `get` metoda dostępu nie istnieje, wystąpi błąd w czasie kompilacji.

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a>Indeksowanie przy użyciu innych wartości

Język C# nie ogranicza typu parametru indeksatora do liczby całkowitej. Na przykład przydatne może być użycie ciągu z indeksatorem. Takie indeksatory mogą być implementowane przez wyszukanie ciągu w kolekcji i zwrócenie odpowiedniej wartości. Metody dostępu mogą być przeciążone, a wersje typu String i Integer mogą współistnieć.

## <a name="example-2"></a>Przykład 2

Poniższy przykład deklaruje klasę, w której są przechowywane dni tygodnia. `get`Metoda dostępu przyjmuje ciąg, nazwę dnia i zwraca odpowiednią liczbę całkowitą. Na przykład "Niedziela" zwraca 0, "poniedziałek" zwraca 1 itd.

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a>Przykład zużywający 2

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a>Przykład 3

Poniższy przykład deklaruje klasę, która przechowuje dni tygodnia przy użyciu <xref:System.DayOfWeek?displayProperty=fullName> wyliczenia. `get`Metoda dostępu przyjmuje `DayOfWeek` , wartość dnia i zwraca odpowiednią liczbę całkowitą. Na przykład `DayOfWeek.Sunday` zwraca wartość 0, `DayOfWeek.Monday` zwraca wartość 1 i tak dalej.

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a>Przykład zużywający 3

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a>Niezawodne programowanie

Istnieją dwa główne sposoby, w których można ulepszyć zabezpieczenia i niezawodność indeksatorów:

- Należy pamiętać o uwzględnieniu niektórych typów strategii obsługi błędów, aby obsłużyć prawdopodobieństwo przekazania kodu klienta w nieprawidłowej wartości indeksu. W pierwszym przykładzie wcześniej w tym temacie Klasa TempRecord zawiera właściwość length, która umożliwia zweryfikowanie danych wejściowych przed przekazaniem ich do indeksatora. Można również umieścić kod obsługi błędu wewnątrz indeksatora. Upewnij się, że dla użytkowników występują wyjątki, które można zgłosić w metodzie dostępu indeksatora.

- Ustaw dostępność metod dostępu [Get](../../language-reference/keywords/get.md) i [Set](../../language-reference/keywords/set.md) tak, aby były tak restrykcyjne, jak to uzasadnione. Jest to ważne w przypadku `set` metody dostępu w szczególności. Aby uzyskać więcej informacji, zobacz [ograniczanie dostępności metody](../classes-and-structs/restricting-accessor-accessibility.md)dostępu.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Indeksatory](./index.md)
- [Właściwości](../classes-and-structs/properties.md)
