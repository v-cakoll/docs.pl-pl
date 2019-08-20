---
title: Korzystanie z indeksatorów C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 4411fe0ffe7dc136b4e74adeba3e5596af3aa1db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589426"
---
# <a name="using-indexers-c-programming-guide"></a>Korzystanie z indeksatorówC# (Przewodnik programowania)

Indeksatory to wygoda składni, która umożliwia tworzenie [klasy](../../language-reference/keywords/class.md), [struktury](../../language-reference/keywords/struct.md)lub [interfejsu](../../language-reference/keywords/interface.md) , które aplikacje klienckie mogą uzyskiwać dostęp do samego siebie jako tablicy. Indeksatory są najczęściej implementowane w typach, których głównym celem jest hermetyzacja wewnętrznej kolekcji lub tablicy. Załóżmy na przykład, że masz klasę `TempRecord` , która reprezentuje temperaturę w numerze Fahrenheita w ciągu 10 różnych razy w okresie 24 godzin. Klasa zawiera tablicę `temps` typu `float[]` do przechowywania wartości temperatury. Implementując indeksator w tej klasie, klienci mogą uzyskać dostęp do temperatury w `TempRecord` wystąpieniu jako `float temp = tr[4]` zamiast `float temp = tr.temps[4]`. Notacja indeksatora nie tylko upraszcza składnię aplikacji klienckich; sprawia również, że Klasa i jej cel są bardziej intuicyjne dla innych deweloperów do zrozumienia.  
  
Aby zadeklarować indeksator dla klasy lub struktury, użyj słowa kluczowego [this](../../language-reference/keywords/this.md) , jak pokazano w poniższym przykładzie:

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a>Uwagi

Typ indeksatora i typ jego parametrów muszą być co najmniej tak samo samo jak indeksator. Aby uzyskać więcej informacji na temat poziomów ułatwień dostępu, zobacz [Modyfikatory dostępu](../../language-reference/keywords/access-modifiers.md).  
  
 Aby uzyskać więcej informacji na temat używania indeksatorów z interfejsem, zobacz [indeksatory interfejsów](./indexers-in-interfaces.md).  
  
 Podpis indeksatora składa się z liczby i typów jego parametrów formalnych. Nie zawiera typu indeksatora ani nazw parametrów formalnych. Jeśli zadeklarujesz więcej niż jeden indeksator w tej samej klasie, muszą mieć różne podpisy.  
  
 Wartość indeksatora nie została sklasyfikowana jako zmienna; w związku z tym nie można przekazać wartości indeksatora jako parametru [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) .  
  
 Aby podać indeksator przy użyciu nazwy, która może być używana przez inne języki, <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>jak pokazano w poniższym przykładzie:  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

Ten indeksator będzie miał nazwę `TheItem`. Niedostarczenie atrybutu Name spowoduje wprowadzenie `Item` nazwy domyślnej.  
  
## <a name="example-1"></a>Przykład 1  
  
Poniższy przykład pokazuje, jak zadeklarować pole tablicy prywatnej, `temps`i indeksator. Indeksator umożliwia bezpośredni dostęp do wystąpienia `tempRecord[i]`. Alternatywą dla korzystania z indeksatora jest zadeklarowanie tablicy jako [publicznego](../../language-reference/keywords/public.md) elementu członkowskiego i dostęp do jej członków `tempRecord.temps[i]`, bezpośrednio.  
  
 Należy zauważyć, że gdy jest oceniany dostęp indeksatora, na przykład w `Console.Write` instrukcji metoda dostępu [Get](../../language-reference/keywords/get.md) jest wywoływana. W związku z tym `get` , jeśli żadna metoda dostępu nie istnieje, wystąpi błąd w czasie kompilacji.  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a>Indeksowanie przy użyciu innych wartości

C#nie ogranicza typu parametru indeksatora do liczby całkowitej. Na przykład przydatne może być użycie ciągu z indeksatorem. Takie indeksatory mogą być implementowane przez wyszukanie ciągu w kolekcji i zwrócenie odpowiedniej wartości. W miarę jak metody dostępu mogą być przeciążone, wersje typu String i Integer mogą współistnieć.  
  
## <a name="example-2"></a>Przykład 2  
  
Poniższy przykład deklaruje klasę, w której są przechowywane dni tygodnia. `get` Metoda dostępu przyjmuje ciąg, nazwę dnia i zwraca odpowiednią liczbę całkowitą. Na przykład "Niedziela" zwraca 0, "poniedziałek" zwraca 1 itd.  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie

 Istnieją dwa główne sposoby, w których można ulepszyć zabezpieczenia i niezawodność indeksatorów:  
  
- Należy pamiętać o uwzględnieniu niektórych typów strategii obsługi błędów, aby obsłużyć prawdopodobieństwo przekazania kodu klienta w nieprawidłowej wartości indeksu. W pierwszym przykładzie wcześniej w tym temacie Klasa TempRecord zawiera właściwość length, która umożliwia zweryfikowanie danych wejściowych przed przekazaniem ich do indeksatora. Można również umieścić kod obsługi błędu wewnątrz indeksatora. Upewnij się, że dla użytkowników występują wyjątki, które można zgłosić w metodzie dostępu indeksatora.  
  
- Ustaw dostępność metod dostępu [Get](../../language-reference/keywords/get.md) i [Set](../../language-reference/keywords/set.md) tak, aby były tak restrykcyjne, jak to uzasadnione. Jest to ważne w przypadku `set` metody dostępu w szczególności. Aby uzyskać więcej informacji, zobacz [ograniczanie dostępności metody](../classes-and-structs/restricting-accessor-accessibility.md)dostępu.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Indeksatory](./index.md)
- [Właściwości](../classes-and-structs/properties.md)
