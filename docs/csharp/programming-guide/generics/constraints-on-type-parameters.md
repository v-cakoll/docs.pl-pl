---
title: Ograniczenia dotyczące parametrów typu (Przewodnik programowania w języku C#)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25c4a1137df335080659bf878fce5e3a3270dfda
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Ograniczenia dotyczące parametrów typu (C# przewodnik programowania w języku)

Ograniczenia informuje kompilator o możliwościach, które musi mieć argument typu. Bez żadnych ograniczeń argumentu typu może być dowolnego typu. Kompilator może przyjmować tylko członkowie <xref:System.Object?displayPropety=nameWithType>, która jest ostatecznym klasę podstawową dla dowolnego typu .NET. Aby uzyskać więcej informacji, zobacz [Dlaczego warto korzystać z ograniczeniami](#why-use-constraints). Jeśli kod klienta próbuje utworzyć wystąpienia klasy przy użyciu typu, który nie jest dozwolona przez ograniczenie, wynikiem jest błąd kompilacji. Ograniczenia są określane przy użyciu `where` kontekstowe słowo kluczowe. W poniższej tabeli wymieniono siedmiu typy ograniczeń:

|Ograniczenia|Opis|
|----------------|-----------------|
|`where T: struct`|Argument typu musi być typem wartości. Wszystkie wartości typu z wyjątkiem <xref:System.Nullable> można określić. Aby uzyskać więcej informacji, zobacz [przy użyciu typów dopuszczających wartości zerowe](../nullable-types/using-nullable-types.md).|
|`where T : class`|Argument typu musi być typem referencyjnym. To ograniczenie ma zastosowanie również do klasy, interfejsu, delegata lub typ tablicy.|
|`where T : unmanaged`|Argument typu nie może być typem referencyjnym i nie może zawierać żadnych elementów członkowskich typu odwołania na dowolnym poziomie zagnieżdżenia.|
|`where T : new()`|Typ argumentu musi mieć publicznego konstruktora bez parametrów. Gdy jest używany z innymi ograniczeniami `new()` ograniczenie musi być określony jako ostatni.|
|`where T :` *\<Nazwa klasy podstawowej >*|Argument typu musi być lub pochodzić od określonej klasy podstawowej.|
|`where T :` *\<Nazwa interfejsu >*|Argument typu muszą być lub implementować określonego interfejsu. Można określić wiele ograniczeń interfejsu. Można też ogólnego ograniczający interfejsu.|
|`where T : U`|Argumentu typu dostarczonego T musi być lub pochodzić od argument dostarczony dla U.|

Niektóre ograniczenia wzajemnie się wykluczają. Wszystkie typy wartości musi mieć dostępny konstruktor bez parametrów. `struct` Oznacza ograniczenie `new()` ograniczenia i `new()` ograniczenia nie można połączyć z `struct` ograniczenia. `unmanaged` Oznacza ograniczenie `struct` ograniczenia. `unmanaged` Ograniczenia nie można łączyć z jedną `struct` lub `new()` ograniczenia.

## <a name="why-use-constraints"></a>Dlaczego warto korzystać z ograniczeniami

Ograniczający parametr typu, powoduje zwiększenie liczby operacji w dozwolonym i wywołania metody do obsługiwanych przez ograniczającego typu i wszystkie typy w jej hierarchii dziedziczenia. Podczas projektowania klas ogólnego lub metody, jeśli operacji na ogólnych elementów członkowskich poza przypisanie proste lub wywoływania żadnych metod, które nie są obsługiwane przez <xref:System.Object?displayProperty=nameWithType>, należy zastosować ograniczenia do parametru typu. Na przykład ograniczenie klasy podstawowej informuje kompilator, że tylko obiekty tego typu lub pochodzi z tego typu, będzie można używać jako argumentów typu. Kompilator ma gwarancji, umożliwiają metody tego typu można wywołać w klasie rodzajowej. Poniższy przykład kodu pokazuje funkcji, można dodać do `GenericList<T>` klasy (w [wprowadzenie do typów ogólnych](introduction-to-generics.md)), stosując ograniczenie klasy podstawowej.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Klasy ogólnej użyć umożliwia ograniczenie `Employee.Name` właściwości. Ograniczenie Określa, że wszystkie elementy typu `T` zapewniona jest albo `Employee` lub obiektu, który dziedziczy z `Employee`.

Wiele ograniczeń można zastosować do tego samego parametru typu, a same ograniczenia może mieć typów ogólnych w następujący sposób:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Podczas stosowania `where T : class` ograniczenia, należy unikać `==` i `!=` operatory w parametrze typu ponieważ tych operatorów sprawdza tożsamości odwołania, nie dla równości wartości. Dzieje się tak, nawet jeśli te operatory są przeciążone w typie, który jest używany jako argument. Poniższy kod ilustruje tę sytuację; nawet jeśli dane wyjściowe ma wartość false <xref:System.String> klasy przeciążenia `==` operatora.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilator tylko wie, że T jest typem referencyjnym w czasie kompilacji i musi być operatory domyślne, które są prawidłowe dla wszystkich typów odniesienia. Jeśli konieczne jest przetestowanie wartość pod kątem równości, zalecaną metodą jest również zastosować `where T : IEquatable<T>` lub `where T : IComparable<T>` ograniczenia i zaimplementuj interfejs w dowolnej klasy, która ma być użyty do utworzenia klasy ogólnej.

## <a name="constraining-multiple-parameters"></a>Ograniczający wiele parametrów

Wiele parametrów, a wiele ograniczeń na jeden parametr, można zastosować ograniczenia, jak pokazano w poniższym przykładzie:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Parametry typu niepowiązanego

 Wpisz parametry, które mają żadne ograniczenia, takie jak T w publicznej klasy `SampleClass<T>{}`, są nazywane parametrów niepowiązanego typu. Parametry typu niepowiązanego mają następujące reguły:

- `!=` i `==` nie można używać operatorów, ponieważ nie ma żadnej gwarancji, że argument typu konkretnego będzie obsługiwać tych operatorów.
- Może być przekonwertowany do i z `System.Object` lub jawnie przekonwertowane do dowolnego typu interfejsu.
- Możesz je, aby porównać [null](../../language-reference/keywords/null.md). Jeśli jest porównywany niepowiązany parametr `null`, porównanie zawsze zwróci wartość false, jeśli argument Typ jest typem wartości.

## <a name="type-parameters-as-constraints"></a>Parametry typu jako ograniczenia

Użyj parametru typu ogólnego jako ograniczenie jest przydatne w przypadku funkcji członkowskiej z własną parametr typu ma ograniczenie parametru typu parametru typu zawierającego, jak pokazano w poniższym przykładzie:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

W poprzednim przykładzie `T` ograniczenie typu w kontekście `Add` — metoda i parametr niepowiązanego typu w kontekście `List` klasy.

Parametry typu mogą służyć jako ograniczeń w definicji klasy ogólnej. Parametr typu musi być zadeklarowana w nawiasy razem z innymi parametrami typu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Przydatność parametrów typu jako ograniczenia z klas rodzajowych są ograniczone, ponieważ kompilator można założyć, nie ma parametru typu z tą różnicą, że pochodzi od `System.Object`. Parametry typu jako ograniczenia dotyczące klas ogólnych w scenariuszach, w których chcesz wymusić relację dziedziczenia między dwoma parametrami typu.

## <a name="unmanaged-constraint"></a>Ograniczenie niezarządzane

Począwszy od 7.3 C#, można użyć `unmanaged` ograniczenie, aby określić, że parametr typu musi być **niezarządzany typ**. **Niezarządzany typ** jest typ, który nie jest typem referencyjnym i nie zawiera odwołanie do pola typu na dowolnym poziomie zagnieżdżenia. `unmanaged` Ograniczenia umożliwia pisanie procedury wielokrotnego użytku do pracy z typów, które można manipulować jako bloki pamięci, jak pokazano w poniższym przykładzie:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Powyższa metoda musi zostać skompilowany w `unsafe` kontekstu, ponieważ używa `sizeof` operator dla typu nie jest znany jako typ wbudowany. Bez `unmanaged` ograniczenie `sizeof` operator jest niedostępny.

## <a name="delegate-constraints"></a>Ograniczenia obiektu delegowanego

Można również począwszy od 7.3 C#, <xref:System.Delegate?displayProperty=nameWithType> lub <xref:System.MulticastDelegate?displayProperty=nameWithType> jako ograniczenia klasy podstawowej. Środowisko CLR zawsze dozwolone to ograniczenie, ale w języku C# niedopuszczalne go. `System.Delegate` Ograniczenia umożliwia pisanie kodu, który współpracuje z delegatów w bezpieczny sposób. Poniższy kod definiuje metodę rozszerzenia, łączącą dwa obiekty delegowane warunkiem, że są tego samego typu:

[!code-csharp[using the delegate constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Metoda powyżej umożliwia łączenie obiektów delegowanych, które są tego samego typu:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Jeśli usuń znaczniki komentarza ostatni wiersz, nie będzie kompilacji. Zarówno `first` i `test` są typy delegatów, ale są one delegata różnych typów.

## <a name="enum-constraints"></a>Ograniczenia wyliczenia

Począwszy od 7.3 C#, można również określić <xref:System.Enum?displayProperty=nameWithType> typu jako ograniczenia klasy podstawowej. Środowisko CLR zawsze dozwolone to ograniczenie, ale w języku C# niedopuszczalne go. Typy ogólne przy użyciu `System.Enum` zapewnić bezpieczne programowania do pamięci podręcznej wyniki z przy użyciu metod statycznych w `System.Enum`. Poniższy przykład znajduje wszystkie prawidłowe wartości dla typu wyliczeniowego, a następnie tworzy słownik mapujący te wartości do reprezentacji ciągu.

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Metody używane, należy użyć odbicia, który ma wpływ na wydajność. Możesz wywołać tę metodę, aby utworzyć kolekcję w pamięci podręcznej i ponownie użyte zamiast powtarzające się wywołania, które wymagają odbicia.

Można użyć tego jak pokazano w poniższym przykładzie do tworzenia wyliczenia i kompilowania słownik nazw i wartości:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Zobacz także

 <xref:System.Collections.Generic> [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Klasy ogólne](../../../csharp/programming-guide/generics/generic-classes.md)  
 [new, ograniczenie](../../../csharp/language-reference/keywords/new-constraint.md)  
