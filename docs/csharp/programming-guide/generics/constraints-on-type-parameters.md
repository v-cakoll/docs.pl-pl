---
title: Ograniczenia dotyczące parametrów typu (Przewodnik programowania w języku C#)
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: df5a509296f3fb9e8e77a273a0636c74a6f86da3
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711288"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Ograniczenia dotyczące parametrów typu (C# Programming Guide)

Ograniczenia informuje kompilator o możliwościach, którego argument typu musi mieć. Bez żadnych ograniczeń argument typu może być dowolnego typu. Kompilator, można założyć tylko członkowie <xref:System.Object?displayPropety=nameWithType>, czyli ultimate klasę bazową dla wszystkich typów .NET. Aby uzyskać więcej informacji, zobacz [Dlaczego warto korzystać z ograniczeniami](#why-use-constraints). Jeśli kod klienta próbuje utworzyć wystąpienie klasy przy użyciu typu, który nie jest dozwolona przez ograniczenie, wynikiem jest błąd w czasie kompilacji. Ograniczenia są określane za pomocą `where` kontekstowego słowa kluczowego. W poniższej tabeli wymieniono siedem typy ograniczeń:

|Ograniczenia|Opis|
|----------------|-----------------|
|`where T : struct`|Argument typu musi być typem wartości. Wszystkie wartości typu z wyjątkiem <xref:System.Nullable%601> można określić. Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe zobacz [typów dopuszczających wartości zerowe](../nullable-types/index.md).|
|`where T : class`|Argument typu musi być typem referencyjnym. To ograniczenie ma zastosowanie także do klasy, interfejsu, delegata lub typu tablicowego.|
|`where T : unmanaged`|Argument typu nie może być typem referencyjnym i nie może zawierać żadnych składowych typu odwołania na każdym poziomie zagnieżdżania.|
|`where T : new()`|Typ argumentu musi mieć publicznego konstruktora bez parametrów. Gdy jest używany z innymi ograniczeniami `new()` ograniczenie musi być określony jako ostatni.|
|`where T :` *\<Klasa bazowa nazwa >*|Argument typu musi być lub pochodzić od określonej klasy podstawowej.|
|`where T :` *\<Nazwa interfejsu >*|Argument typu muszą być lub implementować określonego interfejsu. Można określić wiele ograniczeń interfejsu. Można też ogólnego ograniczający interfejsu.|
|`where T : U`|Argumentu typu dostarczonego T musi być lub pochodzić od argument dostarczony dla U.|

Niektóre ograniczenia wzajemnie się wykluczają. Wszystkie typy wartości, musi mieć konstruktora bez parametrów dostępny. `struct` Oznacza ograniczenie `new()` ograniczenia i `new()` ograniczenia nie można łączyć z `struct` ograniczenia. `unmanaged` Oznacza ograniczenie `struct` ograniczenia. `unmanaged` Ograniczenia nie można łączyć z jedną `struct` lub `new()` ograniczenia.

## <a name="why-use-constraints"></a>Dlaczego warto korzystać z ograniczeniami

Ograniczając parametr typu, zwiększenie liczby dopuszczalnych operacji i wywołania metody do obsługiwanych przez ograniczający typu oraz wszystkich typów w hierarchii dziedziczenia. Podczas projektowania klas ogólnych lub metody, jeśli wykonywanie żadnych operacji na ogólnych składowych poza przypisanie proste lub wszystkie metody, które nie są obsługiwane przez wywołanie <xref:System.Object?displayProperty=nameWithType>, należy zastosować ograniczenia do parametru typu. Na przykład ograniczenia klasy bazowej informuje kompilator, że tylko obiekty tego typu lub pochodzić z tego typu będzie służyć jako argumentów typu. Gdy kompilator ma gwarancji, umożliwia metody tego typu można wywołać w klasy ogólnej. Poniższy przykład kodu pokazuje funkcje, możesz dodać do `GenericList<T>` klasy (w [wprowadzenie do typów ogólnych](introduction-to-generics.md)), stosując ograniczenia klasy bazowej.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Ograniczenie umożliwia klasy generycznej użyć `Employee.Name` właściwości. Ograniczenie Określa, że wszystkie elementy typu `T` zapewniona jest albo `Employee` obiekt lub obiekt, który dziedziczy z `Employee`.

Wiele ograniczeń mogą być stosowane do tego samego parametru typu, a same ograniczenia mogą być typów ogólnych w następujący sposób:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Podczas stosowania `where T : class` ograniczenia, należy unikać `==` i `!=` operatory dla parametru typu, ponieważ te operatory przetestuje tożsamości odwołanie, nie na równoważność wartości. Dzieje się tak nawet wtedy, gdy te operatory są przeciążone w typie, który jest używany jako argument. Poniższy kod ilustruje ten punkt; nawet jeśli dane wyjściowe są fałszywe <xref:System.String> klasy przeciążenia `==` operatora.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilator wie jedynie, że T jest typem odwołania w czasie kompilacji i musi być domyślne operatory, które są prawidłowe dla wszystkich typów odniesienia. Jeśli należy przetestować na równoważność wartości, zalecaną metodą jest również dotyczyć `where T : IEquatable<T>` lub `where T : IComparable<T>` ograniczenia i zaimplementuj interfejs w każdej klasy, która będzie służyć do konstruowania klasy ogólnej.

## <a name="constraining-multiple-parameters"></a>Ograniczając wiele parametrów

Ograniczenia można zastosować do wielu parametrów, a wiele ograniczeń na jeden parametr, jak pokazano w poniższym przykładzie:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Parametry typu niepowiązanego

 Parametry, które mają nie ograniczeń, takich jak T w klasę publiczną typu `SampleClass<T>{}`, są nazywane parametrami typu niepowiązanego. Parametry typu niepowiązanego mają następujące reguły:

- `!=` i `==` nie można używać operatorów, ponieważ nie ma żadnej gwarancji, że argument typu konkretnego obejmie te operatory.
- Mogą być konwertowane do i z `System.Object` lub jawnie konwertowane na dowolny typ interfejsu.
- Możesz porównać ich [null](../../language-reference/keywords/null.md). Jeśli podano parametr niepowiązanego jest porównywany z `null`, porównanie zawsze zwróci wartość false, jeśli argument typu jest typem wartości.

## <a name="type-parameters-as-constraints"></a>Parametry typu jako ograniczenia

Użyj parametru typu ogólnego jako ograniczenie jest przydatne, gdy funkcja elementu członkowskiego z parametrem typu ma ograniczenie tego parametru, aby parametr typu zawierającego, jak pokazano w poniższym przykładzie:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

W poprzednim przykładzie `T` ograniczenie typu w kontekście `Add` metody i parametrów niepowiązanego typu w kontekście `List` klasy.

Parametrów typu można również jako warunki ograniczające w definicji klasy ogólnej. Parametr typu musi być zadeklarowany w nawiasach kątowych wraz z innymi parametrami typu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Użyteczność parametrów typu jako warunki ograniczające z klasami ogólnego jest ograniczona, ponieważ kompilator może przyjąć, nie ma parametru typu z tą różnicą, że pochodzi od klasy `System.Object`. Używać parametrów typu jako ograniczenia dotyczące klas ogólnych w scenariuszach, w których chcesz wymusić relacje dziedziczenia między dwa parametry typu.

## <a name="unmanaged-constraint"></a>Ograniczenie Unmanaged

Począwszy od języka C# 7.3, można użyć `unmanaged` ograniczenie, aby określić, że parametr typu musi być **niezarządzany typ**. **Niezarządzany typ** to typ, który nie jest typem odwołania i nie zawiera pola typu odwołania na każdym poziomie zagnieżdżania. `unmanaged` Ograniczenie pozwala na zapis wielokrotnego użytku procedur do pracy z typami, które mogą być zmieniane jako bloki pamięci, jak pokazano w poniższym przykładzie:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Powyższa metoda musi zostać skompilowany w `unsafe` kontekstu, ponieważ używa ona `sizeof` operator dla typu, nie jest znany jako typ wbudowany. Bez `unmanaged` ograniczenie `sizeof` operatora jest niedostępny.

## <a name="delegate-constraints"></a>Delegowanie ograniczeń

Ponadto począwszy od języka C# 7.3, można użyć <xref:System.Delegate?displayProperty=nameWithType> lub <xref:System.MulticastDelegate?displayProperty=nameWithType> jako ograniczenie klasy bazowej. Środowisko CLR jest zawsze dozwolona to ograniczenie, ale niedozwolone w języku C#, go. `System.Delegate` Ograniczenie pozwala napisać kod, który współdziała z delegatów w sposób bezpieczny. Poniższy kod definiuje metodę rozszerzenia, która łączy dwa delegaty warunkiem, że są tego samego typu:

[!code-csharp[using the delegate constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Metoda powyżej umożliwia łączenie obiektów delegowanych, które są tego samego typu:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Jeśli usuniesz komentarz ostatni wiersz, nie będzie kompilacji. Zarówno `first` i `test` są typami delegatów, ale są one delegata różnych typów.

## <a name="enum-constraints"></a>Ograniczenia typu wyliczeniowego

Począwszy od języka C# 7.3, można również określić <xref:System.Enum?displayProperty=nameWithType> typu jako ograniczenia klasy bazowej. Środowisko CLR jest zawsze dozwolona to ograniczenie, ale niedozwolone w języku C#, go. Za pomocą typów ogólnych `System.Enum` umożliwiające bezpieczny programowania do wyników z pamięci podręcznej z poziomu przy użyciu metod statycznych w `System.Enum`. Poniższy przykład umożliwia znalezienie wszystkich prawidłowych wartości dla typu wyliczeniowego, a następnie tworzy słownik mapujący te wartości na jego reprezentację ciągu.

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Metody stosowane używać odbicia, która ma wpływ na wydajność. Możesz wywołać tę metodę, aby utworzyć kolekcję pamięci podręcznej i ponowne użycie zamiast powtarzania wywołania, które wymagają odbicia.

Można użyć tego jak pokazano w następującym przykładzie do wyliczenia i tworzenia słownik nazw i wartości:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [Klasy ogólne](../../../csharp/programming-guide/generics/generic-classes.md)  
- [new, ograniczenie](../../../csharp/language-reference/keywords/new-constraint.md)  
