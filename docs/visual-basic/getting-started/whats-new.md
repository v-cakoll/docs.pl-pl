---
title: Nowości w języku Visual Basic
ms.date: 02/15/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0452a5dde3a266f5d50f69016eac8144bab9ba6
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="whats-new-for-visual-basic"></a>Nowości w języku Visual Basic

Ten temat zawiera listę nazw funkcji klucza dla każdej wersji programu Visual Basic z szczegółowe opisy nowych i ulepszonych funkcji w najnowsza wersja języka.
  
## <a name="current-version"></a>Bieżąca wersja

Visual Basic 15,5 cala   
W przypadku nowych funkcji, zobacz [15,5 cala Visual Basic](#visual-basic-155)

## <a name="previous-versions"></a>Poprzednie wersje

Visual Basic 15 ustęp 3   
W przypadku nowych funkcji, zobacz [15 ustęp 3 Visual Basic](#visual-basic-153)

2017 Visual Basic   
W przypadku nowych funkcji, zobacz [2017 Visual Basic](#visual-basic-2017)

Visual Basic / Visual Studio .NET 2015   
W przypadku nowych funkcji, zobacz [14 Visual Basic](#visual-basic-14)

Visual Basic / Visual Studio .NET 2013  
Podglądy technologii platformy kompilatora .NET ("Roslyn")

Visual Basic / Visual Studio .NET 2012   
`Async` i `await` słów kluczowych, Iteratory, caller — atrybuty informacji

Visual Basic, Visual Studio .NET 2010   
Właściwości zaimplementowane automatycznie, inicjatory kolekcji, kontynuacji wiersza niejawne, odchylenie dynamicznych, ogólny co/ma przeciwwskazań, dostępu globalnej przestrzeni nazw

Visual Basic / Visual Studio .NET 2008   
Język zintegrowane zapytania (LINQ), literałów XML, wnioskowanie o typie lokalnym, obiekt inicjatory, typy anonimowe, metody rozszerzenia, lokalnego `var` wnioskowanie o typie, wyrażenia lambda `if` operatora, metody częściowe, typy o wartości zerowalnej  

Visual Basic / Visual Studio .NET 2005   
`My` Typu i pomocnika typów (dostęp do aplikacji, komputera, systemu plików, sieci)

Visual Basic / Visual Studio .NET 2003   
Operatory przesunięcia bitowego, deklaracja zmiennej pętli

Visual Basic / Visual Studio .NET 2002   
Pierwszej wersji programu Visual Basic .NET

## <a name="visual-basic-155"></a>Visual Basic 15,5 cala

[Non końcowe nazwane argumenty](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

W Visual Basic 15 ustęp 3 i starszych wersjach gdy wywołanie metody uwzględnione argumentów zarówno według pozycji i według nazwy, argumenty pozycyjne musiał poprzedzać nazwane argumenty. Argumenty nazwane i pozycyjnych począwszy od 15,5 cala Visual Basic, może wystąpić w dowolnej kolejności, tak długo, jak wszystkie argumenty do ostatni argument pozycyjny są w poprawnej pozycji. Jest to szczególnie przydatne, gdy nazwane argumenty są używane, aby zwiększyć czytelność kodu.

Na przykład następujące wywołanie metody ma dwa argumenty pozycyjne między nazwany argument. Nazwany argument ułatwia wyczyść reprezentowany przez wartość 19 wieku.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

**Wiodący znak separatora hex/binary/ósemkowe**

Visual Basic 2017 dodano obsługę znaku podkreślenia (`_`) jako separator cyfr. Począwszy od 15,5 cala Visual Basic, można użyć znaku podkreślenia jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. W poniższym przykładzie użyto wiodące separator cyfr, aby zdefiniować 3,271,948,384 jako liczbę szesnastkową:

```vb
Dim number As Integer = &H_C305_F860
``` 
Aby użyć znaku podkreślenia jako separator początkowych, należy dodać następujący element do projektu Visual Basic (\*.vbproj) plików:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15 ustęp 3

[**Wnioskowanie spójnej kolekcji o nazwie**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Jeśli wartość krotki elementy z zmienne, Visual Basic wnioskuje nazwy elementów krotki z odpowiedniej nazwy zmiennych; nie trzeba jawnie nazwa element spójnej kolekcji. W poniższym przykładzie użyto wnioskowania do utworzenia spójnych kolekcji z trzy elementy o nazwie, `state`, `stateName`, i `capital`.

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Dodatkowe przełączniki kompilatora**  

Obsługuje teraz wiersza polecenia kompilatora Visual Basic [ **- refout** ](../reference/command-line-compiler/refout-compiler-option.md) i [ **- refonly** ](../reference/command-line-compiler/refonly-compiler-option.md) opcje kontroli dane wyjściowe kompilatora zestawy odwołań. **-refout** definiuje katalogu wyjściowego zestawu odwołania i **- refonly** Określa, że zestaw odwołania ma być danymi wyjściowymi kompilacji.

## <a name="visual-basic-2017"></a>2017 Visual Basic

[**Krotki**](../programming-guide/language-features/data-types/tuples.md)

Spójne kolekcje są lekkie danych struktury, która najczęściej służy do zwracania wiele wartości z wywołania pojedynczej metody. Zwykle zwracać wiele wartości z metody, należy wykonać jedną z następujących czynności:

- Definiowanie niestandardowego typu ( `Class` lub `Structure`). Jest to rozwiązanie ogromnych.

- Zdefiniuj co najmniej jeden `ByRef` parametrów, oprócz zwracanie wartości z metody.
 
Obsługa języka Visual Basic krotek pozwala szybko zdefiniować krotka, opcjonalnie przypisać semantycznego nazwy do jego wartości i szybko pobrać jego wartości. Poniższy przykład opakowuje wywołanie <xref:System.Int32.TryParse%2A> metodę i zwraca spójną kolekcję.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Można wywołać metody i obsługi zwrócony krotki z kodu podobne do następujących.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)] 

**Literały binarne i separatory cyfr**

Dane binarne literału można zdefiniować przy użyciu prefiksu `&B` lub `&b`. Ponadto można użyć znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności. W poniższym przykładzie użyto obie funkcje można przypisać `Byte` wartość i wyświetl ją jako liczbę dziesiętną szesnastkowe i binarnego.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Aby uzyskać więcej informacji, zobacz sekcję "Przypisania literału" [bajtów](../language-reference/data-types/byte-data-type.md#literal-assignments), [całkowitą](../language-reference/data-types/integer-data-type.md#literal-assignments), [długi](../language-reference/data-types/long-data-type.md#literal-assignments), [krótki](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte ](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [Uinteger —](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments), i [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) typów danych.

**Obsługa języka C# odwołanie zwracanych wartości**

Począwszy od C# 7, C# obsługuje odwołania może zwracać wartości. Oznacza to gdy wywołanie metody odbiera wartość zwracana przez odwołanie, można zmienić wartości odwołania. Visual Basic nie zezwala na utworzenia metod z odwołaniem zwracają wartości, ale pozwala ona do wykorzystania i zmodyfikować zwracanych wartości odwołania.

Na przykład następująca `Sentence` klasa napisane w języku C# zawiera `FindNext` metodę, która znajduje następny wyraz w zdaniu zaczyna się od wskazany podciąg. Jako wartość zwracana przez odwołanie i zostanie zwrócony ciąg `Boolean` zmiennej przekazywana przez odwołanie do metody wskazuje, czy wyszukiwanie zakończyła się powodzeniem. Oznacza to, że obiekt wywołujący nie może tylko odczytać zwrócona wartość; on również ją zmodyfikować, a tej zmiany jest widoczny w `Sentence` klasy.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

W najprostszej postaci można zmodyfikować wyraz znaleziony w zdaniu przy użyciu kodu podobne do następujących. Należy pamiętać, że nie przypisujesz wartość do metody, ale raczej wyrażenie zwraca metody, których to odwołanie, wartość zwracana.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Problem z tym kodem jest, że jeśli nie, metoda zwraca pierwsze słowo. Ponieważ przykładzie nie bada wartość `Boolean` argumentu, aby określić, czy dopasowanie zostanie znaleziony, modyfikuje pierwsze słowo, jeśli nie zostanie odnaleziony odpowiednik. Poniższy przykład poprawia to zastępując pierwsze słowo z samym sobą, jeśli nie Brak dopasowania.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Lepszym rozwiązaniem jest przy użyciu metody pomocnika, do której odwołanie wartość zwracana jest przekazywana przez odwołanie. Metoda pomocnika można następnie zmodyfikować argumentu przekazanego do niej przez odwołanie. Poniższy przykład robi to.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Aby uzyskać więcej informacji, zobacz [odwołania zwracać wartości](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[Nameof](../../csharp/language-reference/keywords/nameof.md)  
 Niekwalifikowane ciąg nazwę typu lub elementu członkowskiego do użycia w komunikacie o błędzie można uzyskać, bez twardych kodowanie ciągu.  Dzięki temu swój kod, aby pozostać poprawne podczas refaktoryzacji.  Ta funkcja jest również przydatne w przypadku podłączenia łącza MVC model-view-controller i wyzwalania zdarzenia zmiany właściwości.  
  
[Interpolacja ciągów](../../csharp/language-reference/keywords/interpolated-strings.md)  
 Wyrażenia parametrów interpolacji służy do tworzenia ciągów.  Wyrażenie ciągu interpolowanym wygląda jak ciąg szablonu, który zawiera wyrażenia.  Ciągu interpolowanym łatwiej zrozumieć względem argumentów niż [złożone formatowanie](../../standard/base-types/composite-format.md).  
  
[Dostęp do elementu członkowskiego warunkowe null i indeksowania](../../csharp/language-reference/operators/null-conditional-operators.md)  
Można sprawdzić wartość null w sposób składni bardzo małe przed wykonaniem dostępu elementu członkowskiego (`?.`) lub indeks (`?[]`) operacji.  Tych operatorów pomóc zapisu sprawdza mniej kod obsługujący wartości null, szczególnie w przypadku malejącej do struktur danych.  Jeśli Lewy argument operacji lub obiektu odwołanie ma wartość null, operacje zwraca wartość null.  
  
[Literały ciągu wiele wierszy](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 Literały ciągu może zawierać sekwencje znaków nowego wiersza.  Możesz już konieczne stary obejść użycia `<xml><![CDATA[...text with newlines...]]></xml>.Value`  
  
Komentarze  
Możesz umieścić komentarze po kontynuacje niejawne wiersza, wewnątrz wyrażenia inicjatora, jak i między LINQ wyrażeń.  
  
 Inteligentny rozdzielczość w pełni kwalifikowaną nazwę  
 Podany kod, takich jak `Threading.Thread.Sleep(1000)`, Visual Basic używaną do odszukania przestrzeni nazw "Wątkowość" odnajdywanie jest niejednoznaczny między System.Threading i System.Windows.Threading, a następnie składają raporty wystąpił błąd.  Visual Basic uwzględnia teraz obu tych możliwości przestrzeni nazw razem.  Jeśli występuje na liście uzupełniania, edytorze programu Visual Studio zawiera listę elementów członkowskich z obu typów na liście uzupełniania.  
  
 Literały daty pierwszej roku  
 Masz literały daty w formacie rrrr mm-dd `#2015-03-17 16:10 PM#`.  
  
 Właściwości tylko do odczytu — interfejs  
 Można wdrożyć tylko do odczytu właściwości interfejsu za pomocą właściwości odczytu i zapisu.  Interfejs gwarantuje minimalny zestaw funkcji, a nie zatrzymuje klasa implementująca z stosowanie ustawionej właściwości.  
  
 [TypeOf \<expr > IsNot \<typu >](../../visual-basic/language-reference/operators/typeof-operator.md)  
 Aby uzyskać więcej czytelność kodu, można teraz używać `TypeOf` z `IsNot`.  
  
 [Ostrzeżenie #Disable \<ID > i ostrzeżenie #Enable \<ID >](../../visual-basic/language-reference/directives/directives.md)  
 Można wyłączyć i Włącz określone ostrzeżenia dla regionów, w pliku źródłowym.  
  
 Ulepszenia komentarza dokumentu XML  
 Podczas zapisywania komentarze w dokumencie, Pobierz inteligentne edytora i Obsługa sprawdzania poprawności nazwy parametrów, odpowiednich Obsługa kompilacji `crefs` (Ogólne, operatory, itp.), kolorowanie i refaktoryzacji.  
  
 [Moduł częściowe i definicje interfejsu](../../visual-basic/language-reference/modifiers/partial.md)  
 Oprócz klas i struktur mogą zadeklarować częściowe moduły i interfejsów.  
  
 [#Region dyrektywy wewnątrz treści — metoda](../../visual-basic/language-reference/directives/region-directive.md)  
 Możesz też zaznaczyć #Region... ograniczniki #End Region w dowolnym miejscu w funkcjach, a nawet, dzieląc go w pliku funkcji jednostki.  
  
 [Definicje zastąpienia są niejawnie Overloads](../../visual-basic/language-reference/modifiers/overrides.md)  
 Jeśli dodasz `Overrides` modyfikator do definicji, kompilator niejawnie dodaje `Overloads` przypadków, w którym można wpisać wspólną mniejsza ilość kodu.  
  
 CObj w argumentach atrybutów dozwolone  
 Kompilator używać, aby zapewnić błąd, że CObj(...) nie jest stałą, gdy są używane w konstrukcji atrybutu.  
  
 Deklarowanie i korzystanie z metody niejednoznaczne z różnych interfejsów  
 Wcześniej następujący kod zwróciło błędy, które uniemożliwiały deklarowanie `IMock` lub z wywołaniem `GetDetails` (jeśli je zadeklarowano w języku C#):  
  
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
  
 Teraz kompilator użyje reguł rozwiązywania normalne przeciążenia wybranie najbardziej odpowiedniej `GetDetails` do wywołania, i można zadeklarować interfejsu relacje w języku Visual Basic, jak pokazano w przykładzie.  
  
## <a name="see-also"></a>Zobacz także  
 [Co to jest nowa w programie Visual Studio 2017 r.](/visualstudio/ide/whats-new-in-visual-studio)
