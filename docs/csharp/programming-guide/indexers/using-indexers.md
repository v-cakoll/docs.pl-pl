---
title: Korzystanie z indeksatorów — przewodnik programowania C#
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628166"
---
# <a name="using-indexers-c-programming-guide"></a>Korzystanie z indeksatorów (Przewodnik programowania C#)

Indeksatory to wygoda składni, która umożliwia tworzenie [klasy,](../../language-reference/keywords/class.md) [struktury](../../language-reference/builtin-types/struct.md)lub [interfejsu,](../../language-reference/keywords/interface.md) do którego aplikacje klienckie mają dostęp tak samo jak tablica. Indeksatory są najczęściej implementowane w typach, których głównym celem jest hermetyzowanie wewnętrznej kolekcji lub tablicy. Załóżmy na przykład, `TempRecord` że masz klasę, która reprezentuje temperaturę w Fahrenheita zarejestrowaną w 10 różnych momentach w okresie 24 godzin. Klasa zawiera tablicę `temps` `float[]` typu do przechowywania wartości temperatury. Implementując indeksator w tej klasie, klienci `TempRecord` mogą `float temp = tr[4]` uzyskać dostęp `float temp = tr.temps[4]`do temperatury w wystąpieniu, jak zamiast jako . Notacja indeksatora nie tylko upraszcza składnię aplikacji klienckich; to również sprawia, że klasa i jej cel bardziej intuicyjne dla innych programistów, aby zrozumieć.  
  
Aby zadeklarować indeksatora w klasie lub strukturze, użyj [tego](../../language-reference/keywords/this.md) słowa kluczowego, jak pokazano w poniższym przykładzie:

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a>Uwagi

Typ indeksatora i typ jego parametrów musi być co najmniej tak samo dostępne jak indeksator sam. Aby uzyskać więcej informacji na temat poziomów ułatwień dostępu, zobacz [Modyfikatory programu Access](../../language-reference/keywords/access-modifiers.md).  
  
 Aby uzyskać więcej informacji na temat używania indeksatorów z interfejsem, zobacz [Indeksatory interfejsu](./indexers-in-interfaces.md).  
  
 Podpis indeksatora składa się z liczby i typów jego parametrów formalnych. Nie zawiera typu indeksatora lub nazwy parametrów formalnych. Jeśli deklarujesz więcej niż jeden indeksator w tej samej klasie, muszą mieć różne podpisy.  
  
 Wartość indeksatora nie jest klasyfikowana jako zmienna; w związku z tym nie można przekazać wartość indeksatora jako [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) parametru.  
  
 Aby zapewnić indeksatorowi nazwę, z którego <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>mogą używać inne języki, użyj , jak pokazano w poniższym przykładzie:  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

Ten indeksator będzie `TheItem`miał nazwę . Niepodanie atrybutu name `Item` spowoduje ustawienie domyślnej nazwy.  
  
## <a name="example-1"></a>Przykład 1  
  
W poniższym przykładzie pokazano, `temps`jak zadeklarować pole tablicy prywatnej i indeksatora. Indeksator umożliwia bezpośredni dostęp `tempRecord[i]`do wystąpienia . Alternatywą dla indeksatora jest zadeklarowanie [public](../../language-reference/keywords/public.md) tablicy jako publicznego `tempRecord.temps[i]`elementu członkowskiego i dostęp do jej członków, bezpośrednio.  
  
 Należy zauważyć, że gdy dostęp indeksatora jest `Console.Write` oceniana, na przykład w instrukcji, [get](../../language-reference/keywords/get.md) akcesor jest wywoływana. W związku `get` z tym jeśli nie ma akcesor istnieje, występuje błąd w czasie kompilacji.  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a>Indeksowanie przy użyciu innych wartości

C# nie ogranicza typ parametru indeksatora do liczby całkowitej. Na przykład może być przydatne użycie ciągu z indeksatorem. Taki indeksator może być implementowany przez wyszukanie ciągu w kolekcji i zwrócenie odpowiedniej wartości. Jako akcesory mogą być przeciążone, ciąg i całkowita wersja może współistnieć.  
  
## <a name="example-2"></a>Przykład 2  
  
W poniższym przykładzie deklaruje klasę, która przechowuje dni tygodnia. Akcesor `get` przyjmuje ciąg, nazwę dnia i zwraca odpowiednią liczbę całkowitą. Na przykład "Niedziela" zwraca 0, "Poniedziałek" zwraca 1 i tak dalej.  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a>Solidne programowanie

 Istnieją dwa główne sposoby poprawy bezpieczeństwa i niezawodności indeksatorów:  
  
- Pamiętaj, aby uwzględnić jakiś typ strategii obsługi błędów, aby obsłużyć prawdopodobieństwo przekazywania kodu klienta w nieprawidłowej wartości indeksu. W pierwszym przykładzie wcześniej w tym temacie TempRecord klasa zawiera Length właściwość, która umożliwia kod klienta, aby zweryfikować dane wejściowe przed przekazaniem go do indeksatora. Można również umieścić kod obsługi błędów wewnątrz indeksatora się. Pamiętaj, aby udokumentować dla użytkowników wszelkie wyjątki, które można zgłosić wewnątrz akcesora indeksatora.  
  
- Ustaw dostępność [get](../../language-reference/keywords/get.md) i [set](../../language-reference/keywords/set.md) akcesorów być tak restrykcyjne, jak jest to uzasadnione. Jest to ważne `set` w szczególności dla akcesora. Aby uzyskać więcej informacji, zobacz [Ograniczanie ułatwień dostępu .](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Indexers](./index.md) (Indeksatory)
- [Właściwości](../classes-and-structs/properties.md)
