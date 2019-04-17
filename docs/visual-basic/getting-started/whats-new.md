---
title: Co nowego w języku Visual Basic
ms.date: 10/24/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
ms.openlocfilehash: 5b1547f596a0ff1c52a402f90457dced6ef604a0
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611799"
---
# <a name="whats-new-for-visual-basic"></a>Co nowego w języku Visual Basic

Ten temat zawiera listę nazw funkcji klucza dla każdej wersji programu Visual Basic z szczegółowe opisy nowych i ulepszonych funkcji w najnowszych wersjach języka.

## <a name="current-version"></a>Bieżąca wersja

Visual Basic należy zachować 15,8 / Visual Studio 2017 w wersji 15.8 dla nowych funkcji, zobacz [15.8 Visual Basic](#visual-basic-158)

## <a name="previous-versions"></a>Poprzednie wersje

Visual Basic 15.5 / Visual Studio 2017 w wersji 15.5 dla nowych funkcji, zobacz [15.5 Visual Basic](#visual-basic-155)

Visual Basic 15.3 / Visual Studio 2017 w wersji 15.3 dla nowych funkcji, zobacz [15.3 programu Visual Basic](#visual-basic-153)

Visual Basic 2017 / Visual Studio 2017 dla nowych funkcji, zobacz [2017 Visual Basic](#visual-basic-2017)

Visual Basic / Visual Studio 2015 r. Aby uzyskać nowe funkcje, zobacz [14 Visual Basic](#visual-basic-14)

Visual Basic / Visual Studio 2013 technologii zawiera wersje zapoznawcze platformy kompilatora .NET ("Roslyn")

Visual Basic / Visual Studio 2012 `Async` i `await` słów kluczowych, Iteratory, caller — atrybuty informacji

Visual Basic, Visual Studio 2010 automatycznie implementowanych właściwości, inicjatory kolekcji, niejawnej kontynuacji wiersza, dynamiczne, ogólna Company/ma przeciwwskazań wariancji, dostęp do globalnej przestrzeni nazw

Visual Basic / Visual Studio 2008 Language Integrated Query (LINQ), literałów XML, wnioskowanie o typie lokalnym, obiekt inicjatorów, typów anonimowych, metody rozszerzające, lokalnego `var` wnioskowanie, wyrażeń lambda, typu `if` operator częściowe metody, typy o wartości zerowalnej

Visual Basic / Visual Studio 2005 `My` typu i pomocnika typów (dostęp do aplikacji, komputer, system plików, użycia sieci)

Visual Basic / Visual Studio .NET 2003 Bit-shift — operatory pętli deklarację zmiennej

Visual Basic / Visual Studio .NET 2002 kanał pierwszego wydania programu Visual Basic .NET

## <a name="visual-basic-158"></a>Visual Basic 15.8

**Zoptymalizowane pod kątem zmiennoprzecinkowych, konwersja liczby całkowitej**

W poprzednich wersjach programu Visual Basic, konwersja [Double](../language-reference/data-types/double-data-type.md) i [pojedynczego](../language-reference/data-types/single-data-type.md) wartości liczb całkowitych oferowane stosunkowo niska wydajność. Podczas przekazywania wartości zwracanej przez dowolny z następujących metod do jednego z 15.8 Visual Basic znacznie zwiększa wydajność konwersje zmiennoprzecinkowe do liczb całkowitych [funkcje wewnętrzne konwersji liczby całkowitej w Visual Basic](../language-reference/functions/type-conversion-functions.md) () CByte CShort, CInt, CLng, CSByte, CUShort, CUInt, CULng), lub kiedy wartość zwracana przez dowolny z następujących metod jest niejawnie rzutowany na całkowite wpisz kiedy [Option Strict](~/docs/visual-basic/language-reference/statements/option-strict-statement.md) ustawiono `Off`:

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Tego rodzaju optymalizacji umożliwia kod wymagany do uruchomienia szybciej — maksymalnie dwa razy, jak szybko uzyskać kod, który obsługuje dużą liczbę konwersji na typy liczb całkowitych. W poniższym przykładzie pokazano niektóre wywołania prosta metoda, które dotyczą tego rodzaju optymalizacji:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174

```

Należy zwrócić uwagę na to, czy jest to obcina zamiast wartości zmiennoprzecinkowych Zaokrągla liczbę.

## <a name="visual-basic-155"></a>Visual Basic 15.5

[Argumenty nazwane inne niż końcowe](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

W wersji Visual Basic 15.3 i starszych wersjach gdy wywołanie metody uwzględniało argumenty zarówno według pozycji, jak i według nazwy, argumenty pozycyjne musiały poprzedzać argumenty nazwane. W wersji Visual Basic 15.5 i nowszych argumenty pozycyjne i argumenty nazwane mogą występować w dowolnej kolejności, pod warunkiem że wszystkie argumenty (do ostatniego argumentu pozycyjnego) znajdują się we właściwych pozycjach. Jest to szczególnie przydatne, gdy argumenty nazwane są stosowane w celu poprawy czytelności kodu.


Na przykład następujące wywołanie metody ma dwa argumenty pozycyjne, między argumentu nazwanego. Argument nazwany sprawia, że wyczyść wiek reprezentowany przez wartość 19.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected` Modyfikator dostępu elementu członkowskiego](../language-reference/modifiers/private-protected.md)

Ta nowa kombinacja — słowo kluczowe definiuje element członkowski, który jest dostępny, wszystkie elementy członkowskie w swojej klasie zawierający, a także typów pochodnych typu zawierającego klasy, ale tylko wtedy, gdy są one również znajdują się w zawierające zestaw. Ponieważ struktury nie może być dziedziczona, `Private Protected` może być stosowany tylko do składowych klasy.

**Wiodący znak separatora szesnastkowy/binarny/ósemkowy**

W wersji +Visual Basic 2017 dodano obsługę znaku podkreślenia (`_`) jako separatora cyfr. Począwszy od wersji Visual Basic 15.5, można używać znaku podkreślenia jako separatora wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi. W poniższym przykładzie użyto separatora wiodącego cyfr, aby zdefiniować liczbę 3 271 948 384 w postaci szesnastkowej:

```vb
Dim number As Integer = &H_C305_F860
```

Aby użyć znaku podkreślenia jako separatora wiodącego, należy dodać następujący element do pliku projektu Visual Basic (\*.vbproj):

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15.3

[**Wnioskowanie o nazwie krotki**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Gdy przypiszesz wartość elementów krotki ze zmiennych, Visual Basic wnioskuje nazwy elementów krotki z odpowiedniej nazwy zmiennych; nie trzeba jawnie nazwa elementu krotki. W poniższym przykładzie użyto wnioskowania, aby utworzyć krotki o trzy elementy o nazwie, `state`, `stateName`, i `capital`.

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Dodatkowe przełączniki kompilatora**

Visual Basic obsługuje teraz kompilatora wiersza polecenia [ **- opcji refout** ](../reference/command-line-compiler/refout-compiler-option.md) i [ **jest opcja refonly -** ](../reference/command-line-compiler/refonly-compiler-option.md) opcje kompilatora, aby kontrolować dane wyjściowe zestawy referencyjne. **-opcji refout** definiuje katalogu wyjściowego zestawu odwołania i **jest opcja refonly -** Określa, że zestaw odwołania na wyjściu przez kompilację.

## <a name="visual-basic-2017"></a>2017 Visual Basic

[**Tuples**](../programming-guide/language-features/data-types/tuples.md)

Kolekcje są uproszczone danych struktury, które najczęściej umożliwia zwracanie wielu wartości z pojedynczym wywołaniu metody. Zazwyczaj zwracanie wielu wartości z metody, należy wykonać jedną z następujących czynności:

- Definiowanie niestandardowego typu ( `Class` lub `Structure`). Jest to rozwiązanie niewielkich.

- Definiują jedną lub więcej `ByRef` parametry oprócz zwracanie wartości z metody.

Obsługa języka Visual Basic dla krotki pozwala szybko zdefiniować krotki, opcjonalnie przypisać nazwy semantycznego do jego wartości i szybko pobrać jego wartości. Poniższy przykład zawija wywołanie do <xref:System.Int32.TryParse%2A> metodę i zwraca spójną kolekcję.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Można następnie wywołać metodę i obsługiwać zwracane spójna kolekcja znajdująca się z kodem, jak pokazano poniżej.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**Literały binarne oraz separatory cyfr**

Plik binarny literału można zdefiniować przy użyciu prefiksu `&B` lub `&b`. Ponadto można użyć znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności. W poniższym przykładzie użyto obu funkcji, aby przypisać `Byte` wartość i wyświetlić go jako liczbę dziesiętną, szesnastkowym i binarny.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Aby uzyskać więcej informacji, zobacz sekcję "Przypisania literału" [bajtów](../language-reference/data-types/byte-data-type.md#literal-assignments), [całkowitą](../language-reference/data-types/integer-data-type.md#literal-assignments), [długie](../language-reference/data-types/long-data-type.md#literal-assignments), [krótki](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte ](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [Uinteger —](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments), i [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) typów danych.

[**Obsługa języka C# odwołanie zwracane wartości**](../programming-guide/language-features/procedures/ref-return-values.md)

Począwszy od języka C# 7.0, C# obsługuje odwołanie zwracane wartości. Oznacza to, że podczas wywoływania metody otrzymuje wartości zwracane przez odwołanie, można zmienić wartości odwołania. Visual Basic nie umożliwia utworzenia metody z odwołaniem do wartości zwracane, ale pozwala korzystać i modyfikować wartości zwracane odwołanie.

Na przykład następująca `Sentence` klasa napisane w języku C# zawiera `FindNext` metodę, która umożliwia znalezienie następnego wyrazu w zdaniu, zaczynającą się podanym podciągiem. Ten ciąg jest zwracany jako wartość zwracana przez odwołanie, a `Boolean` zmiennej przekazywany przez odwołanie do metody wskazuje, czy wyszukiwanie zakończyło się pomyślnie. Oznacza to, że wywołujący można nie tylko do odczytu zwrócona wartość; on również modyfikować go i modyfikacja tego znajduje odzwierciedlenie w `Sentence` klasy.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

W najprostszej postaci można zmodyfikować wyraz znaleziony w zdaniu przy użyciu kodu, jak pokazano poniżej. Należy pamiętać, że nie przypisujesz wartość do metody, ale raczej do wyrażenia, metoda zwraca odwołanie jest zwracają wartość.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Problem z tym kodem jest jednak to, że jeśli nie zostanie znalezione dopasowanie, metoda zwraca pierwszy wyraz. Ponieważ przykładu nie analizuje wartość `Boolean` argumentu, aby ustalić, czy zostanie znalezione dopasowanie, modyfikuje pierwszy wyraz, jeśli nie ma dopasowania. Poniższy przykład naprawia to przez zastąpienie pierwszy wyraz z samym sobą, jeśli nie ma dopasowania.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Lepszym rozwiązaniem jest użycie metody pomocnika, do której odwołanie wartość zwracana jest przekazywany przez odwołanie. Metoda pomocnika, następnie można zmodyfikować argumentu przekazanego do niej przez odwołanie. Poniższy przykład robi to.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Aby uzyskać więcej informacji, zobacz [odwołania Return Values](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic, 14

[Nameof](../../csharp/language-reference/keywords/nameof.md)

Można uzyskać nazwy niekwalifikowanej ciąg typu lub elementu członkowskiego do użytku w komunikacie o błędzie, bez twardych kodowanie ciągu.  Dzięki temu kodzie zachować poprawne podczas refaktoryzacji.  Ta funkcja jest również przydatne w przypadku Podłączanie łącza MVC model-view-controller i wyzwalanie zdarzenia zmiany właściwości.

[Interpolacja ciągów](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)

Wyrażenie interpolacji ciągu służy do konstruowania ciągów.  Wyrażenie ciągu interpolowanego wygląda jak ciąg szablonu, który zawiera wyrażenia.  Ciąg interpolowany łatwiej zrozumieć względem argumentów niż [formatowania złożonego](../../standard/base-types/composite-format.md).

[Dostęp do elementu członkowskiego warunkowe null i indeksowania](../language-reference/operators/null-conditional-operators.md)

Możesz sprawdzić o wartości null w sposób bardzo małe, składni przed wykonaniem dostęp do elementu członkowskiego (`?.`) lub indeksu (`?[]`) operacji.  Operatory te pomagają ograniczyć ilość kodu potrzebnego do sprawdzenia wystąpień wartości „null”, zwłaszcza w przypadku wchodzenia głębiej w struktury danych.  W przypadku o wartości null po lewej stronie operatora lub obiektu odwołania operacji zwraca wartość null.

[Literały ciągu wielowierszowy](../../visual-basic/programming-guide/language-features/strings/string-basics.md)

Literały ciągu może zawierać sekwencje nowego wiersza.  Możesz nie jest już konieczne starego obejść użycia `<xml><![CDATA[...text with newlines...]]></xml>.Value`

**Komentarze**

Po kontynuacji wiersza niejawne, wewnątrz wyrażenia inicjatora, a wśród warunki wyrażenia LINQ, można umieścić komentarze.

**Inteligentniejsze rozwiązania w pełni kwalifikowana nazwa**

Podany kod taki jak `Threading.Thread.Sleep(1000)`, Visual Basic, używany do wyszukiwania przestrzeni nazw "Wątkowości" odnajdywanie było niejednoznaczne między System.Threading i System.Windows.Threading, a następnie zgłaszanie błędu.  Visual Basic traktuje teraz zarówno możliwe przestrzenie nazw ze sobą.  Jeśli możesz wyświetlić na liście uzupełniania, Edytor programu Visual Studio Wyświetla listę elementów członkowskich z obu typów na liście uzupełniania.

**Literały daty pierwszego roku**

Masz literały daty w formacie rrrr mm-dd `#2015-03-17 16:10 PM#`.

**Właściwości interfejsu tylko do odczytu**

Można zaimplementować tylko do odczytu właściwości interfejsu przy użyciu właściwości odczytu i zapisu.  Interfejs gwarantuje minimalny zestaw funkcji, a nie zatrzymuje klasa implementująca z zezwalającej na właściwość należy ustawić.

[TypeOf \<expr > IsNot \<typ >](../../visual-basic/language-reference/operators/typeof-operator.md)

Aby uzyskać więcej czytelność kodu, można teraz używać `TypeOf` z `IsNot`.

[Ostrzeżenie #Disable \<ID > i ostrzeżenie #Enable \<identyfikator >](../../visual-basic/language-reference/directives/index.md)

Można wyłączyć i Włącz określone ostrzeżenia dotyczące regionów, w pliku źródłowym.

**Ulepszenia komentarzy dokumentacji XML**

Podczas pisania komentarzy dokumentacji, otrzymujesz Edytor smart i Obsługa sprawdzania poprawności nazwy parametrów, odpowiednich, Obsługa narzędzia build `crefs` (Ogólne, operatory, itp.), kolorowanie i refaktoryzacji.

[Definicje częściowe moduł i interfejsu](../../visual-basic/language-reference/modifiers/partial.md)

Oprócz klasy i struktury można zadeklarować moduły częściowe i interfejsy.

[Dyrektywy #Region wewnątrz treści metod](../../visual-basic/language-reference/directives/region-directive.md)

Możesz umieścić #Region... ograniczniki #End Region, w dowolnym miejscu pliku wewnątrz funkcji, a nawet, dzieląc go w funkcji jednostki.

[Definicje zastąpienia są niejawnie przeciążenia](../../visual-basic/language-reference/modifiers/overrides.md)

Jeśli dodasz `Overrides` modyfikator do definicji, kompilator niejawnie dodaje `Overloads` tak, aby mniejszej ilości kodu można wpisać w typowych przypadkach.

**CObj dozwolone w argumentach atrybutów**

Kompilator używać, aby zapewnić błąd, że CObj(...) nie jest stałą, gdy są używane w konstrukcji atrybutu.

**Deklarowanie i używanie niejednoznaczne metody z różnych interfejsów**

Wcześniej następujący kod zwróciło błędy, które uniemożliwiały deklarowanie `IMock` lub wywoływania `GetDetails` (jeśli zostały one zgłoszone w języku C#):

```vb
Interface ICustomer
  Sub GetDetails(x As Integer)
End Interface

Interface ITime
  Sub GetDetails(x As String)
End Interface

Interface IMock : Inherits ICustomer, ITime
  Overloads Sub GetDetails(x As Char)
End Interface

Interface IMock2 : Inherits ICustomer, ITime
End Interface
```

Teraz to kompilator użyje reguł rozwiązywania normalne przeciążenia wybranie najbardziej odpowiedniej `GetDetails` do wywołania, i można zadeklarować interfejsu relacje w języku Visual Basic, podobnie jak pokazano w przykładzie.

## <a name="see-also"></a>Zobacz także

- [Co nowego w programie Visual Studio 2017](/visualstudio/ide/whats-new-in-visual-studio)
