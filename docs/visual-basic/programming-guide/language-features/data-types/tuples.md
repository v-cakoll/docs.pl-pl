---
title: Krotki
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: 378ee4e7d3a3b106b719e5da819b09f336ff218e
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226663"
---
# <a name="tuples-visual-basic"></a>Krotki (Visual Basic)

Począwszy od Visual Basic 2017, język Visual Basic oferuje wbudowaną obsługę spójnych krotek, które ułatwiają tworzenie spójnych krotek i uzyskiwanie dostępu do elementów krotek. Krotka jest lekkim strukturą danych, która ma określoną liczbę i sekwencję wartości. Podczas tworzenia wystąpienia krotki należy zdefiniować liczbę i typ danych każdej wartości (lub elementu). Na przykład 2-krotka (lub para) ma dwa elementy. Pierwsza może być `Boolean` wartością, a druga to `String` . Ponieważ krotki ułatwiają przechowywanie wielu wartości w pojedynczym obiekcie, są one często używane jako lekki sposób zwracania wielu wartości z metody.

> [!IMPORTANT]
> Obsługa krotki wymaga <xref:System.ValueTuple> typu. Jeśli .NET Framework 4,7 nie jest zainstalowana, należy dodać pakiet NuGet `System.ValueTuple` , który jest dostępny w galerii NuGet. Bez tego pakietu może zostać wyświetlony komunikat o błędzie kompilacji podobny do: "wstępnie zdefiniowany typ" ValueTuple (z,,,) "nie został zdefiniowany ani zaimportowany."

## <a name="instantiating-and-using-a-tuple"></a>Tworzenie wystąpień i używanie spójnej kolekcji

Tworzysz wystąpienie spójnej kolekcji, umieszczając ich wartości rozdzielane przecinkami w nawiasach. Każda z tych wartości zostaje następnie do pola krotki. Na przykład poniższy kod definiuje potrójną (lub 3-krotkę) z `Date` jako pierwszą wartością, a `String` jako drugą, a `Boolean` jako trzecią.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Domyślnie nazwa każdego pola w kolekcji składa się z ciągu `Item` wraz z jedną pozycją opartą na tym polu w spójnej kolekcji. W przypadku tej 3-spójnej kolekcji pole ma wartość, `Date` `Item1` `String` pole jest `Item2` , a `Boolean` pole jest `Item3` . Poniższy przykład wyświetla wartości pól krotki utworzone w poprzednim wierszu kodu

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Pola krotki Visual Basic są do odczytu i zapisu; Po utworzeniu wystąpienia spójnej kolekcji można zmodyfikować jej wartości. Poniższy przykład modyfikuje dwa z trzech pól krotki utworzonej w poprzednim przykładzie i wyświetla wynik.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Tworzenie wystąpienia i używanie nazwanej krotki

Zamiast używać domyślnych nazw dla pól krotki, można utworzyć wystąpienie *nazwanej krotki* przez przypisanie własnych nazw do elementów krotki. Dostęp do pól krotki można uzyskać za pomocą przypisanych im nazw *lub* według ich nazw domyślnych. Poniższy przykład tworzy wystąpienie tej samej 3-spójnej kolekcji jak poprzednio, z tą różnicą, że jawnie nazywa pierwsze pole `EventDate` , drugi `Name` i trzeci `IsHoliday` . Następnie wyświetla wartości pól, modyfikuje je i ponownie wyświetla wartości pól.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Wywnioskowane nazwy elementów krotki

Począwszy od Visual Basic 15,3, Visual Basic może wywnioskować nazwy elementów krotki; nie trzeba ich jawnie przypisywać. Wywnioskowane nazwy krotek są przydatne w przypadku inicjowania krotki z zestawu zmiennych i chcesz, aby nazwa elementu krotki była taka sama jak nazwa zmiennej.

Poniższy przykład tworzy `stateInfo` krotkę zawierającą trzy jawnie nazwane elementy, `state` , `stateName` , i `capital` . Należy zauważyć, że w przypadku nazywania elementów instrukcja inicjowania krotki po prostu przypisuje nazwane elementy wartości zmiennych o identycznych nazwach.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]

Ponieważ elementy i zmienne mają taką samą nazwę, kompilator Visual Basic może wywnioskować nazwy pól, jak pokazano w poniższym przykładzie.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Aby włączyć wywnioskowane nazwy elementów krotki, należy zdefiniować wersję kompilatora Visual Basic, która ma być używana w pliku projektu Visual Basic ( \* vbproj):

```xml
<PropertyGroup>
  <LangVersion>15.3</LangVersion>
</PropertyGroup>
```

Numer wersji może być dowolną wersją kompilatora Visual Basic rozpoczynającą się od 15,3. Zamiast nakodować twardą wersję kompilatora, można również określić "Najnowsza" jako wartość `LangVersion` do kompilowania z najnowszą wersją kompilatora Visual Basic zainstalowanego w systemie.

Aby uzyskać więcej informacji, zobacz [Ustawianie wersji językowej Visual Basic](../../../language-reference/configure-language-version.md).

W niektórych przypadkach kompilator Visual Basic nie może wywnioskować nazwy elementu krotki z nazwy kandydującej, a do pola krotki można odwoływać się tylko przy użyciu nazwy domyślnej, takiej jak `Item1` , `Item2` itp. Należą do nich:

- Nazwa kandydata jest taka sama jak nazwa składowej spójnej kolekcji, takiej jak `Item3` , `Rest` , lub `ToString` .

- Nazwa kandydata jest zduplikowana w spójnej kolekcji.

Gdy wnioskowanie o nazwie pola nie powiedzie się, Visual Basic nie generuje błędu kompilatora ani nie występuje wyjątek w czasie wykonywania. Zamiast tego pola krotek muszą być przywoływane przez ich wstępnie zdefiniowane nazwy, takie jak `Item1` i `Item2` .

## <a name="tuples-versus-structures"></a>Krotki i struktury

Krotka Visual Basic jest typem wartości, który jest wystąpieniem jednego z typów ogólnych **System. ValueTuple** . Na przykład `holiday` krotka zdefiniowana w poprzednim przykładzie jest wystąpieniem <xref:System.ValueTuple%603> struktury. Jest on przeznaczony do uproszczonego kontenera dla danych. Ponieważ krotka ma ułatwić tworzenie obiektu z wieloma elementami danych, nie ma niektórych funkcji, które mogą mieć niestandardową strukturę. Są to moduły:

- Niestandardowe elementy członkowskie. Nie można definiować własnych właściwości, metod lub zdarzeń dla krotki.

- Zatwierdzenia. Nie można sprawdzić poprawności danych przypisanych do pól.

- Niezmienności. Kolekcje Visual Basic są modyfikowalne. W przeciwieństwie do struktury niestandardowej można kontrolować, czy wystąpienie jest modyfikowalne czy niezmienne.

Jeśli niestandardowe elementy członkowskie, walidacja właściwości i pól lub niezmienności są ważne, należy użyć instrukcji Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) , aby zdefiniować niestandardowy typ wartości.

Krotka Visual Basic dziedziczy elementy członkowskie jego typu **ValueTuple** . Oprócz pól te elementy obejmują następujące metody:

| Członek | Opis |
| ---|---|
| CompareTo | Porównuje bieżącą krotkę z inną krotką o tej samej liczbie elementów. |
| Równa się | Określa, czy bieżąca Krotka jest równa innej kolekcji lub obiektowi. |
| GetHashCode | Oblicza wartość skrótu dla bieżącego wystąpienia. |
| ToString | Zwraca ciąg reprezentujący tę krotkę, która przyjmuje formularz `(Item1, Item2...)` , gdzie `Item1` i `Item2` reprezentuje wartości pól krotki. |

Ponadto typy **ValueTuple** implementują <xref:System.Collections.IStructuralComparable> i <xref:System.Collections.IStructuralEquatable> interfejsy, które umożliwiają definiowanie porównywania klientów.

## <a name="assignment-and-tuples"></a>Przypisanie i krotki

Visual Basic obsługuje przypisanie między typami krotek, które mają taką samą liczbę pól. Typy pól mogą być konwertowane, jeśli jest spełniony jeden z następujących warunków:

- Pole źródłowe i docelowe są tego samego typu.

- Zdefiniowano niejawną konwersję typu źródłowego na typ docelowy.

- `Option Strict`jest `On` i jest zdefiniowany Zawężanie (lub jawne) konwersji typu źródłowego na typ docelowy. Ta konwersja może zgłosić wyjątek, jeśli wartość źródłowa znajduje się poza zakresem typu docelowego.

Inne konwersje nie są brane pod uwagę w przypisaniach. Przyjrzyjmy się typom przypisań, które są dozwolone między typami krotek.

Należy wziąć pod uwagę te zmienne, które są używane w następujących przykładach:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

Pierwsze dwie zmienne, `unnamed` i nie `anonymous` mają nazw semantycznych dla pól. Nazwy pól są domyślne `Item1` i `Item2` . Ostatnie dwie zmienne `named` i `differentName` mają nazwy pól semantycznych. Należy zauważyć, że te dwie krotki mają różne nazwy pól.

Wszystkie cztery z tych krotek mają tę samą liczbę pól (określaną jako "liczba argumentów"), a typy tych pól są identyczne. W związku z tym wszystkie te przypisania działają:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Zauważ, że nazwy krotek nie są przypisane. Wartości pól są przypisywane po kolejności pól w spójnej kolekcji.

Na koniec należy zauważyć, że możemy przypisać `named` krotkę do `conversion` krotki, nawet jeśli pierwsze pole `named` to `Integer` a, a pierwsze pole `conversion` jest `Long` . To przypisanie powiedzie się, ponieważ konwersja `Integer` na a `Long` jest konwersją rozszerzającą.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Nie można przypisać krotek z różnymi liczbami pól:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Krotki jako wartości zwracane przez metodę

Metoda może zwracać tylko jedną wartość. Często, chociaż chcemy, aby wywołanie metody zwracało wiele wartości. Istnieje kilka sposobów obejścia tego ograniczenia:

- Można utworzyć niestandardową klasę lub strukturę, której właściwości lub pola reprezentują wartości zwracane przez metodę. Jest to bardzo ciężki rozwiązanie; wymaga zdefiniowania typu niestandardowego, którego jedynym celem jest pobieranie wartości z wywołania metody.

- Można zwrócić jedną wartość z metody i zwrócić pozostałe wartości przez przekazanie ich przez odwołanie do metody. Wiąże się to z narzutem tworzenia wystąpienia zmiennej i ryzyka przypadkowo zastępującej wartość zmiennej przekazanej przez odwołanie.

- Możesz użyć krotki, która udostępnia lekkie rozwiązanie do pobierania wielu zwracanych wartości.

Na przykład metody **TryParse** w programie .NET zwracają `Boolean` wartość wskazującą, czy operacja analizowania zakończyła się pomyślnie. Wynik operacji analizowania jest zwracany w zmiennej przekazaną przez odwołanie do metody. Zwykle wywołanie metody analizy, takie jak wygląda następująco <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> :

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Możemy zwrócić krotkę z operacji analizowania, jeśli zawijamy wywołanie <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metody w naszej metodzie. W poniższym przykładzie `NumericLibrary.ParseInteger` wywołuje <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodę i zwraca nazwaną krotkę z dwoma elementami.

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Następnie można wywołać metodę z kodem podobnym do poniższego:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Visual Basic krotek i krotki w .NET Framework

Krotka Visual Basic to wystąpienie jednego z typów ogólnych **System. ValueTuple** , które zostały wprowadzone w .NET Framework 4,7. .NET Framework obejmuje również zestaw rodzajowych klas **System. krotek** . Jednak klasy te różnią się od Visual Basic krotek i typów ogólnych **System. ValueTuple** na wiele sposobów:

- Elementy klas **krotek** są właściwościami o nazwach `Item1` , `Item2` i tak dalej. W Visual Basic krotekch i typach **ValueTuple** elementy krotki to pola.

- Nie można przypisać znaczących nazw do elementów wystąpienia **krotki** lub wystąpienia **ValueTuple** . Visual Basic umożliwia przypisanie nazw, które komunikują znaczenie pól.

- Właściwości wystąpienia **krotki** są tylko do odczytu; krotki są niezmienne. W Visual Basic krotekch i typach **ValueTuple** pola krotek są do odczytu i zapisu; krotki są modyfikowalne.

- Typy **kolekcji** generycznej to typy odwołań. Korzystanie z tych typów **krotek** oznacza alokowanie obiektów. W przypadku ścieżek gorąca może to mieć wymierny wpływ na wydajność aplikacji. Kolekcje Visual Basic i typy **ValueTuple** są typami wartości.

Metody rozszerzające w <xref:System.TupleExtensions> klasie ułatwiają konwersję między kolekcjami Visual Basic i obiektami **kolekcji** programu .NET. Metoda **ToTuple** konwertuje krotkę Visual Basic do obiektu **krotki** platformy .NET, a Metoda **ToValueTuple** Konwertuje obiekt **krotki** .NET na krotkę Visual Basic.

Poniższy przykład tworzy krotkę, konwertuje ją na obiekt **krotki** .NET i konwertuje ją z powrotem do krotki Visual Basic. Przykład następnie porównuje tę spójną krotkę z oryginalną, aby upewnić się, że są równe.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka Visual Basic](index.md)
