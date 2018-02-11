---
title: "Spójne kolekcje w języku Visual Basic"
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="tuples-visual-basic"></a>Krotki (Visual Basic)

Począwszy od programu Visual Basic 2017 języka Visual Basic udostępnia wbudowaną obsługę krotek, która umożliwia tworzenie krotek i uzyskiwanie dostępu do elementów krotek łatwiejsze. Krotka jest strukturą lekki danych, która ma określoną liczbę i sekwencja wartości. W przypadku wystąpienia spójnej kolekcji, należy zdefiniować liczbę i typ danych w każdej wartości (lub elementu). Na przykład krotki 2 (lub parę) zawiera dwa elementy. Może być pierwszym `Boolean` wartości, podczas gdy druga `String`. Ponieważ spójne kolekcje ułatwiają przechowywanie wielu wartości w jednym obiekcie, często są one używane jako lekkie sposób zwrócenia wiele wartości z metody.

> [!IMPORTANT]
> Obsługa krotki wymaga <xref:System.ValueTuple> typu. .NET Framework 4.7 nie jest zainstalowany, należy dodać pakiet NuGet `System.ValueTuple`, która jest dostępna w galerii NuGet. Bez tego pakietu może wystąpić błąd kompilacji podobne do "Wstępnie zdefiniowany typ"ValueTuple(Of,,,)"nie został zdefiniowany ani zaimportowany."

## <a name="instantiating-and-using-a-tuple"></a>Tworzenie wystąpień i przy użyciu spójnych kolekcji

Umieszczając nawiasami wiadomości błyskawicznych wartości rozdzielanych przecinkami Utwórz wystąpienie spójnej kolekcji. Każdy z tych wartości staje się pole spójnej kolekcji. Na przykład poniższy kod definiuje triple (lub krotki 3) z `Date` jako wartość pierwszego `String` jako jego, a `Boolean` jako jego innych.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Domyślnie nazwa każdego pola w krotce składa się z ciągu `Item` wraz z pozycji na podstawie jednego pola w spójnej kolekcji. Dla tego krotki 3 `Date` pole jest `Item1`, `String` pole jest `Item2`i `Boolean` pole jest `Item3`. W poniższym przykładzie przedstawiono wartości pól spójna kolekcja znajdująca się w poprzednim wierszu kodu

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Pola spójnych kolekcji Visual Basic są odczytu i zapisu; Po krotka został uruchomiony, można modyfikować jej wartości. Poniższy przykład modyfikuje dwie z trzech pól krotki utworzony w poprzednim przykładzie i wyświetla wyniki.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Tworzenie wystąpień i przy użyciu spójnej kolekcji o nazwie

Zamiast przy użyciu domyślnych nazw pól spójnej kolekcji, można utworzyć wystąpienia *o nazwie krotki* przez przypisanie własne nazwy elementów spójnej kolekcji. Pola krotki mają dostęp przy użyciu nazw przypisane *lub* przez domyślne nazwy. Poniższy przykład tworzy wystąpienie tego samego krotki 3 jak poprzednio, z wyjątkiem tego, że jawnie nazwy pierwsze pole `EventDate`, drugi `Name`, a trzeci `IsHoliday`. Następnie wyświetla wartości pól, modyfikuje je i ponownie wyświetla wartości pól.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Nazwy elementów wywnioskowanych spójnej kolekcji

Począwszy od 15 ustęp 3 Visual Basic, Visual Basic można wywnioskować nazwy elementów krotki; nie masz ich jawnie przypisać. Wywnioskowane krotki nazwy są przydatne, gdy zainicjować spójną kolekcję z zestawu zmiennych i ma być taka sama jak nazwa zmiennej nazwy elementu spójnej kolekcji. 

Poniższy przykład tworzy `stateInfo` elementy, o nazwie spójnej kolekcji, która zawiera trzy jawnie `state`, `stateName`, i `capital`. Należy zauważyć, że w nazw elementów, instrukcja inicjowania spójnej kolekcji po prostu przypisuje elementy o wartości zmiennych o identycznej nazwie.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
Ponieważ elementy i zmienne mają taką samą nazwę, kompilator Visual Basic można wywnioskować nazwy pól, jak w poniższym przykładzie pokazano.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Aby włączyć nazwy elementów interred spójnej kolekcji, należy zdefiniować wersji kompilatora Visual Basic do użycia w projekcie języka Visual Basic (\*.vbproj) plików: 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Wartości zwracane krotek jako — metoda

Metoda może zwracać tylko jedną wartość. Często jednak chcesz wywołania metody, aby zwrócić wielu wartości. Istnieje kilka sposobów obejścia tego ograniczenia:

- Możesz tworzyć niestandardowe klasy lub struktury którego właściwości lub pola reprezentują wartości zwracanych przez metodę. W związku z tym jest to rozwiązanie ogromnych; wymaga zdefiniowania typu niestandardowego, którego jedynym celem jest można pobrać wartości z wywołania metody.

- Zwraca pojedynczą wartość z metody i pozostałe wartości zwracane przez przekazywanie ich poprzez odwołanie do metody. Obejmuje to obciążenie tworzenia wystąpienia w zmiennej i ryzyka nieodwracalne nadpisanie wartość zmiennej, który jest przekazywany przez odwołanie.

- Można użyć spójnej kolekcji, która to lekkie rozwiązanie do pobierania wiele wartości zwrotnych.

Na przykład **TryParse** metod .NET powrotu `Boolean` wartość, która wskazuje, czy podczas analizowania operacja zakończyła się pomyślnie. Wynik operacji przetwarzania jest zwracana w zmiennej przekazywana przez odwołanie do metody. Zazwyczaj wywołanie metodę analizowania, takich jak <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> wygląda podobnie do następującego:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Zostanie zwrócona krotka z przetwarzaniem operacji, jeśli firma Microsoft zawijać wywołanie <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metody własnej metody. W poniższym przykładzie `NumericLibrary.ParseInteger` wywołania <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodę i zwraca spójną kolekcję o nazwie z dwoma elementami. 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Następnie można wywołać metody z kodu podobne do poniższych:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Krotki Visual Basic i spójnych kolekcji w programie .NET Framework

Krotka Visual Basic jest wystąpienie jednego z **System.ValueTuple** typów ogólnych, które zostały wprowadzone w .NET Framework 4.7. .NET Framework obejmuje również zestaw ogólny **System.Tuple** klasy. Te klasy jednak różnić się od krotek Visual Basic i **System.ValueTuple** typów ogólnych na kilka sposobów:

- Elementy **krotki** klasy są właściwości o nazwie `Item1`, `Item2`i tak dalej. W Visual Basic krotek i **ValueTuple** pola są typy elementów spójnej kolekcji.

- Nie można przypisać łatwy do rozpoznania nazwy elementów **krotki** wystąpienia lub **ValueTuple** wystąpienia. Visual Basic umożliwia przypisanie nazw, które komunikują się znaczenie pola.

- Właściwości **krotki** wystąpienia są tylko do odczytu; spójne kolekcje są niezmienne. W Visual Basic krotek i **ValueTuple** typów, pól krotki są odczytu i zapisu; spójne kolekcje są modyfikowalne.

- Ogólnego **krotki** typy są typy referencyjne. Korzystanie z tych **krotki** typy oznacza Alokacja obiektów. Na gorąco ścieżki to ma zauważalnego wpływu na wydajność aplikacji. Krotki Visual Basic i **ValueTuple** typy są typami wartości.

Metody rozszerzenia w <xref:System.TupleExtensions> klasy ułatwia konwersję między krotek Visual Basic .NET **krotki** obiektów. **ToTuple** metoda konwertuje spójnych kolekcji Visual Basic .NET **krotki** obiektu i **ToValueTuple** metoda konwertuje .NET **krotki** obiekt do spójnych kolekcji Visual Basic.

Poniższy przykład tworzy spójną kolekcję, konwertuje ją na .NET **krotki** obiektu i konwertuje ją z powrotem do spójnych kolekcji Visual Basic. Przykład następnie porównuje to krotki z oryginału, aby upewnić się, że są one takie same.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka Visual Basic](index.md)  
