---
title: Co nowego w Visual Basic
ms.date: 10/24/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
ms.openlocfilehash: a9bac04a7839796229a2e1c61771ca32573f8fcd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374515"
---
# <a name="whats-new-for-visual-basic"></a>Co nowego w Visual Basic

Ten temat zawiera listę najważniejszych nazw funkcji dla każdej wersji Visual Basic z szczegółowymi opisami nowych i ulepszonych funkcji w najnowszych wersjach języka.

## <a name="current-version"></a>Bieżąca wersja

Visual Basic 16,0/Visual Studio 2019 wersja 16,0 \
Aby poznać nowe funkcje, zobacz [Visual Basic 16,0](#visual-basic-160).

## <a name="previous-versions"></a>Poprzednie wersje

Visual Basic 15,8/Visual Studio 2017 wersja 15,8 \
Aby poznać nowe funkcje, zobacz [Visual Basic 15,8](#visual-basic-158).

Visual Basic 15,5/Visual Studio 2017 wersja 15,5 \
Aby poznać nowe funkcje, zobacz [Visual Basic 15,5](#visual-basic-155).

Visual Basic 15,3/Visual Studio 2017 wersja 15,3 \
Aby poznać nowe funkcje, zobacz [Visual Basic 15,3](#visual-basic-153).

Visual Basic 2017/Visual Studio 2017 \
Aby poznać nowe funkcje, zobacz [Visual Basic 2017](#visual-basic-2017).

Visual Basic/Visual Studio 2015 \
Aby poznać nowe funkcje, zobacz [Visual Basic 14](#visual-basic-14).

Visual Basic/Visual Studio 2013 \
Wersje zapoznawcze technologii .NET Compiler Platform ("Roslyn")

Visual Basic/Visual Studio 2012 \
`Async`i `await` słowa kluczowe, Iteratory, atrybuty informacji o wywołującym

Visual Basic, Visual Studio 2010 \
Właściwości zaimplementowane przez autoimplementację, Inicjatory kolekcji, niejawne kontynuacja wiersza, dynamiczne, ogólne, proste/odchylenia, globalny dostęp do przestrzeni nazw

Visual Basic/Visual Studio 2008 \
Language Integrated Query (LINQ), literały XML, wnioskowanie typu lokalnego, Inicjatory obiektów, typy anonimowe, metody rozszerzające, `var` wnioskowanie typu lokalnego, wyrażenia lambda, `if` operator, metody częściowe, typy wartości null

Visual Basic/Visual Studio 2005 \
`My`Typ i typy pomocnika (dostęp do aplikacji, komputera, systemu plików, sieci)

Visual Basic/Visual Studio .NET 2003 \
Operatory przesunięcia bitowego, deklaracja zmiennej pętli

Visual Basic/Visual Studio .NET 2002 \
Pierwsze wydanie Visual Basic .NET

## <a name="visual-basic-160"></a>Visual Basic 16,0

Visual Basic 16,0 koncentruje się na dostarczaniu większej liczby funkcji środowiska uruchomieniowego Visual Basic (Microsoft. VisualBasic. dll) do programu .NET Core i to pierwsza wersja Visual Basic skoncentrowana na platformie .NET Core. Wiele części środowiska uruchomieniowego Visual Basic jest zależne od WinForms i zostaną dodane do nowszej wersji Visual Basic.

**Komentarze są dozwolone w większej liczbie miejsc w instrukcjach**

W Visual Basic 15,8 i wcześniejszych wersjach Komentarze są dozwolone tylko w pustych wierszach, na końcu instrukcji lub w określonych miejscach w instrukcji, w których niejawna kontynuacja wiersza jest dozwolona. Począwszy od Visual Basic 16,0, komentarze są również dozwolone po jawnej kontynuacji wiersza i wewnątrz instrukcji w wierszu rozpoczynającym się od znaku podkreślenia.

```vb
Public Sub Main()
    cmd.CommandText = ' Comment is allowed here without _
        "SELECT * FROM Titles JOIN Publishers " _ ' This is a comment
        & "ON Publishers.PubId = Titles.PubID " _
 _ ' This is a comment on a line without code
        & "WHERE Publishers.State = 'CA'"
End Sub
```

## <a name="visual-basic-158"></a>Visual Basic 15,8

**Optymalizacja konwersji zmiennoprzecinkowej na liczbę całkowitą**

W poprzednich wersjach Visual Basic konwersja wartości [podwójnej](../language-reference/data-types/double-data-type.md) i [pojedynczej](../language-reference/data-types/single-data-type.md) na liczbę całkowitą oferuje stosunkowo niską wydajność. Visual Basic 15,8 znacząco podnosi wydajność konwersji zmiennoprzecinkowych do liczb całkowitych, gdy przekazujesz wartość zwróconą przez dowolną z następujących metod do jednej z [funkcji konwersji wewnętrznej Visual Basic liczb całkowitych](../language-reference/functions/type-conversion-functions.md) (CByte, CShort, CInt, CLng, CSByte, CUShort, CUInt, CULng) lub gdy wartość zwrócona przez dowolną z następujących metod jest niejawnie rzutowana na typ całkowity, gdy [opcja Strict](../language-reference/statements/option-strict-statement.md) jest ustawiona na `Off` :

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

Ta optymalizacja umożliwia szybsze uruchamianie kodu — maksymalnie dwa razy w przypadku kodu, który wykonuje dużą liczbę konwersji na typy całkowite. Poniższy przykład ilustruje niektóre proste wywołania metod, których dotyczy ta Optymalizacja:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

Należy zauważyć, że to obcina zamiast zaokrąglania wartości zmiennoprzecinkowych.

## <a name="visual-basic-155"></a>Visual Basic 15,5

[Argumenty nazwane inne niż końcowe](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

W Visual Basic 15,3 i starszych wersjach, gdy wywołanie metody zawierało argumenty w obu położeniach i według nazwy, argumenty pozycyjne musiały poprzedzać nazwane argumenty. Począwszy od Visual Basic 15,5, argumenty pozycyjne i nazwane mogą pojawiać się w dowolnej kolejności, tak długo, jak wszystkie argumenty do ostatniego argumentu pozycyjnego znajdują się w poprawnej pozycji. Jest to szczególnie przydatne w przypadku, gdy nazwane argumenty są używane w celu łatwiejszego odczytywania kodu.

Na przykład następujące wywołanie metody ma dwa argumenty pozycyjne między nazwanym argumentem. Nazwany argument sprawia, że wartość 19 reprezentuje wiek.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected`Modyfikator dostępu składowej](../language-reference/modifiers/private-protected.md)

Ta nowa kombinacja słów kluczowych definiuje element członkowski, który jest dostępny dla wszystkich elementów członkowskich w jego klasie zawierającej, a także typów pochodzących od klasy zawierającej, ale tylko wtedy, gdy znajdują się one również w zawierającym go zestawie. Ponieważ struktury nie mogą być dziedziczone, `Private Protected` można je stosować tylko do elementów członkowskich klasy.

**Wiodący separator szesnastkowy/binarny**

Visual Basic 2017 dodano obsługę znaku podkreślenia ( `_` ) jako separatora cyfr. Począwszy od Visual Basic 15,5, można użyć znaku podkreślenia jako wiodącego separatora między cyframi prefiksu i szesnastkowym, dwójkowym lub ósemkowym. W poniższym przykładzie zastosowano wiodący separator cyfr, aby zdefiniować 3 271 948 384 jako liczbę szesnastkową:

```vb
Dim number As Integer = &H_C305_F860
```

Aby użyć znaku podkreślenia jako separatora wiodącego, należy dodać następujący element do pliku projektu Visual Basic ( \* vbproj):

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15,3

[**Wnioskowanie o nazwie krotki**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Podczas przypisywania wartości elementów krotki ze zmiennych, Visual Basic wnioskuje nazwę elementów krotki z odpowiednich nazw zmiennych; nie ma potrzeby jawnej nazwy elementu krotki. Poniższy przykład używa wnioskowania, aby utworzyć krotkę z trzema nazwanymi elementami, `state` , `stateName` i `capital` .

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Dodatkowe przełączniki kompilatora**

Kompilator wiersza polecenia Visual Basic obsługuje teraz opcje kompilatora [**-opcji refout**](../reference/command-line-compiler/refout-compiler-option.md) i [**-refonly**](../reference/command-line-compiler/refonly-compiler-option.md) , aby kontrolować dane wyjściowe zestawów referencyjnych. **-opcji refout** definiuje katalog wyjściowy zestawu referencyjnego i **-refonly** określa, że tylko zestaw odwołania ma być wyprowadzany przez kompilację.

## <a name="visual-basic-2017"></a>Visual Basic 2017

[**Krotki**](../programming-guide/language-features/data-types/tuples.md)

Krotki są prostą strukturą danych, najczęściej używaną do zwracania wielu wartości z pojedynczego wywołania metody. Zwykle, aby zwrócić wiele wartości z metody, należy wykonać jedną z następujących czynności:

- Zdefiniuj typ niestandardowy (a `Class` lub `Structure` ). Jest to bardzo ciężki rozwiązanie.

- Zdefiniuj co najmniej jeden `ByRef` parametr, oprócz zwracania wartości z metody.

Obsługa Visual Basic kroteks umożliwia szybkie Definiowanie krotek, opcjonalnie przypisanie nazw semantycznych do wartości i szybkie pobranie wartości. Poniższy przykład otacza wywołanie <xref:System.Int32.TryParse%2A> metody i zwraca spójną krotkę.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Następnie można wywołać metodę i obsłużyć zwróconą krotkę z kodem podobnym do poniższego.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**Literały binarne i separatory cyfr**

Można zdefiniować literał binarny przy użyciu prefiksu `&B` lub `&b` . Ponadto można użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność. Poniższy przykład używa obu funkcji do przypisywania `Byte` wartości i wyświetlania jej jako liczby dziesiętnej, szesnastkowej i binarnej.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Aby uzyskać więcej informacji, zobacz sekcję "przypisania literałów" dla typów danych [Byte](../language-reference/data-types/byte-data-type.md#literal-assignments), [Integer](../language-reference/data-types/integer-data-type.md#literal-assignments), [Long](../language-reference/data-types/long-data-type.md#literal-assignments), [SByte](../language-reference/data-types/sbyte-data-type.md#literal-assignments) [Short](../language-reference/data-types/short-data-type.md#literal-assignments), [UInteger —](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULONG](../language-reference/data-types/ulong-data-type.md#literal-assignments)i [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) .

[**Obsługa wartości zwracanych odwołań języka C#**](../programming-guide/language-features/procedures/ref-return-values.md)

Począwszy od języka C# 7,0, C# obsługuje wartości zwracane przez odwołanie. Oznacza to, że gdy metoda wywołująca otrzymuje wartość zwracaną przez odwołanie, może zmienić wartość odwołania. Visual Basic nie pozwala na tworzenie metod za pomocą zwracanych wartości, ale pozwala na używanie i modyfikowanie wartości zwracanych przez odwołanie.

Na przykład następująca `Sentence` Klasa zapisywana w języku C# zawiera `FindNext` metodę, która umożliwia znalezienie następnego wyrazu w zdaniu rozpoczynającym się od określonego podciągu. Ciąg jest zwracany jako wartość zwracana przez odwołanie, a `Boolean` zmienna przekazana przez odwołanie do metody wskazuje, czy wyszukiwanie zakończyło się pomyślnie. Oznacza to, że oprócz odczytywania zwracanej wartości, obiekt wywołujący może również go zmodyfikować, a modyfikacja jest odzwierciedlona w `Sentence` klasie.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

W najprostszej postaci można modyfikować wyraz znaleziony w zdaniu przy użyciu kodu, takiego jak poniższy. Zwróć uwagę, że nie przypiszesz wartości do metody, ale zamiast wyrażenia zwracanego przez metodę, która jest wartością zwracaną przez odwołanie.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Wystąpił problem z tym kodem, chociaż jest to, że jeśli dopasowanie nie zostanie znalezione, metoda zwraca pierwszy wyraz. Ponieważ przykład nie sprawdza wartości `Boolean` argumentu, aby określić, czy dopasowanie zostanie znalezione, modyfikuje pierwsze słowo, jeśli nie ma żadnego dopasowania. Poniższy przykład rozwiązuje ten problem, zastępując pierwszy wyraz własnym, jeśli nie ma żadnego dopasowania.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Lepszym rozwiązaniem jest użycie metody pomocnika, do której jest przenoszona wartość zwracana odwołania przez odwołanie. Metoda pomocnika może następnie zmodyfikować argument przesłany do niego przez odwołanie. W poniższym przykładzie jest to.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Aby uzyskać więcej informacji, zobacz [odwołania do zwracanych wartości](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[NameOf](../language-reference/operators/nameof.md)

Można uzyskać niekwalifikowaną nazwę ciągu typu lub składowej, która ma być używana w komunikacie o błędzie bez twardego kodowania ciągu.  Dzięki temu kod może pozostawać poprawny podczas refaktoryzacji.  Ta funkcja jest również przydatna w przypadku podłączania linków modelu MVC i kontrolera widoku oraz wyzwalania zdarzeń ze zmienionymi właściwościami.

[Interpolacja ciągów](../programming-guide/language-features/strings/interpolated-strings.md)

Do konstruowania ciągów można użyć wyrażeń interpolacji ciągów.  Wyrażenie interpolowane ciąg wygląda jak ciąg szablonu, który zawiera wyrażenia.  Ciąg interpolowany jest łatwiejszy do zrozumienia w odniesieniu do argumentów niż [formatowanie złożone](../../standard/base-types/composite-formatting.md).

[Dostęp warunkowy do elementu członkowskiego o wartości null i indeksowanie](../language-reference/operators/null-conditional-operators.md)

Można testować pod kątem wartości null w bardzo jasny sposób składni przed wykonaniem operacji dostępu do elementu członkowskiego ( `?.` ) lub indeksu ( `?[]` ).  Te operatory pomagają pisać mniej kodu do obsługi kontroli wartości null, szczególnie w przypadku malejących struktur danych.  Jeśli lewy operand lub odwołanie do obiektu ma wartość null, operacje zwracają wartość null.

[Wielowierszowe literały ciągów](../programming-guide/language-features/strings/string-basics.md)

Literały ciągu mogą zawierać sekwencje nowego wiersza.  Nie potrzebujesz już starego obejścia z używania`<xml><![CDATA[...text with newlines...]]></xml>.Value`

**Komentarze**

Komentarze można umieszczać po niejawnej kontynuacji wierszy, wewnątrz wyrażeń inicjatora i wśród postanowień wyrażenia LINQ.

**Inteligentniejsze w pełni kwalifikowane rozpoznawanie nazw**

Podany kod, taki jak `Threading.Thread.Sleep(1000)` , Visual Basic używany do wyszukiwania przestrzeni nazw "Threading", odkrywał, że był niejednoznaczny między system. Threading i system. Windows. Threading, a następnie zgłasza błąd.  Visual Basic teraz traktuje jednocześnie wszystkie możliwe przestrzenie nazw.  Jeśli zostanie wyświetlona lista uzupełniania, Edytor programu Visual Studio Wyświetla listę członków z obu typów na liście uzupełniania.

**Literały daty od początku roku**

Możesz mieć literały dat w formacie RRRR-MM-DD `#2015-03-17 16:10 PM#` .

**Właściwości interfejsu tylko do odczytu**

Właściwości interfejsu ReadOnly można zaimplementować przy użyciu właściwości ReadWrite. Interfejs gwarantuje minimalną funkcjonalność i nie zatrzymuje klasy implementującej, umożliwiając ustawienie właściwości.

[\<expr>IsNot typeof\<type>](../language-reference/operators/typeof-operator.md)

Aby zwiększyć czytelność kodu, można teraz użyć `TypeOf` programu z `IsNot` .

[Ostrzeżenie #Disable \<ID> i #Enable\<ID>](../language-reference/directives/index.md)

Można wyłączyć i włączyć określone ostrzeżenia dla regionów w pliku źródłowym.

**Ulepszenia komentarzy w dokumencie XML**

Podczas pisania komentarzy do dokumentu uzyskasz Inteligentny edytor i kompilację do walidacji nazw parametrów, prawidłowej obsługi `crefs` (typów ogólnych, operatorów itp.), kolorowania i refaktoryzacji.

[Częściowe definicje modułów i interfejsów](../language-reference/modifiers/partial.md)

Oprócz klas i struktur można zadeklarować częściowe moduły i interfejsy.

[Dyrektywy #Region wewnątrz treści metod](../language-reference/directives/region-directive.md)

Można umieścić #Region... #End ograniczników regionów w dowolnym miejscu w pliku, wewnątrz funkcji, a nawet w obrębie treści funkcji.

[Definicje zastąpień są niejawnie przeciążeń](../language-reference/modifiers/overrides.md)

Jeśli dodasz `Overrides` modyfikator do definicji, kompilator niejawnie doda, `Overloads` tak aby można było wpisać mniej kodu w typowych przypadkach.

**CObj dozwolone w argumentach atrybutów**

Kompilator używany do wydawania błędu, który CObj (...) nie był stałą, gdy jest używany w konstrukcjach atrybutu.

**Deklarowanie i używanie niejednoznacznych metod z różnych interfejsów**

Wcześniej Poniższy kod zgłosił błędy, które uniemożliwiły zadeklarowanie `IMock` lub wywołanie `GetDetails` (jeśli zostały zadeklarowane w języku C#):

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

Teraz kompilator będzie używać normalnych reguł rozpoznawania przeciążenia, aby wybrać najbardziej odpowiednie `GetDetails` do wywołania i można zadeklarować relacje interfejsu w Visual Basic jak te, które przedstawiono w przykładzie.

## <a name="see-also"></a>Zobacz też

- [Co nowego w programie Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017)
- [Co nowego w programie Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019)
