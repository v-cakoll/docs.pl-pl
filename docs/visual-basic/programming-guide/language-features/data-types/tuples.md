---
title: Kolekcje w języku Visual Basic
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: c0198cde88b66f5e115c82b5454bd8a32db7ef96
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143717"
---
# <a name="tuples-visual-basic"></a>Krotki (Visual Basic)

Począwszy od 2017 Visual Basic języka Visual Basic oferuje wbudowaną obsługę krotek, który ułatwia tworzenie krotek i uzyskiwania dostępu do elementów krotek łatwiejsze. Spójna Kolekcja to struktura danych lekki, która ma określoną liczbę i sekwencję wartości. Podczas tworzenia wystąpienia spójnej kolekcji należy zdefiniować numer i typ danych w każdej wartości (lub elementu). Na przykład 2-krotka (lub para) ma dwa elementy. Może być pierwszym `Boolean` wartości, a drugą jest wartość `String`. Ponieważ kolekcje ułatwiają do przechowywania wielu wartości w pojedynczy obiekt, często są one używane jako lekka sposób zwracanie wielu wartości z metody.

> [!IMPORTANT]
> Obsługa krotki wymaga <xref:System.ValueTuple> typu. Jeśli nie zainstalowano programu .NET Framework 4.7, należy dodać pakiet NuGet `System.ValueTuple`, który jest dostępny w galerii NuGet. Bez tego pakietu może wystąpić błąd kompilacji podobny do "Wstępnie zdefiniowany typ"ValueTuple(Of,,,)"nie został zdefiniowany ani zaimportowany."

## <a name="instantiating-and-using-a-tuple"></a>Utworzenie wystąpienia i korzystania z krotki

Umieszczając nawiasami wiadomości błyskawicznych wartości rozdzielonych przecinkami Utwórz wystąpienie spójnej kolekcji. Każda z tych wartości stanie się polem spójnej kolekcji. Na przykład, poniższy kod definiuje triple (lub 3-krotka) za pomocą `Date` jako wartość pierwszej `String` jako jego sekunda i `Boolean` jako jego innych.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Domyślnie nazwa każdego pola w krotce składa się z ciągu `Item` wraz z pozycji liczonego od jednego pola w spójnej kolekcji. Dla tego 3-krotka `Date` pole jest `Item1`, `String` pole jest `Item2`i `Boolean` pole jest `Item3`. Poniższy przykład wyświetla wartości pól spójna kolekcja znajdująca się w poprzednim wierszu kodu

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Pola krotki języka Visual Basic są odczytu / zapisu Po został uruchomiony spójnej kolekcji, można zmodyfikować jego wartości. Poniższy przykład modyfikuje dwa z trzech pól krotki utworzony w poprzednim przykładzie i wyświetla wynik.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Utworzenie wystąpienia i przy użyciu nazwanego krotki

Zamiast używania nazw domyślnych pól spójnej kolekcji, można utworzyć wystąpienie *o nazwie krotki* , przypisując własnymi nazwami elementów krotki. Pola spójnej kolekcji następnie są dostępne przy użyciu ich nazw przypisane *lub* przez ich domyślne nazwy. Poniższy przykład tworzy wystąpienie tego samego 3-krotka jak poprzednio, chyba że jawnie nazw pierwsze pole `EventDate`, drugi `Name`, a trzeci `IsHoliday`. Go następnie wyświetla wartości pól modyfikuje je i ponownie wyświetla wartości pól.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Wywnioskowane nazwy elementów krotki

Począwszy od 15.3 programu Visual Basic, Visual Basic można wywnioskować nazwami elementów krotki; nie trzeba przypisać je jawnie. Nazwy wywnioskowanego krotki są przydatne podczas inicjowania spójną kolekcję na podstawie zestawu zmiennych i chcesz, aby nazwa elementu krotki być taka sama jak nazwa zmiennej. 

Poniższy przykład tworzy `stateInfo` spójną kolekcją, która zawiera trzy jawnie nazwane elementy `state`, `stateName`, i `capital`. Należy zauważyć, że w nazwach elementów, instrukcja inicjowania krotki po prostu przypisuje elementy o wartości zmiennych o identycznej nazwie.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
Ponieważ elementy i zmienne mają taką samą nazwę, kompilator Visual Basic można wywnioskować nazw pól, co ilustruje poniższy przykład.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Aby włączyć wywnioskowane nazwy elementów krotki, należy zdefiniować wersji kompilatora języka Visual Basic do użycia w projekcie języka Visual Basic (\*.vbproj) pliku: 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 
```

Numer wersji może być dowolną wersję kompilatora języka Visual Basic, począwszy od 15.3. Zamiast kodować na określonej wersji kompilatora, można również określić "najnowszej wersji" jako wartość `LangVersion` można skompilować przy użyciu najnowszej wersji kompilatora języka Visual Basic, zainstalowanych w systemie.

Aby uzyskać więcej informacji, zobacz [ustawienie wersji języka Visual Basic](../../../language-reference/configure-language-version.md).

W niektórych przypadkach kompilator Visual Basic nie można wywnioskować nazwa elementu krotki z nazwy Release candidate, a pole spójnej kolekcji mogą być przywoływane tylko, przy użyciu domyślnej nazwy, takie jak `Item1`, `Item2`itp. Należą do nich następujące elementy:

- Nazwa Release candidate jest taka sama jak nazwa elementu członkowskiego spójnej kolekcji, takie jak `Item3`, `Rest`, lub `ToString`.

- Nazwa Release candidate jest zduplikowana w spójnej kolekcji.
 
Podczas wnioskowania Nazwa pola nie powiedzie się, Visual Basic nie generuje błąd kompilatora nie jest wyjątek w czasie wykonywania. Zamiast tego pola krotki musi odwoływać się ich wstępnie zdefiniowanych nazw, takich jak `Item1` i `Item2`. 
  
## <a name="tuples-versus-structures"></a>Kolekcje i struktury

Krotki języka Visual Basic jest typem wartości, który jest wystąpieniem jednej z **System.ValueTuple** typów ogólnych. Na przykład `holiday` krotki zdefiniowane w poprzednim przykładzie to wystąpienie <xref:System.ValueTuple%603> struktury. Zaprojektowano go jako lekka kontener dla danych. Ponieważ spójnej kolekcji ma na celu ułatwić utworzenia obiektu z wielu elementów danych, brakuje niektórych funkcji, które może mieć strukturze niestandardowej. Należą do nich następujące elementy:

- Niestandardowe elementy członkowskie. Nie można zdefiniować własne właściwości, metody i zdarzenia dla krotki.

- Sprawdzanie poprawności. Nie można zweryfikować danych przypisane do pól.

- Niezmienności. Kolekcje języka Visual Basic są modyfikowalna. Natomiast w strukturze niestandardowej umożliwia kontrolowanie czy wystąpienie jest modyfikowalną niezmienne.

W przypadku niestandardowych elementów członkowskich, właściwości i sprawdzanie poprawności pól lub niezmienności ważna, należy używać języka Visual Basic [struktury](../../../language-reference/statements/structure-statement.md) instrukcji, aby zdefiniować typ wartości niestandardowych.

Krotki języka Visual Basic dziedziczą członkowie jej **ValueTuple** typu. Oprócz jego pól należą do nich następujące metody:

| Element członkowski | Opis |
| ---|---|
| Element compareTo | Porównuje bieżącą spójną kolekcję do innego krotki z taką samą liczbę elementów. |
| Równa się | Określa, czy bieżącą spójną kolekcję jest równa innego spójnej kolekcji lub obiektu. |
| GetHashCode | Oblicza wartość skrótu dla bieżącego wystąpienia. |
| ToString | Zwraca reprezentację ciągu tego spójna kolekcja, która ma postać `(Item1, Item2...)`, gdzie `Item1` i `Item2` reprezentują wartości pól spójnej. |

Ponadto **ValueTuple** typy implementują <xref:System.Collections.IStructuralComparable> i <xref:System.Collections.IStructuralEquatable> interfejsów, które umożliwiają definiowanie porównywanie klienta.

## <a name="assignment-and-tuples"></a>Przypisanie i krotki

Visual Basic obsługuje przypisanie między typy krotek, które mają taką samą liczbę pól. Typy pól mogą być konwertowane, jeśli jest spełniony jeden z następujących czynności:

- Pole źródłowe i docelowe mają tego samego typu.

- Zdefiniowano rozszerzającą (lub niejawnie) konwersji typu źródłowego na typ docelowy. 

- `Option Strict` jest `On`, i zdefiniowano konwersji zawężającej (lub jawny) typu źródłowego na typ docelowy. Ta konwersja może zgłosić wyjątek, jeśli wartość źródła znajduje się poza zakresem typu docelowego.

Inne konwersje nie są uwzględniane przydziałów. Przyjrzyjmy się rodzaje przypisania, które są dozwolone między typami spójnej kolekcji.

Należy wziąć pod uwagę te zmienne używane w następujących przykładach:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

Pierwsze dwie zmienne `unnamed` i `anonymous`, nie zawiera semantyczną nazw podane dla pól. Ich nazwy pól są domyślnie `Item1` i `Item2`. Ostatnie dwie zmienne `named` i `differentName` mają nazwy pól semantycznego. Należy pamiętać, że te dwie spójne kolekcje mają różne nazwy pól.

Wszystkie cztery krotek, te mają taką samą liczbę pola (nazywane "liczby argumentów") i typy tych pól są identyczne. W związku z tym wszystkie te przydziały pracy:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Należy zauważyć, że nazwy kolekcje nie są przypisane. Wartości pól są przypisywane w kolejności pól w spójnej kolekcji.

Na koniec Zauważ, że można przypisywać `named` krotka `conversion` spójnej kolekcji, nawet jeśli pierwsze pole `named` jest `Integer`, a pierwsze pole `conversion` jest `Long`. To przypisanie zakończy się pomyślnie, ponieważ konwersja `Integer` do `Long` konwersji rozszerzającej.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Krotki z różną liczbą pól nie są możliwe do przypisania:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Krotki jako wartości zwracane metody

Metoda może zwracać pojedynczą wartość. Często jednak chcesz wywołanie metody zwracanie wielu wartości. Istnieje kilka sposobów obejścia tego ograniczenia:

- Można utworzyć niestandardową klasę lub strukturę którego właściwości lub pól reprezentują wartości zwracanych przez metodę. Ten sposób jest rozwiązaniem niewielkich; wymaga zdefiniowania typ niestandardowy, którego jedynym celem jest można pobrać wartości z wywołania metody.

- Może zwracać pojedynczą wartość z metody, a pozostałe wartości są zwracane, przekazując je przez odwołanie do metody. Obejmuje to obciążenie związane z wystąpienia zmienną i ryzyko nieodwracalne nadpisanie wartość zmiennej, który jest przekazywany przez odwołanie.

- Można użyć spójnej kolekcji, która zapewnia rozwiązanie o małych wymaganiach do pobierania z wieloma wartościami zwracanymi.

Na przykład **TryParse** metod .NET powrotu `Boolean` wartość, która wskazuje, czy podczas analizowania operacja zakończyła się pomyślnie. Wynik operacji analizowania jest zwracany w zmiennej, przekazywany przez odwołanie do metody. Zazwyczaj wywołanie w celu analizowania metody takie jak <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> wygląda podobnie do następującego:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Firma Microsoft zwraca spójną kolekcję z operacji analizowania, jeśli możemy opakować wywołanie <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metody w własną metodę. W poniższym przykładzie `NumericLibrary.ParseInteger` wywołania <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodę i zwraca spójną kolekcję o nazwie z dwóch elementów. 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Następnie możesz wywołać metody z kodu, jak pokazano poniżej:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Spójne kolekcje w programie .NET Framework i Visual Basic kolekcje

Spójna kolekcja języka Visual Basic to wystąpienie jednego z **System.ValueTuple** typów ogólnych, które zostały wprowadzone w .NET Framework 4.7. Program .NET Framework zawiera również zestaw ogólnych **System.Tuple** klasy. Te klasy jednak różnić się od krotek języka Visual Basic i **System.ValueTuple** typów ogólnych w na kilka sposobów:

- Elementy **krotki** klasy są właściwości o nazwie `Item1`, `Item2`i tak dalej. W języku Visual Basic w spójnych kolekcjach i **ValueTuple** typy, elementy krotki są polami.

- Nie można przypisać opisowych nazw elementów **krotki** wystąpienia lub **ValueTuple** wystąpienia. Visual Basic umożliwia można przypisać nazwy, które komunikują się znaczenie pola.

- Właściwości **krotki** wystąpienia są przeznaczone tylko do odczytu; kolekcje są niezmienne. W języku Visual Basic w spójnych kolekcjach i **ValueTuple** typy, pola krotki są odczytu i zapisu; kolekcje są modyfikowalna.

- Ogólny **krotki** typy są typami odwołań. Korzystanie z tych **krotki** typy oznacza, że alokacja obiektów. W ścieżkach, gorąca może to mieć zauważalnego wpływu na wydajność aplikacji. Krotek języka Visual Basic i **ValueTuple** typy są typami wartości.

Metody rozszerzające w <xref:System.TupleExtensions> klasy ułatwiają konwertowanie krotek języka Visual Basic .NET **krotki** obiektów. **ToTuple** metoda konwertuje krotki języka Visual Basic .NET **krotki** obiektu, a **ToValueTuple** metoda konwertuje .NET **krotki** obiekt do krotki języka Visual Basic.

Poniższy przykład tworzy spójną kolekcję, konwertuje go na .NET **krotki** obiektu i konwertuje je z powrotem do krotki języka Visual Basic. Przykład następnie porównuje ten krotki z oryginałem, aby upewnić się, że są równe.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka Visual Basic](index.md)  
