---
title: "Spójne kolekcje w języku Visual Basic"
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be50b22e9acca9ff8cfbde798d78869ee1c72634
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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

## <a name="tuples-versus-structures"></a>Spójne kolekcje i struktury

Krotka Visual Basic jest typem wartości, który jest wystąpieniem jednej z **System.ValueTuple** typów ogólnych. Na przykład `holiday` krotki zdefiniowane w poprzednim przykładzie jest wystąpieniem <xref:System.ValueTuple%603> struktury. Zaprojektowano go jako lekkie kontener dla danych. Ponieważ spójnej kolekcji ma na celu ułatwić tworzenie obiektu z wieloma elementami danych, brakuje niektórych funkcji, które mogą mieć strukturze niestandardowej. Należą do nich następujące elementy:

- Elementy członkowskie klienta. Nie można definiować własnych właściwości, metody lub zdarzenia dla spójnych kolekcji.

- Sprawdzanie poprawności. Nie można sprawdzić poprawności danych przypisany do pola.

- Immutability. Modyfikowalne są krotek Visual Basic. Natomiast w strukturze niestandardowej umożliwia kontrolowanie, czy wystąpienie jest modyfikowalna lub modyfikować.

Jeśli niestandardowe elementy członkowskie, właściwość i pole weryfikacji lub immutability są ważne, należy użyć programu Visual Basic [struktury](../../../language-reference/statements/structure-statement.md) instrukcji, aby zdefiniować typu wartości niestandardowych.

Krotka Visual Basic dziedziczą członkowie jego **ValueTuple** typu. Oprócz pól należą do nich następujące metody:

| Element członkowski | Opis |
| ---|---|
| Wykonanie funkcji CompareTo | Porównuje bieżącą spójną kolekcję do innego krotki z taką samą liczbę elementów. |
| równa się | Określa, czy bieżącą spójną kolekcję jest równa innego spójnej kolekcji lub obiektu. |
| GetHashCode | Oblicza wartość skrótu dla bieżącego wystąpienia. |
| ToString | Zwraca reprezentację ciągu tego spójnej kolekcji, która ma postać `(Item1, Item2...)`, gdzie `Item1` i `Item2` reprezentują wartości pól spójnej kolekcji. |

Ponadto **ValueTuple** typy implementować <xref:System.Collections.IStructuralComparable> i <xref:System.Collections.IStructuralEquatable> interfejsów, które umożliwiają definiowanie comparers klienta.

## <a name="assignment-and-tuples"></a>Przypisanie i spójnych kolekcji

Visual Basic obsługuje przypisanie między typami spójnej kolekcji, które mają taką samą liczbę pól. Typy pól mogą być konwertowane, jeśli spełniony jest jeden z następujących czynności:

- W polu źródłowa i docelowa są tego samego typu.

- Zdefiniowano konwersji rozszerzającej (lub niejawne) typu źródłowego na typ docelowy. 

- `Option Strict`jest `On`, a zdefiniowano konwersji zawężającej (bezpośredniego lub pośredniego) typu źródłowego na typ docelowy. Ta konwersja może zgłoszenia wyjątku, jeśli wartością źródłową jest poza zakresem typu docelowego.

Inne konwersje nie są uznawane za przydziałów. Oto typy przydziałów, które mogą między typami spójnej kolekcji.

Należy wziąć pod uwagę następujące zmienne używane w poniższych przykładach:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

Pierwsze dwie zmienne `unnamed` i `anonymous`, nie ma nazwy semantycznego podana dla pola. Ich nazwy pól są domyślnymi `Item1` i `Item2`. Ostatnie dwie zmienne `named` i `differentName` mają nazwy pól semantycznego. Należy pamiętać, że te dwie spójne kolekcje mają różne nazwy pól.

Wszystkie cztery te krotki mają taką samą liczbę pól (określanych jako "Liczba ról") i typy pól są identyczne. W związku z tym wszystkie te przydziały działają:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Należy zauważyć, że nazwy krotki nie są przypisane. Wartości pól są przypisywane kolejności pól w spójnej kolekcji.

Warto zauważyć, że firma Microsoft można przypisać `named` spójnej kolekcji do `conversion` spójnej kolekcji, nawet jeśli pierwsze pole `named` jest `Integer`, a pierwsze pole `conversion` jest `Long`. To przypisanie zakończy się pomyślnie, ponieważ konwersja `Integer` do `Long` jest konwersję rozszerzającą.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Spójnych kolekcji zawierający różne liczby pól nie są można przypisać:

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
