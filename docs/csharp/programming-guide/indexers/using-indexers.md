---
title: Używanie indeksatorów (Przewodnik programowania w języku C#)
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 0bb7b848f5484b78e8dae0c40320e7945b78eea0
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873462"
---
# <a name="using-indexers-c-programming-guide"></a>Używanie indeksatorów (C# Programming Guide)

Indeksatory są wygody składni, które umożliwiają tworzenie [klasy](../../../csharp/language-reference/keywords/class.md), [struktury](../../../csharp/language-reference/keywords/struct.md), lub [interfejsu](../../../csharp/language-reference/keywords/interface.md) że aplikacje klienckie mogą uzyskać dostęp, podobnie jak tablica. Indeksatory najczęściej są implementowane w typach, której głównym celem jest hermetyzacji wewnętrznej kolekcji lub tablicy. Załóżmy na przykład, posiadasz klasę `TempRecord` reprezentujący temperaturę w Farenheit zarejestrowanej w 10 różnych razy w okresie 24-godzinnym. Klasa zawiera tablicę `temps` typu `float[]` do przechowywania wartości temperatury. Wdrażając indeksatora w tej klasie, klienci mogą uzyskiwać dostęp temperatur w `TempRecord` wystąpienia jako `float temp = tr[4]` zamiast jako `float temp = tr.temps[4]`. Notacja indeksator nie tylko upraszcza składnię dla aplikacji klienckich; zapewnia także klasa i jej przeznaczenie bardziej intuicyjne innym deweloperom zrozumieć.  
  
Aby zadeklarować indeksatora w klasie lub strukturze, użyj [to](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe, co ilustruje poniższy przykład:

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a>Uwagi

Typ indeksatora i typ parametrów musi być co najmniej tak samo dostępna jak indeksatora, sam. Aby uzyskać więcej informacji na temat poziomów ułatwień dostępu, zobacz [modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Aby uzyskać więcej informacji o tym, jak korzystać z indeksatorów za pomocą interfejsu, zobacz [indeksatory interfejsu](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).  
  
 Podpis indeksatora składa się z liczbę i typy parametrów formalnych. Nie zawiera typ indeksatora lub nazwy parametrów formalnych. Jeśli zadeklarujesz więcej niż jeden indeksatora w tej samej klasy muszą mieć różnych podpisów.  
  
 Wartość będącą liczbą indeksator nie jest sklasyfikowany jako zmienna; w związku z tym, nie można przekazać wartość indeksatora jako [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru.  
  
 Aby zapewnić indeksatora o nazwie używanego w innych językach, należy użyć <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie:  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

Ten indeksator będzie mieć taką nazwę `TheItem`. Nie udostępniają atrybut name czyniłyby `Item` nazwę domyślną.  
  
## <a name="example-1"></a>Przykład 1  
  
Poniższy przykład pokazuje sposób deklarowania pola tablicy prywatnej `temps`i indeksatora. Indeksator umożliwia bezpośredni dostęp do wystąpienia `tempRecord[i]`. Zamiast za pomocą indeksatora jest, aby zadeklarować tablicę jako [publicznych](../../../csharp/language-reference/keywords/public.md) elementu członkowskiego i uzyskiwać dostęp do swoich elementów członkowskich, `tempRecord.temps[i]`bezpośrednio.  
  
 Należy zauważyć, że dostęp indeksatora jest sprawdzane, na przykład w `Console.Write` instrukcji [uzyskać](../../../csharp/language-reference/keywords/get.md) zostanie wywołana metoda dostępu. W związku z tym jeśli nie `get` istnieje dostępu, wystąpi błąd kompilacji.  
  
[!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a>Indeksowanie przy użyciu innych wartości

C# nie są ograniczone typu indeksu do liczby całkowitej. Na przykład może być przydatne do ciągu za pomocą indeksatora. Takie indeksator może być realizowane przez wyszukiwanie ciągu w kolekcji i zwraca odpowiednią wartość. Jak mogą być przeciążone metody dostępu, string i integer wersje mogą współistnieć.  
  
## <a name="example-2"></a>Przykład 2  
  
Poniższy przykład deklaruje klasę, która przechowuje dni tygodnia. A `get` akcesor przyjmuje ciąg nazwy dnia i zwraca odpowiedniej liczby całkowitej. Na przykład "Niedziela" zwraca wartość 0, zwraca "Poniedziałek", 1 i tak dalej.  
  
[!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie

 Istnieją dwa główne sposoby, w których można zwiększyć bezpieczeństwo i niezawodność indeksatory:  
  
- Pamiętaj wprowadzić pewien rodzaj strategii obsługi błędów do obsługi prawdopodobieństwo kod klienta, przekazując wartość nieprawidłowy indeks. W pierwszym przykładzie we wcześniejszej części tego tematu klasa TempRecord udostępnia właściwości długości, która umożliwia kodu klienta, sprawdź dane wejściowe przed przekazaniem go do indeksatora. Można również wprowadzić kod wewnątrz samego indeksatora obsługi błędów. Pamiętaj dokumentów dla użytkowników ewentualne wyjątki, które generują wewnątrz metody dostępu indeksatora.  
  
- Zestawu dostępności [uzyskać](../../../csharp/language-reference/keywords/get.md) i [ustaw](../../../csharp/language-reference/keywords/set.md) metod dostępu do jako restrykcyjne uprawnienia, ponieważ jest uzasadnione. Jest to ważne w przypadku `set` dostępu, w szczególności. Aby uzyskać więcej informacji, zobacz [Ograniczanie dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
