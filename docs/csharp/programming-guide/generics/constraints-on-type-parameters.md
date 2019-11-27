---
title: Ograniczenia dotyczące parametrów typu — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: d05307735506db0f0e4abab067334e4f0466ee6a
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204637"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Ograniczenia dotyczące parametrów typu (C# Przewodnik programowania)

Ograniczenia informują kompilator o możliwościach, które argument typu musi zawierać. Bez żadnych ograniczeń argument typu może być dowolnym typem. Kompilator może przyjmować tylko elementy członkowskie <xref:System.Object?displayProperty=nameWithType>, które jest ostateczną klasą bazową dla dowolnego typu .NET. Aby uzyskać więcej informacji, zobacz [Dlaczego należy używać ograniczeń](#why-use-constraints). Jeśli kod klienta próbuje utworzyć wystąpienie klasy przy użyciu typu, który nie jest dozwolony przez ograniczenie, wynikiem jest błąd czasu kompilacji. Ograniczenia są określone za pomocą słowa kluczowego `where` kontekstowego. W poniższej tabeli wymieniono siedem typów ograniczeń:

|Typu|Opis|
|----------------|-----------------|
|`where T : struct`|Argument typu musi być typem wartości niedopuszczający wartości null. Aby uzyskać informacje o typach wartości null, zobacz [dopuszczanie typów wartości null](../../language-reference/builtin-types/nullable-value-types.md). Ponieważ wszystkie typy wartości mają dostępny Konstruktor bez parametrów, ograniczenie `struct` implikuje ograniczenie `new()` i nie można go łączyć z ograniczeniem `new()`. Nie można również połączyć ograniczenia `struct` z ograniczeniami `unmanaged`.|
|`where T : class`|Argument typu musi być typem referencyjnym. To ograniczenie dotyczy również dowolnego typu klasy, interfejsu, delegata lub tablicy.|
|`where T : notnull`|Argument typu musi być typem niedopuszczający wartości null. Argument może być typem referencyjnym niedopuszczający wartości null C# w 8,0 lub późniejszym lub nie DOPUSZCZANYM typem wartości. To ograniczenie dotyczy również dowolnego typu klasy, interfejsu, delegata lub tablicy.|
|`where T : unmanaged`|Argument typu musi być [typem niezarządzanym](../../language-reference/builtin-types/unmanaged-types.md)niedopuszczający wartości null. Ograniczenie `unmanaged` implikuje ograniczenie `struct` i nie można go łączyć z ograniczeniami `struct` lub `new()`.|
|`where T : new()`|Typ argumentu musi mieć publicznego konstruktora bez parametrów. W przypadku użycia razem z innymi ograniczeniami, ograniczenie `new()` musi być określone jako ostatnie. Nie można łączyć ograniczenia `new()` z ograniczeniami `struct` i `unmanaged`.|
|`where T :` *\<nazwę klasy bazowej >*|Argument typu musi być lub pochodzić od określonej klasy podstawowej.|
|`where T :` *\<nazwy interfejsu >*|Argument typu muszą być lub implementować określonego interfejsu. Można określić wiele ograniczeń interfejsu. Można też ogólnego ograniczający interfejsu.|
|`where T : U`|Argumentu typu dostarczonego T musi być lub pochodzić od argument dostarczony dla U.|

## <a name="why-use-constraints"></a>Dlaczego warto używać ograniczeń

Ograniczając parametr typu, zwiększa liczbę dozwolonych operacji i wywołań metod do tych, które są obsługiwane przez typ ograniczenia i wszystkie typy w hierarchii dziedziczenia. Podczas projektowania klas ogólnych lub metod w przypadku wykonywania operacji na ogólnych elementach członkowskich wykraczających poza proste przypisanie lub wywoływanie jakichkolwiek metod nieobsługiwanych przez <xref:System.Object?displayProperty=nameWithType>należy zastosować ograniczenia do parametru typu. Na przykład ograniczenie klasy bazowej instruuje kompilator, że tylko obiekty tego typu lub pochodne z tego typu będą używane jako argumenty typu. Gdy kompilator ma tę gwarancję, może zezwolić na wywoływanie metod tego typu w klasie generycznej. Poniższy przykład kodu demonstruje funkcjonalność, którą można dodać do klasy `GenericList<T>` (w artykule [wprowadzenie do typów ogólnych](../../../standard/generics/index.md)) przez zastosowanie ograniczenia klasy bazowej.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Ograniczenie pozwala klasie generycznej używać właściwości `Employee.Name`. Ograniczenie określa, że wszystkie elementy typu `T` mają być obiektem `Employee` lub obiektem, który dziedziczy po `Employee`.

Do tego samego parametru typu można zastosować wiele ograniczeń, a same ograniczenia mogą być typami ogólnymi w następujący sposób:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Podczas stosowania ograniczenia `where T : class`, unikaj operatorów `==` i `!=` w parametrze typu, ponieważ te operatory przetestują tylko tożsamość referencyjną, a nie równość wartości. To zachowanie występuje nawet wtedy, gdy te operatory są przeciążone w typie, który jest używany jako argument. Poniższy kod ilustruje ten punkt; wynik ma wartość false, mimo że Klasa <xref:System.String> przeciążuje operator `==`.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilator wie, że `T` jest typem referencyjnym w czasie kompilacji i musi używać domyślnych operatorów, które są prawidłowe dla wszystkich typów referencyjnych. Jeśli konieczne jest przetestowanie pod kątem równości wartości, zalecanym sposobem jest również zastosowanie ograniczenia `where T : IEquatable<T>` lub `where T : IComparable<T>` i zaimplementowanie interfejsu w dowolnej klasie, która będzie używana do konstruowania klasy generycznej.

## <a name="constraining-multiple-parameters"></a>Ograniczanie wielu parametrów

Można zastosować ograniczenia do wielu parametrów i wiele ograniczeń do jednego parametru, jak pokazano w następującym przykładzie:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Niepowiązane parametry typu

 Parametry typu, które nie mają żadnych ograniczeń, takich jak T w publicznej klasy `SampleClass<T>{}`, są nazywane niezwiązanymi parametrami typu. Parametry typu niepowiązanego mają następujące reguły:

- Nie można używać operatorów `!=` i `==`, ponieważ nie ma gwarancji, że konkretny argument typu będzie obsługiwał te operatory.
- Mogą być konwertowane na i z `System.Object` lub jawnie konwertowane na dowolny typ interfejsu.
- Można je porównać z [wartością null](../../language-reference/keywords/null.md). Jeśli niezwiązany parametr jest porównywany z `null`, porównanie zwróci wartość false, jeśli argument typu jest typem wartości.

## <a name="type-parameters-as-constraints"></a>Parametry typu jako ograniczenia

Użycie parametru typu ogólnego jako ograniczenia jest przydatne, gdy funkcja członkowska z własnym parametrem typu musi ograniczyć ten parametr do parametru typu zawierającego typ, jak pokazano w następującym przykładzie:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

W poprzednim przykładzie `T` jest ograniczeniem typu w kontekście metody `Add` i niezwiązanym parametrem typu w kontekście klasy `List`.

Parametry typu mogą być również używane jako ograniczenia w definicjach klasy generycznej. Parametr type musi być zadeklarowany w nawiasach kątowych wraz z innymi parametrami typu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Użyteczność parametrów typu jako ograniczenia z klasami generycznymi jest ograniczona, ponieważ kompilator może nie zajmować niczego informacji o parametrze typu, z wyjątkiem tego, że pochodzi on z `System.Object`. Użyj parametrów typu jako ograniczeń dotyczących klas ogólnych w scenariuszach, w których chcesz wymusić relację dziedziczenia między dwoma parametrami typu.

## <a name="notnull-constraint"></a>Ograniczenie NotNull

Począwszy od C# 8,0, można użyć ograniczenia `notnull`, aby określić, że argument typu musi być typem wartości niedopuszczających wartości null lub typem referencyjnym, który nie dopuszcza wartości null. Ograniczenie `notnull` może być używane tylko w kontekście `nullable enable`. Kompilator generuje ostrzeżenie w przypadku dodania ograniczenia `notnull` w kontekście dopuszczającym wartość null. 

W przeciwieństwie do innych ograniczeń, gdy argument typu narusza ograniczenie `notnull`, kompilator generuje ostrzeżenie, gdy ten kod jest kompilowany w kontekście `nullable enable`. Jeśli kod jest kompilowany w kontekście Oblivious dopuszczający wartość null, kompilator nie generuje żadnych ostrzeżeń ani błędów.

## <a name="unmanaged-constraint"></a>Niezarządzany warunek ograniczający

Począwszy od C# 7,3, można użyć ograniczenia `unmanaged`, aby określić, że parametr typu musi być [typem niezarządzanym](../../language-reference/builtin-types/unmanaged-types.md)null. Ograniczenie `unmanaged` umożliwia zapisanie procedur wielokrotnego użytku w celu pracy z typami, które mogą być przetwarzane jako bloki pamięci, jak pokazano w następującym przykładzie:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Poprzednią metodę należy skompilować w kontekście `unsafe`, ponieważ używa ona operatora `sizeof` na typie, który nie jest znany jako typ wbudowany. Bez ograniczenia `unmanaged` operator `sizeof` jest niedostępny.

Ograniczenie `unmanaged` implikuje ograniczenie `struct` i nie może zostać połączone z nim. Ponieważ ograniczenie `struct` implikuje ograniczenie `new()`, nie można łączyć ograniczenia `unmanaged` z ograniczeniem `new()`.

## <a name="delegate-constraints"></a>Delegowanie ograniczeń

Począwszy od C# 7,3, można również użyć <xref:System.Delegate?displayProperty=nameWithType> lub <xref:System.MulticastDelegate?displayProperty=nameWithType> jako ograniczenia klasy bazowej. Środowisko CLR zawsze zezwala na to ograniczenie, ale C# język nie jest dozwolony. Ograniczenie `System.Delegate` pozwala pisać kod, który współpracuje z delegatami w sposób bezpieczny dla typu. Poniższy kod definiuje metodę rozszerzenia, która łączy dwa Delegaty pod warunkiem, że są tego samego typu:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Możesz użyć powyższej metody do łączenia delegatów, które są tego samego typu:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Usunięcie komentarza do ostatniego wiersza nie spowoduje skompilowania. Zarówno `first`, jak i `test` są typami delegatów, ale są różnymi typami delegatów.

## <a name="enum-constraints"></a>Ograniczenia wyliczeniowe

Począwszy od C# 7,3, można również określić typ <xref:System.Enum?displayProperty=nameWithType> jako ograniczenie klasy bazowej. Środowisko CLR zawsze zezwala na to ograniczenie, ale C# język nie jest dozwolony. Typy ogólne wykorzystujące `System.Enum` zapewniają programowanie bezpiecznego typu w celu buforowania wyników z używania metod statycznych w `System.Enum`. Poniższy przykład odnajduje wszystkie prawidłowe wartości dla typu wyliczeniowego, a następnie tworzy słownik, który mapuje te wartości na jego reprezentację w postaci ciągu.

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Używane metody wykorzystują odbicie, które mają wpływ na wydajność. Można wywołać tę metodę, aby utworzyć kolekcję, która jest buforowana i ponownie używana zamiast powtarzających się wywołań, które wymagają odbicia.

Można go użyć, jak pokazano w poniższym przykładzie, aby utworzyć Wyliczenie i skompilować słownik jego wartości i nazw:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Klasy ogólne](./generic-classes.md)
- [new, ograniczenie](../../language-reference/keywords/new-constraint.md)
