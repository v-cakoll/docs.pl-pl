---
title: Niezależność od języka i składniki niezależne od języka
description: Dowiedz się, jak można tworzyć w jednym z wielu języków obsługiwanych na platformie .NET, takich jak C#, C + +/ CLI, F#, IronPython, VB, Visual COBOL i programu PowerShell.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 40ba9b2dcc7321c81ee3f03112e677363c37a5f9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723312"
---
# <a name="language-independence-and-language-independent-components"></a>Niezależność od języka i składniki niezależne od języka

.NET jest niezależny od języka. Oznacza to, że jako deweloper możesz tworzyć w jednym z wielu języków, których platformą docelową implementacje platformy .NET, takich jak C#, F#i Visual Basic. Dostępne typy i członków bibliotek klas opracowanych dla implementacji platformy .NET, bez znajomości języka, w którym zostały one pierwotnie napisane i bez konieczności którąkolwiek z Konwencji języka oryginału. Jeśli jesteś deweloperem składnika, dostęp do danego składnika jest możliwy przez dowolną aplikację platformy .NET, niezależnie od języka.

> [!NOTE]
> To pierwsza część w tym artykule omówiono tworzenie składników niezależnych od języka — czyli składników, które mogą być używane przez aplikacje napisane w dowolnym języku. Można również utworzyć pojedynczy składnik lub aplikację z kodu źródłowego napisanego w wielu językach; zobacz [współdziałanie między językami](#cross-language-interoperability) w drugiej części tego artykułu.

Pełna interakcja z innymi obiektami napisanymi w dowolnym języku, obiekty muszą ujawnić obiektom wywołującym tylko te funkcje, które są wspólne dla wszystkich języków. Ten wspólny zestaw funkcji jest zdefiniowany przez Common Language Specification (CLS), czyli zestaw reguł, które dotyczą generowanych zestawów. Specyfikacja Common Language Specification jest zdefiniowana w partycji I i klauzulach od 7 do 11 [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Jeśli składnik jest zgodny ze specyfikacją języka wspólnego, może być zgodne ze specyfikacją CLS i jest możliwy z kodu w zestawach napisanych w dowolnym języku programowania, który obsługuje specyfikację CLS. Można określić, czy składnika jest zgodny ze specyfikacją języka wspólnego w czasie kompilacji, stosując [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutu do kodu źródłowego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute).

W tym artykule:

* [Reguły zgodności ze specyfikacją CLS](#cls-compliance-rules)

    * [Typy i podpisy typu członka](#types-and-type-member-signatures)

    * [Konwencje nazewnictwa](#naming-conventions)

    * [Konwersja typu](#type-conversion)

    * [Tablice](#arrays)

    * [Interfejsy](#interfaces)

    * [Wyliczenia](#enumerations)

    * [Ogólnie rzecz biorąc wpisz członków](#type-members-in-general)

    * [Ułatwienia dostępu członków](#member-accessibility)

    * [Typy ogólne i członkowie](#generic-types-and-members)

    * [Konstruktory](#constructors)

    * [Właściwości](#properties)

    * [Zdarzenia](#events)

    * [Overloads](#overloads)

    * [Wyjątki](#exceptions)

    * [Atrybuty](#attributes)

* [Atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute)

* [Współdziałanie między językami](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>Reguły zgodności ze specyfikacją CLS

W tej sekcji omówiono zasady tworzenia składników zgodnych ze specyfikacją CLS. Aby uzyskać pełną listę reguł, patrz część I, klauzula 11 dokumentu [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Specyfikacja Common Language Specification omawia każdą regułę pod kątem zgodności ze specyfikacją CLS, ma zastosowanie do konsumentów (deweloperzy, którzy programowo uzyskują dostęp do składnika, który jest zgodny ze specyfikacją CLS), struktur (deweloperzy, którzy używają kompilatora języka do utworzenia CLS-compliant biblioteki) i extenderów (deweloperzy, którzy tworzą narzędzia, takie jak kompilator języka lub parser kodu tworzący składniki zgodne ze specyfikacją CLS). W tym artykule koncentruje się na reguły, ponieważ mają one zastosowanie do struktur. Należy pamiętać, że niektóre z reguł, które są stosowane do urządzeń Extender mogą dotyczyć także zestawów, które są tworzone przy użyciu [Reflection.Emit](xref:System.Reflection.Emit).

Aby zaprojektować składnik, który jest niezależny od języka, wystarczy zastosować reguły zgodności ze specyfikacją CLS interfejsu publicznego danego składnika. Implementacja prywatna nie musi być zgodna ze specyfikacją.

> [!IMPORTANT]
> Reguły zgodności ze specyfikacją CLS dotyczą tylko publicznego interfejsu składnika, aby nie jego prywatnej implementacji.

Na przykład niepodpisane liczby całkowite inne niż [bajtów](xref:System.Byte) nie są zgodne ze specyfikacją CLS. Ponieważ `Person` klasy w poniższym przykładzie ujawnia `Age` właściwości typu [UInt16](xref:System.UInt16), poniższy kod wyświetla ostrzeżenie kompilatora.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge
      End Get
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

Możesz wprowadzić zgodne ze specyfikacją CLS klasy osoby, zmieniając typ `Age` właściwość `UInt16` do [Int16](xref:System.Int16), który jest zgodny ze specyfikacją CLS, 16-bitowa liczba całkowita ze znakiem. Nie trzeba zmieniać typu prywatnego `personAge` pola.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)
      End Get
   End Property
End Class
```

Publiczny interfejs biblioteki składa się z następujących czynności:

* Definicje klas publicznych.

* Definicje publicznych członków klas publicznych oraz definicje członków dostępnych dla klas pochodnych (czyli chronionych elementów członkowskich).

* Parametry i zwracane typy metod publicznych klas publicznych oraz parametry i zwracane typy metod w klasach pochodnych.

W poniższej tabeli wymieniono reguły zgodności ze specyfikacją CLS. Tekst reguł jest pobierany dosłownie z [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), Copyright 2012 by Ecma International. W poniższych sekcjach znajduje się bardziej szczegółowe informacje dotyczące tych zasad.

Kategoria | Zobacz | Reguła | Numer reguły
-------- | --- | ---- | -----------
Ułatwienia dostępu | [Ułatwienia dostępu członków](#member-accessibility) | Nie powinna być zmieniana dostępność, podczas zastępowania dziedziczonych metod, z wyjątkiem sytuacji, gdy zastępowania metody dziedziczonej z innego zestawu o dostępności `family-or-assembly`. W tym przypadku zastąpienie musi mieć poziom dostępności `family`. | 10
Ułatwienia dostępu | [Ułatwienia dostępu członków](#member-accessibility) | Widoczność i dostępność typów i elementów członkowskich jest taka, że typy w podpisie dowolnego elementu członkowskiego są widoczne i dostępne zawsze, gdy sam element członkowski jest widoczny i dostępny. Na przykład metoda publiczna, która jest widoczna spoza jej zestawu nie mają argumentem, którego typ jest widoczny tylko w obrębie zestawu. Widoczność i dostępność typów tworzących typ ogólny z wystąpieniami używany w podpisie dowolnego elementu członkowskiego jest widoczny i dostępny zawsze, gdy sam element członkowski jest widoczny i dostępny. Na przykład skonkretyzowany typ ogólny obecny w podpisie elementu członkowskiego, który jest widoczny na zewnątrz zestawu nie posiada argument rodzajowy, którego typ jest widoczny tylko w obrębie zestawu. | 12
Tablice | [Tablice](#arrays) | Tablice powinny zawierać elementy o typie zgodnym ze specyfikacją CLS, a wszystkie wymiary tablicy powinny mieć dolne granice równe zero. Tylko fakt, że element jest tablicą i typem elementu tablicy jest wymagany dla rozróżnienia między przeciążeniami. Kiedy przeciążenie opiera się na dwóch lub większej liczbie typów tablicy typy elementu muszą być typami nazwanymi. | 16
Atrybuty | [Atrybuty](#attributes) | Atrybuty powinny być typu [klasy System.Attribute](xref:System.Attribute), lub typu z niego dziedziczącego. | 41
Atrybuty | [Atrybuty](#attributes) | Specyfikacja CLS zezwala tylko na podzestaw kodowań atrybutów niestandardowych. Jedyne typy, które mają się pojawiać w tych kodowaniach to (zobacz część IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [ System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), i Typ wyliczeniowy oparty na zgodny ze specyfikacją CLS podstawowym typie integer. | 34
Atrybuty | [Atrybuty](#attributes) | Specyfikacja CLS nie zezwala na Modyfikatory widoczne publicznie (`modreq`, zob. partycja II), ale zezwala na Modyfikatory opcjonalne (`modopt`, zob. partycja II) nie rozumie. | 35
Konstruktorów | [Konstruktory](#constructors) | Konstruktor obiektu musi wywołać konstruktora pewnego wystąpienia klasy podstawowej zanim nastąpi dostęp do danych wystąpienia dziedziczonego. (To nie dotyczy typów wartości, które nie wymagają konstruktorów.)  | 21
Konstruktorów | [Konstruktory](#constructors) | Konstruktor obiektu nie będzie wywoływany z wyjątkiem jako część tworzenia obiektu i obiekt nie może być inicjowany dwukrotnie. | 22
Wyliczenia | [Wyliczenia](#enumerations) | Podstawowym typem wyliczenia będzie wbudowany typ liczby całkowitej ze specyfikacją CLS, nazwy pola będzie "value__" i pole to będzie oznakowane `RTSpecialName`. |  7
Wyliczenia | [Wyliczenia](#enumerations) | Istnieją dwa odrębne rodzaje wyliczeń, wskazywane przez obecność lub Brak [System.FlagsAttribute](xref:System.FlagsAttribute) atrybut niestandardowy (zobacz Biblioteka partycja IV). Reprezentuje nazwane wartości liczb całkowitych; inne reprezentuje nazwane flagi bitowe, które mogą być połączone do generowania wartości nienazwanej. Wartość `enum` nie jest ograniczona do określonej wartości. |  8
Wyliczenia | [Wyliczenia](#enumerations) | Literał statycznego pola elementu enum ma typ wyliczenia Enum. |  9
Zdarzenia | [Zdarzenia](#events) | Metody, które implementują zdarzenie to będzie oznakowane `SpecialName` w metadanych. |29
Zdarzenia | [Zdarzenia](#events) | Dostępności zdarzenia i jego metod dostępu muszą być identyczne. |30
Zdarzenia | [Zdarzenia](#events) | `add` i `remove` metody dla zdarzenia muszą być obecne lub nieobecne. |31
Zdarzenia | [Zdarzenia](#events) | `add` i `remove` metody zdarzenia powinny uwzględniać jeden parametr, którego typ definiuje typ zdarzenia i musi pochodzić z [System.Delegate](xref:System.Delegate). |32
Zdarzenia | [Zdarzenia](#events) | Zdarzenia powinny przestrzegać określonego wzorca nazewnictwa. Atrybut jako SpecialName określone w regule CLS 29 będzie ignorowany w odpowiednich porównaniach nazw i będzie stosować się do reguł identyfikatorów.  |33
Wyjątki | [Wyjątki](#exceptions) | Obiekty, które są generowane powinny być typu [System.Exception](xref:System.Exception) lub typu z niego dziedziczącego. Niemniej jednak metody ze specyfikacją CLS nie muszą blokować propagacji innych typów wyjątków. | 40
Ogólne | [Reguły zgodności ze specyfikacją CLS](#cls-compliance-rules) | Zasady CLS dotyczą tylko tych części typu, które są dostępne lub widoczne poza zestawem. | 1
Ogólne | [Reguły zgodności ze specyfikacją CLS](#cls-compliance-rules) | Członkowie typów zgodnych ze specyfikacją CLS nie jest oznaczony zgodne ze specyfikacją CLS. | 2
Typy ogólne | [Typy ogólne i członkowie](#generic-types-and-members) | Zagnieżdżone typy muszą mieć przynajmniej tyle parametrów ogólnych, co typ otaczający. Parametry ogólne w typie zagnieżdżonym odpowiadają według pozycji parametrom ogólnym w jego typie otaczającym.  | 42
Typy ogólne | [Typy ogólne i członkowie](#generic-types-and-members) | Nazwa typu ogólnego koduje liczbę parametrów typu zadeklarowanej dla typu niezagnieżdżonego, lub nowo wprowadzonego typu, jeśli jest zagnieżdżony, zgodnie z zasadami określonymi powyżej. | 43
Typy ogólne | [Typy ogólne i członkowie](#generic-types-and-members) | Typ ogólny powinien ponownie deklarować ograniczenia wystarczające do zagwarantowania, że wszelkie ograniczenia typu podstawowego lub interfejsów będą spełnione przez ograniczenia typu ogólnego. | 44
Typy ogólne | [Typy ogólne i członkowie](#generic-types-and-members) | Typy używane jako warunki ograniczające w parametrach ogólnych powinny być zgodne ze specyfikacją CLS. | 45
Typy ogólne | [Typy ogólne i członkowie](#generic-types-and-members) | Widoczność i dostępność elementów członkowskich (w tym typów zagnieżdżonych) w skonkretyzowanym typie ogólnym są uznawane za objętą zakresem konkretyzacji niż deklaracją typu ogólnego jako całości. Tak zakładając, reguły widoczności i dostępności reguły CLS 12 nadal mają zastosowanie. | 46
Typy ogólne | [Typy ogólne i członkowie](#generic-types-and-members) | Dla każdej abstrakcyjnej lub standardowej wirtualnej metody jest domyślny konkretnych implementacji (nieabstrakcyjna) | 47
Interfejsy | [Interfejsy](#interfaces) | Interfejsy zgodne ze specyfikacją CLS nie wymaga definicji metod zgodne ze specyfikacją CLS w celu ich wdrożenia. | 18
Interfejsy | [Interfejsy](#interfaces) | Interfejsy zgodne ze specyfikacją CLS nie mogą definiować metod statycznych ani nie mogą definiować pól. | 19
Elementy członkowskie | [Ogólnie rzecz biorąc wpisz członków](#type-members-in-general) | Globalne statyczne pola i metody nie są zgodne ze specyfikacją CLS. | 36
Elementy członkowskie | -- | Wartość literału statycznego jest określana za pomocą metadanych inicjowania pola. Zgodne ze specyfikacją CLS literał musi mieć wartość określoną w metadanych inicjalizacji pola, który ma ten sam typ, co literał (lub typu podstawowego, jeśli ten literał jest `enum`). | 13
Elementy członkowskie | [Ogólnie rzecz biorąc wpisz członków](#type-members-in-general) | Ograniczenie vararg nie jest częścią specyfikacji CLS, a jedyną Konwencją wywoływania obsługiwaną przez specyfikację CLS jest standardowa zarządzana Konwencja wywoływania. | 15
Konwencje nazewnictwa | [Konwencje nazewnictwa](#naming-conventions) | Zestawy postępuje zgodnie z załącznikiem 7 z technicznego raportu 15 standardy Unicode Standard3.0 regulującego zestaw znaków do rozpoczynać i znajdować się w identyfikatorach, dostępne online pod [form normalizacji Unicode](https://www.unicode.org/unicode/reports/tr15/tr15-18.html). Identyfikatory powinny być w formacie kanonicznym, zdefiniowane przez formularz normalizacji Unicode C. Ze względów ze specyfikacją CLS dwa identyfikatory są takie same, jeśli ich mapowania na małe litery (określone przez Unicode mapowania na małe litery niewrażliwość na ustawienia regionalne, jeden do jednego) są takie same. Oznacza to, że dwa identyfikatory uważane za różne w ramach CLS są różnią się tylko w ich przypadku. Jednak aby można było przesłonić dziedziczonej definicji interfejsu wiersza polecenia wymaga precyzyjnego kodowania pierwotnej deklaracji. | 4
Przeciążenie | [Konwencje nazewnictwa](#naming-conventions) | Wszystkie nazwy wprowadzone w zakresie zgodnym ze specyfikacją CLS są różne, niezależnie od rodzaju, z wyjątkiem sytuacji, w których nazwy są identyczne i rozpoznawane przez przeciążenie. Oznacza to gdy CTS pozwala jeden typ używał tej samej nazwy dla metody, pola, specyfikacja CLS nie zezwala. | 5
Przeciążenie | [Konwencje nazewnictwa](#naming-conventions) | Pola i zagnieżdżone typy powinny wyróżniać się przez porównanie identyfikatorów, mimo że CTS pozwala odróżniać odrębne podpisy. Metody, właściwości i zdarzenia, które mają taką samą nazwę (przez porównanie identyfikatorów), może różnić się więcej niż tylko zwracanym typem, z wyjątkiem określonych w zasadzie 39 CLS | 6
Przeciążenie | [Overloads](#overloads) | Tylko właściwości i metody mogą być przeciążone. | 37
Przeciążenie | [Overloads](#overloads) |Właściwości i metody mogą być przeciążone, oparte tylko na liczbie i rodzaju ich parametrów, z wyjątkiem operatorów konwersji o nazwie `op_Implicit` i `op_Explicit`, które również mogą być przeciążone oparciu o ich typ zwrotu. | 38
Przeciążenie | -- | Jeśli dwa lub więcej metod zgodnych ze specyfikacją CLS zadeklarowane w typie mają taką samą nazwę, dla określonego zestawu wystąpień typu mają ten sam parametr i zwracane typy, następnie wszystkie te metody są semantycznie równoważne w tych wystąpieniach typów. | 48
Właściwości | [Właściwości](#properties) | Metody, które implementują metody getter i setter właściwości to będzie oznakowane `SpecialName` w metadanych. | 24
Właściwości | [Właściwości](#properties) | Metod dostępu do właściwości musza być statyczne, wirtualne lub być wystąpieniem. | 26
Właściwości | [Właściwości](#properties) | Typ właściwości jest zwracany typ metody pobierającej oraz typ ostatniego argumentu metody ustawiającej. Typy parametrów właściwości powinny być typami z parametrami metody pobierającej oraz typami wszystkich parametrów poza ostatnim metody ustawiającej. Wszystkie te typy są zgodne ze specyfikacją CLS i nie może być zarządzanymi wskaźnikami (czyli nie mogą być przekazywane przez odwołanie). | 27
Właściwości | [Właściwości](#properties) | Właściwości powinny przestrzegać określonego wzorca nazewnictwa. `SpecialName` Określone w regule CLS 24 atrybut będzie ignorowany w odpowiednich porównaniach nazw i będzie stosować się do reguł identyfikatorów. Właściwość musi posiadać metodę getter i/lub metoda ustawiająca. | 28
Konwersja typu | [Konwersja typu](#type-conversion) | Jeśli podano op_implicit — lub op_explicit — dostarcza alternatywny sposób wymuszenia. | 39
Types | [Typy i podpisy typu członka](#types-and-type-member-signatures) | Spakowane typy wartości nie są zgodne ze specyfikacją CLS. | 3
Types | [Typy i podpisy typu członka](#types-and-type-member-signatures) | Wszystkie typy pojawiające się w podpisie jest zgodny ze specyfikacją CLS. Wszystkie typy tworzące typ ogólny jest zgodny ze specyfikacją CLS. | 11
Types | [Typy i podpisy typu członka](#types-and-type-member-signatures) | Wpisane odwołania nie są zgodne ze specyfikacją CLS. | 14
Types | [Typy i podpisy typu członka](#types-and-type-member-signatures) | Typy wskaźników niezarządzanych nie są zgodne ze specyfikacją CLS. | 17
Types | [Typy i podpisy typu członka](#types-and-type-member-signatures) | Zgodne ze specyfikacją CLS klasy, typy wartości i interfejsy nie wymagają wdrażania członków niezgodnych-ze specyfikacją CLS | 20
Types | [Typy i podpisy typu członka](#types-and-type-member-signatures) | [System.Object](xref:System.Object) jest zgodny ze specyfikacją CLS. Inne klasy zgodne ze specyfikacją CLS musi dziedziczyć od zgodne ze specyfikacją CLS klasy. | 23

### <a name="types-and-type-member-signatures"></a>Typy i podpisy typu członka

[System.Object](xref:System.Object) typ jest zgodny ze specyfikacją CLS i jest typem podstawowym wszystkich typów obiektów w systemie typów środowiska .NET Framework. Dziedziczenie w .NET Framework jest niejawne (na przykład [ciąg](xref:System.String) klasa dziedziczy niejawnie z `Object` klasy) lub jawny (na przykład [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) klasa dziedziczy jawnie z [ArgumentException](xref:System.ArgumentException) klasy, która dziedziczy jawnie [wyjątek](xref:System.Exception) klasy. Typ pochodny był zgodny ze specyfikacją CLS jego typ podstawowy również musi być zgodny ze specyfikacją CLS.

Poniższy kod przedstawia typ pochodny, którego typ podstawowy nie jest zgodny ze specyfikacją CLS. Definiuje podstawę `Counter` klasę korzystającą z liczbą całkowitą bez znaku 32-bitowych jako licznika. Ponieważ klasa oferuje funkcje licznika dzięki zawijaniu liczbą całkowitą bez znaku, klasa jest oznaczona jako zgodna ze specyfikacją niezgodne ze specyfikacją. W rezultacie Klasa pochodna, `NonZeroCounter`, również jest zgodny ze specyfikacją CLS.

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)]
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return String.Format("{0}). ", ctr);
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment()
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return String.Format("{0}). ", ctr)
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant
'    because it derives from 'Counter', which is not CLS-compliant.
'
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

Wszystkie typy, które pojawiają się w podpisach członków, łącznie z typem zwracania metody lub typem właściwości musi być zgodny ze specyfikacją CLS. Dodatkowo dla typów ogólnych:

* Wszystkie typy tworzące typ ogólny muszą być zgodne ze specyfikacją CLS.

* Wszystkie typy używane jako warunki ograniczające w parametrach rodzajowych musi być zgodny ze specyfikacją CLS.

.NET [wspólny system typów](common-type-system.md) obejmują szereg wbudowanych typów, które są obsługiwane bezpośrednio przez środowisko uruchomieniowe języka wspólnego i są specjalnie kodowane w metadanych zestawu. Z tych typów wewnętrznyc typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS.

Typ zgodny ze specyfikacją CLS | Opis
------------------ | -----------
[Byte](xref:System.Byte) | 8-bitowej nieoznaczonej liczby całkowitej
[Int16](xref:System.Int16) | 16-bitową
[Int32](xref:System.Int32) | 32-bitową
[Int64](xref:System.Int64) | 64-bitową
[Single](xref:System.Single) | Wartość zmiennoprzecinkowa o pojedynczej precyzji
[Double](xref:System.Double) | Wartość zmiennoprzecinkowa o podwójnej precyzji
[Boolean](xref:System.Boolean) | Typ wartości true lub false
[Char](xref:System.Char) | Jednostka zakodowany kodu UTF-16
[Decimal](xref:System.Decimal) | Liczba dziesiętna non--liczba zmiennoprzecinkowa
[IntPtr](xref:System.IntPtr) | Wskaźnik lub uchwyt rozmiaru zdefiniowanej platformy
[Ciąg](xref:System.String) | Zbiór zero, jeden lub więcej obiektów Char

Typy wewnętrzne wymienione w poniższej tabeli nie są zgodne ze specyfikacją CLS.

Typ niezgodny | Opis | Alternatywa zgodna ze specyfikacją CLS
------------------ | ----------- | -------------------------
[SByte](xref:System.SByte) | Typ danych 8-bitową | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16-bitowej nieoznaczonej liczby całkowitej | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32-bitowej nieoznaczonej liczby całkowitej | [Int64](xref:System.Int64)
[UInt64 —](xref:System.UInt64) | 64-bitowej nieoznaczonej liczby całkowitej | [Int64](xref:System.Int64) (możliwe przepełnienie), [BigInteger](xref:System.Numerics.BigInteger), lub [Double](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | Nieoznaczony wskaźnik lub uchwyt | [IntPtr](xref:System.IntPtr)

Biblioteka klas programu .NET Framework lub inne biblioteki klas może zawierać inne typy, które nie są zgodne ze specyfikacją CLS; na przykład:

* Spakowane typy wartości. Następujące C# przykład tworzy klasę, która ma właściwość publiczną typu `int`* o nazwie `Value`. Ponieważ `int`* jest typem wartości spakowanej, kompilator oznacza go jako zgodny ze specyfikacją niezgodne ze specyfikacją.

```csharp
using System;

[assembly:CLSCompliant(true)]

public unsafe class TestClass
{
   private int* val;

   public TestClass(int number)
   {
      val = (int*) number;
   }

   public int* Value {
      get { return val; }
   }
}
// The compiler generates the following output when compiling this example:
//        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
```

* Odwołania typizowane to specjalne konstrukty zawierające odwołanie do obiektu i odwołanie do typu.

Jeśli typ nie jest zgodny ze specyfikacją CLS, należy zastosować [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutem *isCompliant* parametru z wartością `false` do niego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute) sekcji.

Poniższy przykład ilustruje problem zgodności ze specyfikacją CLS w podpisie metody i w tworzeniu wystąpienia typu ogólnego. Definiuje on `InvoiceItem` klasę z właściwością typu [UInt32](xref:System.UInt32), właściwość typu [Nullable (z UInt32)](xref:System.Nullable%601)i konstruktora z parametrami typu `UInt32` i `Nullable(Of UInt32)`. Otrzymujemy cztery ostrzeżenia kompilatora podczas próby skompilowania tego przykładu.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As UInteger
      Get
         Return invId
      End Get
      Set
         invId = value
      End Set
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'
'       Public Property InvoiceId As UInteger
```

Aby wyeliminować ostrzeżenia kompilatora, Zamień typy zgodne ze specyfikacją niezgodne ze specyfikacją w `InvoiceItem` interfejsu publicznego zgodnych typów:

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set {
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As Integer
      Get
         Return CInt(invId)
      End Get
      Set
         invId = CUInt(value)
      End Set
   End Property
End Class
```

Oprócz określonych typów wymienionych niektóre kategorie typów nie są zgodne ze specyfikacją CLS. Należą do nich typy wskaźników niezarządzanych i typy wskaźników funkcji. Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej do utworzenia tablicy liczb całkowitych.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

Klasy abstrakcyjne dla zgodne ze specyfikacją CLS (to znaczy klas oznaczonych jako `abstract` w C#), wszystkie elementy członkowskie klasy, również musi być zgodny ze specyfikacją CLS.

### <a name="naming-conventions"></a>Konwencje nazewnictwa

Ponieważ w niektórych językach programowania jest rozróżniana wielkość liter, identyfikatory (takie jak nazwy przestrzeni nazw, typy i członkowie) muszą różnić się przez więcej niż wielkością liter. Dwa identyfikatory są uważane za równoważne, jeżeli ich mapowania na małe litery są takie same. Poniższy przykład C# definiuje dwie klasy publiczne, `Person` i `person`. Ponieważ różnią się tylko wielkością liter, kompilator języka C# oznacza je jako niezgodne ze specyfikacją CLS.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

Programowanie identyfikatorów języka, takich jak nazwy przestrzeni nazw, typów i członków, musi być zgodna z [Unicode Standard 3.0, 15 raportów technicznych, załącznika 7](https://www.unicode.org/reports/tr15/tr15-18.html). Oznacza to, że:

* Pierwszy znak identyfikatora może być dowolnego Unicode wielką literą, małą literą, literą, literą modyfikatora, inną literą lub znakiem liczby. Aby uzyskać informacji na temat kategorii znaków Unicode, zobacz [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) wyliczenia.

* Kolejne znaki mogą należeć do dowolnej kategorii jako pierwszego znaku i mogą również obejmować nierozdzielające, odstępy, łączenie znaków, liczby dziesiętne, znaki rozdzielające łącznika i kody formatowania.

Przed porównaniem identyfikatorów, należy odfiltrować kody formatowania i dokonać konwersji identyfikatorów do formularza normalizacji Unicode C, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu zakodowane UTF-16. Sekwencje znaków, które generują te same jednostki kodu w formularzu C normalizacji Unicode nie są zgodne ze specyfikacją CLS. Poniższy przykład definiuje właściwość o nazwie `Å`, która składa się ze znaku ANGSTROM SIGN (U + 212B), i drugą właściwość o nazwie `Å` która składa się ze znaku LATIN CAPITAL LETTER A WITH RING ABOVE (U + 00 C 5). C# Kompilator oznacza kod źródłowy jako zgodny ze specyfikacją niezgodne ze specyfikacją.

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set
          a1 = value
       End Set
   End Property

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'
'       Public Property Å As Double
'                       ~
```

Nazwy elementów członkowskich z określonego zakresu (np. obszary nazw w zestawie, typy w przestrzeni nazw lub członków w ramach danego typu) muszą być unikatowe, z wyjątkiem nazw, które są rozpoznawane przez przeciążenie. Wymóg ten jest bardziej rygorystyczny niż wspólny system typów umożliwia członkom wielu w zakresie miało identyczne nazwy, tak długo, jak są one różnych rodzajów elementów członkowskich (na przykład jeden jest metodą i inny jest polem). W szczególności dla członków typu:

* Pola i zagnieżdżone typy są rozróżniane według nazwy samodzielnie.

* Metody, właściwości i zdarzenia, które mają taką samą nazwę muszą różnić się przez więcej niż tylko zwracanym typem.

Poniższy przykład ilustruje wymaganie, że nazwy elementów członkowskich musi być unikatowa w obrębie swojego zakresu. Definiuje klasę o nazwie `Converter` zawierającej czterech członków o nazwie `Conversion`. Trzy to metody, a jedna jest właściwością. Metoda, która obejmuje `Int64` parametr ma unikatową nazwę, ale dwie metody z `Int32` parametru są, ponieważ wartość zwracana nie jest uważany za część podpisu elementu członkowskiego. `Conversion` Właściwości również narusza to wymaganie, ponieważ właściwości nie może mieć taką samą nazwę jak metody przeciążone.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }
}
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get
   End Property
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double'
'                    and 'Public Function Conversion(number As Integer) As Single' cannot
'                    overload each other because they differ only by return types.
'
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function
'                     Conversion(number As Integer) As Single' in this class.
'
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

Poszczególne języki obejmują unikatowe słowa kluczowe, więc języki przeznaczone środowiska uruchomieniowego języka wspólnego muszą również zapewnić pewien mechanizm dla odwoływania się do identyfikatorów (takich jak nazwy typu), które pokrywają się ze słowami kluczowymi. Na przykład `case` jest słowem kluczowym w językach C# i Visual Basic. Jednak w poniższym przykładzie w języku Visual Basic jest w stanie odróżnić klasę o nazwie `case` z `case` — słowo kluczowe przy użyciu otwierających i zamykających nawiasów klamrowych. W przeciwnym razie przykład komunikat o błędzie, "Słowo kluczowe nie jest prawidłowe jako identyfikator" i kompilacja nie powiedzie się.

```vb
Public Class [case]
   Private _id As Guid
   Private name As String

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name
   End Sub

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

Następujące C# przykład jest w stanie utworzyć `case` przy użyciu symbol @ do odróżnić identyfikator od słowa kluczowego języka. Bez tego kompilator języka C# będzie wyświetlane dwa komunikaty o błędach, "Oczekiwano typu" i "wyrażeniu występuje nieprawidłowe określenie"case"."

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a>Konwersja typu

Specyfikacja Common Language Specification definiuje dwa operatory konwersji:

* `op_Implicit`, który jest wykorzystywany do poszerzenia konwersje, nie powodują utraty danych lub precyzji. Na przykład [dziesiętna](xref:System.Decimal) struktura zawiera przeciążony `op_Implicit` operatora, aby konwertować wartości typów całkowitych i [Char](xref:System.Char) wartości `Decimal` wartości.

* `op_Explicit`, które są wykorzystywane przy zawężaniu zakresu konwersje, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub dokładności. Na przykład `Decimal` struktura zawiera przeciążony `op_Explicit` operatora konwersji [Double](xref:System.Double) i [pojedynczego](xref:System.Single) wartości `Decimal` i konwertowania `Decimal` wartości wartości całkowitych, `Double`, `Single`, i `Char`.

Jednak nie wszystkie języki obsługują przeciążanie operatora lub definicję niestandardowych operatorów. Jeśli użytkownik chce zaimplementować te operatory konwersji, należy także podać alternatywny sposób wykonania konwersji. Firma Microsoft zaleca, aby zapewnić `From`Xxx i `To`metody Xxx.

Poniższy przykład definiuje zgodne ze specyfikacją CLS Konwersje jawne i niejawne. Tworzy `UDouble` klasa, która reprezentuje podpisaną podwójnej precyzji liczby zmiennopozycyjnej. Rozporządzenie to przewiduje niejawną konwersję z `UDouble` do `Double` i jawne konwersje z `UDouble` do `Single`, `Double` do `UDouble`, i `Single` do `UDouble`. Umożliwia on również definiowanie `ToDouble` metodę jako alternatywa dla operatora niejawnej konwersji i `ToSingle`, `FromDouble`, i `FromSingle` metody jako alternatywy dla operatora konwersji jawnej.

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue)
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function
End Structure
```

### <a name="arrays"></a>Tablice

Tablice zgodne ze specyfikacją CLS są zgodne z następującymi zasadami:

* Wszystkie wymiary tablicy muszą mieć dolną granicę równą zero. Poniższy przykład tworzy tablicę ze specyfikacją CLS niezgodne ze specyfikacją z dolną granicą równą jeden. Należy pamiętać, że, mimo obecności [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutu, kompilator nie może wykryć czy tablica zwrócona przez `Numbers.GetTenPrimes` metoda nie jest zgodny ze specyfikacją CLS.

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6);
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr;
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* Wszystkie elementy tablicy musi składać się z typów zgodnych ze specyfikacją CLS. W poniższym przykładzie zdefiniowano dwie metody, które zwracają tablice zgodne ze specyfikacją niezgodne ze specyfikacją. Pierwsza zwraca tablicę [UInt32](xref:System.UInt32) wartości. Druga zwraca [obiektu](xref:System.Object) tablicy, która obejmuje [Int32](xref:System.Int32) i `UInt32` wartości. Mimo że kompilator identyfikuje pierwszą tablicę jako niezgodną z powodu jego `UInt32` typu, nie rozpoznaje, że druga tablica zawiera elementy inne niż zgodne ze specyfikacją CLS.

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```

* Rozdzielczość przeciążenia dla metod, które mają parametry tablicy jest opiera się na fakcie, że są to tablice i na ich typie elementu. Z tego powodu następujące definicja przeciążonej `GetSquares` metodą jest zgodny ze specyfikacją CLS.

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]);
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr];

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr)))
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr)
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a>Interfejsy

Interfejsy zgodne ze specyfikacją CLS można zdefiniować właściwości, zdarzenia i metody wirtualne (metody bez wdrażania). Zgodne ze specyfikacją CLS interfejs nie może zawierać żadnych z następujących czynności:

* Metody statyczne lub pola statyczne. C# Kompilator generuje błędy kompilatora, jeśli zdefiniujesz członka statycznego w interfejsie.

* Pola. C# Kompilator generuje błędy kompilatora, jeśli zdefiniujesz pole w interfejsie.

* Metody, które nie są zgodne ze specyfikacją CLS. Na przykład następująca definicja interfejsu zawiera metodę `INumber.GetUnsigned`, która jest oznaczona jako niezgodna-ze specyfikacją CLS. Ten przykład generuje ostrzeżenie kompilatora.

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a
    '    CLS-compliant interface.
    '
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  Z powodu działania tej reguły typy zgodne ze specyfikacją CLS nie muszą Implementuj składowe zgodne ze specyfikacją niezgodne ze specyfikacją. Jeśli platforma zgodna ze specyfikacją CLS udostępnia klasę, która implementuje interfejs zgodne ze specyfikacją CLS, powinno dodatkowo dostarczać konkretnych implementacji wszystkich członków innych niż zgodne ze specyfikacją CLS.

Kompilatory języka zgodne ze specyfikacją CLS muszą również pozwalać, aby klasa zapewniała oddzielne implementacje członków, którzy mają taką samą nazwę i podpis w wielu interfejsach. C#obsługuje jawnych implementacji interfejsu, aby zapewnić różne implementacje metod o identycznej nazwie. Poniższy przykład ilustruje ten scenariusz, definiując `Temperature` klasę, która implementuje `ICelsius` i `IFahrenheit` interfejsów jako jawne implementacje interfejsu.

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   }

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   }
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a>Wyliczenia

Wyliczenia zgodne ze specyfikacją CLS muszą wykonać następujące czynności:

* Podstawowym typem wyliczenia musi być typu integer zgodnym ze specyfikacją CLS wewnętrzne ([bajtów](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), lub [Int64](xref:System.Int64)). Na przykład, poniższy kod próbuje zdefiniować wyliczenie, którego podstawowym typem jest [UInt32](xref:System.UInt32) i generuje ostrzeżenie kompilatora.

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint {
        Unspecified = 0,
        XSmall = 1,
        Small = 2,
        Medium = 3,
        Large = 4,
        XLarge = 5
    };

    public class Clothing
    {
        public string Name;
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* Typ wyliczenia musi posiadać jedno pole wystąpienia o nazwie `Value__` oznaczona za pomocą `FieldAttributes.RTSpecialName` atrybutu. Dzięki temu można odwoływać się niejawnie do wartości pola.

* Wyliczenie zawiera pola statyczne literału o typach jest zgodny z typem samego wyliczenia. Na przykład, jeśli zdefiniujesz `State` wyliczenie z wartościami `State.On` i `State.Off`, `State.On` i `State.Off` są statycznymi polami literału, którego typem jest `State`.

* Istnieją dwa rodzaje wyliczeń:

    * Wyliczenie, które reprezentuje zestaw wzajemnie się wykluczających, nazwanych wartości całkowitych. Ten typ wyliczenia jest oznaczany przez brak z [System.FlagsAttribute](xref:System.FlagsAttribute) atrybutu niestandardowego.

    * Wyliczenie, które reprezentuje zestaw flag bitowych, które można połączyć do generowania wartości nienazwanej. Ten typ wyliczenia jest wskazywane przez obecność [System.FlagsAttribute](xref:System.FlagsAttribute) atrybutu niestandardowego.

 Aby uzyskać więcej informacji, zobacz dokumentację dla [wyliczenia](xref:System.Enum) struktury.

* Wartość wyliczenia nie jest ograniczona do zakresu jego określonych wartości. Innymi słowy zakres wartości wyliczenia to zakres wartości bazowej. Możesz użyć `Enum.IsDefined` metodę, aby określić, czy określona wartość jest członkiem wyliczenia.

### <a name="type-members-in-general"></a>Ogólnie rzecz biorąc wpisz członków

Specyfikacja Common Language Specification wymaga wszystkich pól i metod, które były dostępne jako elementy członkowskie określonej klasy. Dlatego globalne pola i metody statyczne (czyli pola statyczne lub metody, które są definiowane niezależnie od typu) nie są zgodne ze specyfikacją CLS. Jeśli próbujesz dołączyć globalne pole lub metodę w kodzie źródłowym C# kompilator generuje błąd kompilatora.

Specyfikacja Common Language Specification obsługuje tylko standardową konwencję wywoływania zarządzanego. Nie obsługuje on konwencji wywoływania niezarządzanego i metod ze zmiennym argumentem list oznaczonych `varargs` — słowo kluczowe. W przypadku listy zmiennych argumentów, które są zgodne ze standardową konwencją zarządzanego wywoływania użyj [ParamArrayAttribute](xref:System.ParamArrayAttribute) atrybutu lub implementacji konkretnego języka, takich jak `params` — słowo kluczowe w C# i `ParamArray` — słowo kluczowe w języku Visual Basic.

### <a name="member-accessibility"></a>Ułatwienia dostępu członków

Zastępowanie dziedziczonego członka nie można zmienić dostępności tego członka. Na przykład publiczną metodę w klasie bazowej nie może być zastąpiona przez prywatną metodę w klasie pochodnej. Istnieje jeden wyjątek: `protected internal` (w języku C#) lub `Protected Friend` (w języku Visual Basic) elementu członkowskiego w jednym zestawie, który jest zastępowany przez typ w innym zestawie.  W tym przypadku dostępnośc zastąpienia jest `Protected`.

Poniższy przykład ilustruje błąd, który jest generowany, jeśli [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) ma ustawioną wartość atrybutu `true`, i `Person`, która jest klasą pochodną `Animal`, próbuje zmienić dostępność `Species` właściwości z publicznej na prywatną. Przykład pomyślnie wykonuje kompilację po zmianie jego dostępności na publiczną.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species
   {
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;
   }
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species
   {
      get { return base.Species; }
   }

   public override string ToString()
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species
   End Function
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
'
'         Private Overrides ReadOnly Property Species As String
```

Typy w podpisie elementu członkowskiego musi być dostępny zawsze, gdy członek jest dostępny. Na przykład oznacza to, że publiczny członek nie może zawierać parametru, którego typ jest prywatny, chroniony lub wewnętrzny. Poniższy przykład ilustruje błąd kompilatora, który występuje, gdy `StringWrapper` konstruktora klasy uwidacznia wewnętrzną `StringOperationType` wartości wyliczenia, która określa, jak powinna być otoczona wartość ciągu.

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {
      if (type == StringOperationType.Normal) {
         useSB = false;
      }
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder()
         useSB = True
      End If
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a>Typy ogólne i członkowie

Zagnieżdżone typy zawsze mieć przynajmniej tyle parametrów ogólnych, co ich typ otaczający. Odpowiadają one według pozycji parametrom ogólnym w typie otaczającym. Typ ogólny może również zawierać nowe parametry ogólne.

Relacja między parametrów typu ogólnego dla typu zawierającego i jego typów zagnieżdżonych może być ukryta przez składnię poszczególnych języków. W poniższym przykładzie typ rodzajowy `Outer<T>` zawiera dwie klasy zagnieżdżonych, `Inner1A` i `Inner1B<U>`. Wywołania `ToString` metody, która każda klasa dziedziczy `Object.ToString`, pokazują, że każda klasa zagnieżdżona zawiera parametry typu klasy zawierającej.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

Nazwy typów ogólnych zakodowane są w formie *nazwa*"*n*, gdzie *nazwa* jest nazwą typu *`* jest znak literału, i *n* jest liczbą parametrów zadeklarowanych w typie lub dla zagnieżdżonych typów ogólnych, liczba nowo wprowadzonych parametrów typu. To kodowanie nazw typu ogólnego jest przydatne głównie dla deweloperów, którzy używają odbicia do dostępu do typów ogólnych zgodnych ze specyfikacją CLS w bibliotece.

Jeżeli ograniczenia są stosowane jako ogólnego typu, wszystkie typy używane jako ograniczenia również muszą być zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano klasę o nazwie `BaseClass` to znaczy nie zgodne ze specyfikacją CLS i klasę ogólną o nazwie `BaseCollection` której parametr typu musi pochodzić od klasy `BaseClass`. Ale ponieważ `BaseClass` nie jest zgodny ze specyfikacją CLS, kompilator generuje ostrzeżenie.

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}


public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class


Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not
'    CLS-compliant.
'
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

Jeśli typ ogólny jest pochodną ogólnego typu podstawowego, musi redeklarować wszelkie ograniczenia tak, aby mógł zagwarantować, że spełnione są również ograniczenia dotyczące typu podstawowego. W poniższym przykładzie zdefiniowano `Number<T>` reprezentujące dowolnego typu liczbowego. Umożliwia on również definiowanie `FloatingPoint<T>` klasy, która reprezentuje zmiennoprzecinkową wartości. Jednakże, kod źródłowy nie zostanie skompilowany, ponieważ nie ma zastosowania ograniczenia na `Number<T>` (że T musi być typem wartości) do `FloatingPoint<T>`.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T>
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
// The attempt to compile the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

Przykład pomyślnie wykonuje kompilację ograniczenie zostanie dodane do `FloatingPoint<T>` klasy.

```csharp
using System;

[assembly:CLSCompliant(true)]


public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
```

Specyfikacja Common Language Specification nakłada wystąpienia Konserwatywny model dla typów zagnieżdżonych i chronionych elementów członkowskich. Otwarte typy ogólne nie mogą ujawnić pól ani członków z podpisami, zawierającymi określone podczas tworzenia wystąpienia zagnieżdżonego, chronionego typu ogólnego. Typy nieuniwersalne, rozszerzające możliwości określonego wystąpienia rodzajowego klasy podstawowej lub interfejsu nie mogą ujawnić pól ani członków z podpisami, zawierającymi różne wystąpienia zagnieżdżonego, chronionego typu ogólnego.

W poniższym przykładzie zdefiniowano typ ogólny, `C1<T>`i klasę chronioną `C1<T>.N`. `C1<T>` posiada dwie metody, `M1` i `M2`. Jednak `M1` nie jest zgodny ze specyfikacją CLS, ponieważ próbuje zwrócić `C1<int>.N` obiektu z `C1<T>`. Druga klasa `C2`, jest tworzony na podstawie `C1<long>`. Posiada dwie metody `M3` i `M4`. `M3` nie jest zgodny ze specyfikacją CLS, ponieważ próbuje zwrócić `C1<int>.N` obiektu z podklasy `C1<long>`. Należy pamiętać, że Kompilatory języka mogą być jeszcze bardziej restrykcyjne. W tym przykładzie Visual Basic wyświetli błąd przy próbie kompilacji `M4`.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T>
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long>
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T)
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages


   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long)
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)
   End Sub
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace
'    '<Default>' through class 'C1'.
'
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because
'    it is 'Protected'.
'
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'
'                             ~~~~~~~~~~~~~~~~
'
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'
'       Protected Sub M4(n As C1(Of Long).N)
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a>Konstruktorów

Konstruktory w klasach zgodnych ze specyfikacją CLS i struktury, należy wykonać następujące czynności:

* Konstruktor klasy pochodnej musi wywołać konstruktora wystąpienia klasy podstawowej zanim uzyskuje dostęp do danych wystąpienia dziedziczonego. Ten wymóg jest fakt, że Konstruktory klasy bazowej nie są dziedziczone przez ich klasy pochodne. Ta zasada nie ma zastosowania do struktur, które nie obsługują bezpośredniego dziedziczenia.

  Zazwyczaj kompilatory wymuszają tę regułę niezależnie od zgodności ze specyfikacją CLS, co ilustruje poniższy przykład. Tworzy `Doctor` klasy, która jest pochodną `Person` klasy, ale `Doctor` klasy nie wywoła `Person` Konstruktor klasyinicjuje pola wystąpień.

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName
    {
        get { return fName; }
    }

    public string LastName
    {
        get { return lName; }
    }

    public string Id
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName,
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName,
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '
    '       Public Sub New()
    '                  ~~~
    ````

* Nie można wywołać konstruktora obiektu z wyjątkiem tworzenia obiektu. Ponadto nie można zainicjować obiektu dwa razy. Oznacza to, że na przykład `Object.MemberwiseClone` nie mogą wywoływać konstruktorów.

### <a name="properties"></a>Właściwości

Właściwości typów zgodnych ze specyfikacją CLS muszą wykonać następujące czynności:

* Właściwość musi posiadać setter i/lub metody pobierającej. W zestawie są one implementowane jako specjalne metody, co oznacza, że pojawią się one jako odrębne metody (metoda pobierająca o nazwie `get` \_ *propertyname* i metoda ustawiająca o `set` \_ *propertyname*) oznaczone jako `SpecialName` w metadanych zestawu. C# Kompilator wymusza tę regułę automatycznie, bez potrzeby stosowania <xref:System.CLSCompliantAttribute> atrybutu.

* Typ właściwości jest zwracany typ metody pobierającej oraz typ ostatniego argumentu metody ustawiającej. Te typy muszą być zgodne ze specyfikacją CLS i argumentów nie można przypisać do właściwości przez odwołanie (oznacza to, nie mogą być wskaźnikami zarządzanymi).

* Jeśli właściwość jest zarówno metody pobierającą i ustawiającą, obie muszą być wirtualne, statyczne lub wystąpieniami. C# Kompilator automatycznie wymuszają tę regułę poprzez składnię definicji właściwości.

### <a name="events"></a>Zdarzenia

Zdarzenie jest definiowane przez nazwę i jej typu. Typ zdarzenia jest delegat, który jest używany do wskazania zdarzenia. Na przykład `DbConnection.StateChange` zdarzenie jest typu `StateChangeEventHandler`. Oprócz samego zdarzenia trzy metody z nazwami na podstawie nazwy zdarzenia zapewniają implementację zdarzenia i są oznaczone jako `SpecialName` w metadanych zestawu:

* Metoda dodawania programu obsługi zdarzeń o nazwie `add`_*EventName*. Na przykład metoda subskrypcji zdarzeń dla `DbConnection.StateChange` nosi nazwę zdarzeń `add_StateChange`.

* Metoda usuwania programu obsługi zdarzeń o nazwie `remove`_*EventName*. Na przykład metoda usuwania dla `DbConnection.StateChange` nosi nazwę zdarzeń `remove_StateChange`.

* Metoda wskazywania, że zdarzenie nastąpiło, o nazwie `raise` \_ *EventName*.

> [!NOTE]
> Większość zasad specyfikacji języka wspólnego dotyczących zdarzeń jest implementowanych przez Kompilatory języka i są niewidoczne dla deweloperów składników.

Metody dodawania, usuwania i wywoływania zdarzenia muszą mieć identyczną dostępność. Wszystkie one muszą również mieć statyczne, wystąpienie, lub wirtualnych. Metody dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia. Metody dodawania i usuwania muszą być obie obecne lub nieobecne.

W poniższym przykładzie zdefiniowano klasę zgodne ze specyfikacją CLS, o nazwie `Temperature` która zgłasza `TemperatureChanged` zdarzeń, jeśli zmiana temperatury między dwoma odczytami jest równa lub przekracza wartość progową. `Temperature` Jawnie definiuje klasę `raise_TemperatureChanged` metodę, tak że można selektywnie wykonywać procedury obsługi zdarzeń.

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp;
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   }

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   }

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance)
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return;

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub
End Class
```

### <a name="overloads"></a>Overloads

Specyfikacja Common Language Specification nakłada następujące wymagania na przeciążone elementy członkowskie:

* Elementy Członkowskie mogą być przeciążane na podstawie liczby parametrów i typ każdego parametru. Konwencja wywoływania, typ zwracany, Modyfikatory niestandardowe stosowane dla metody lub jej parametrów i tego, czy parametry są przekazywane przez wartość lub przez odwołanie nie są uwzględniane przy rozróżnianiu poszczególnych przeciążeń. Aby uzyskać przykład, zobacz kod dla wymogu, że nazwy muszą być unikatowe w obrębie zakresu w [konwencje nazewnictwa](#naming-conventions) sekcji.

* Tylko właściwości i metody mogą być przeciążone. Pola i zdarzenia nie mogą być przeciążone.

* Metody ogólne mogą być przeciążane na podstawie liczby ich parametrów ogólnych.

> [!NOTE]
> `op_Explicit` i `op_Implicit` operatory są wyjątki od reguły, które zwracają wartość nie jest uważana za część podpisu metody w przypadku rozpoznawania przeciążenia. Te dwa operatory mogą być przeciążone dla obu swoich parametrów i ich wartości zwracanej.

### <a name="exceptions"></a>Wyjątki

Obiekty wyjątków muszą pochodzić z [System.Exception](xref:System.Exception) lub z innych typów pochodzących od `System.Exception`. Poniższy przykład ilustruje błąd kompilatora, która powstaje, gdy klasa niestandardowa o nazwie `ErrorClass` służy do obsługi wyjątków.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

Aby naprawić ten błąd `ErrorClass` musi dziedziczyć klasy `System.Exception`. Ponadto właściwości komunikatu musi zostać zastąpiona. Poniższy przykład usuwa te błędy, aby zdefiniować `ErrorClass` klasę, która jest zgodna ze specyfikacją CLS.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a>Atrybuty

Zestawy w zestawach.NET Framework, atrybuty niestandardowe zapewniają rozszerzony mechanizm do przechowywania atrybutów niestandardowych i pobierania metadanych dotyczących obiektów, takich jak zestawy, typy, elementy członkowskie i parametry metody programowania. Atrybuty niestandardowe muszą pochodzić z [klasy System.Attribute](xref:System.Attribute) lub typ pochodzący od `System.Attribute`.

Poniższy przykład narusza tę regułę. Definiuje on `NumericAttribute` klasę, która nie pochodzi od `System.Attribute`. Należy zauważyć, że błąd kompilatora powstaje tylko kiedy innych niż zgodne ze specyfikacją CLS jest stosowany, nie wtedy, gdy klasa jest zdefiniowana.

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)]
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it
'    does not inherit from 'System.Attribute'.
'
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

Konstruktor lub właściwości atrybutu zgodne ze specyfikacją CLS mogą uwidaczniać tylko następujące typy:

* [Boolean](xref:System.Boolean)

* [Byte](xref:System.Byte)

* [Char](xref:System.Char)

* [Double](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Single](xref:System.Single)

* [Ciąg](xref:System.String)

* [Typ](xref:System.Type)

* Każdy typ wyliczenia o typie podstawowym `Byte`, `Int16`, `Int32`, lub `Int64`.

W poniższym przykładzie zdefiniowano `DescriptionAttribute` klasę pochodzącą od [atrybutu](xref:System.Attribute). Konstruktor klasy ma parametr typu `Descriptor`, więc klasa nie jest zgodny ze specyfikacją CLS. Należy pamiętać, że C# kompilator emituje ostrzeżenie, ale kompiluje pomyślnie.

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description;
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d;
   }

   public Descriptor Descriptor
   { get { return desc; } }
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType
   Public Description As String
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get
         Return desc
      End Get
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a>Atrybut CLSCompliantAttribute

[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybut jest używany do wskazania, czy element programu jest zgodny z Common Language Specification. `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` Konstruktora zawiera jeden parametr wymagany *isCompliant*, która wskazuje, czy element programu jest zgodne ze specyfikacją CLS.

W czasie kompilacji kompilator wykrywa niezgodne elementy, które jest uważana za zgodny ze specyfikacją CLS i emituje ostrzeżenie. Kompilator nie generuje ostrzeżeń dotyczących typów ani elementów członkowskich, które są jawnie zadeklarowane jako niezgodne.

Deweloperzy składników mogą użyć `CLSCompliantAttribute` atrybutu na dwa sposoby:

* Aby zdefiniować części interfejsu publicznego udostępnianego przez składnik, które są zgodne ze specyfikacją CLS i części, które nie są zgodne ze specyfikacją CLS. Jeśli ten atrybut jest używany do oznaczania elementów konkretnego programu jako zgodne ze specyfikacją CLS, posługiwanie się nim gwarantuje, że te elementy są dostępne we wszystkich językach i narzędzia, które obsługują program .NET Framework.

* Aby upewnić się, że interfejs publiczny biblioteki składników udostępnia tylko te elementy programu, które są zgodne ze specyfikacją CLS. Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory zasadniczo generują ostrzeżenie.

> [!WARNING]
> W niektórych przypadkach Kompilatory języka wymuszają reguły zgodne ze specyfikacją CLS, niezależnie od tego, czy `CLSCompliantAttribute` atrybut jest używany. Na przykład zdefiniowanie `*static` elementu członkowskiego w interfejsie narusza regułę specyfikacji CLS. Jednakże jeśli zdefiniujesz `*static` elementu członkowskiego w interfejsie C# kompilator wyświetla komunikat o błędzie i nie powiedzie się skompilować aplikację.

`CLSCompliantAttribute` Atrybut jest oznaczony za pomocą [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) atrybut, który ma wartość `AttributeTargets.All`. Ta wartość umożliwia zastosowanie `CLSCompliantAttribute` atrybutu do dowolnego elementu programu, w tym zestawy, moduły, elementy członkowskie (konstruktorów, metod, właściwości, pola i zdarzenia), typu typami (klasy, struktury, wyliczenia, interfejsy i delegaci), Parametry, ogólne parametry i wartości zwracane. Jednak w praktyce powinien zastosować atrybut tylko do zestawów, typów i elementów członkowskich typu. W przeciwnym razie kompilatory ignorują atrybut i generowanie ostrzeżenia kompilatora, ilekroć mogą wystąpić niezgodny parametr, parametr ogólny, lub zwrócą wartość w swojej bibliotece interfejsu publicznego w dalszym ciągu.

Wartość `CLSCompliantAttribute` atrybutu jest dziedziczona przez zawarte elementy programu. Na przykład, jeśli zestaw jest oznaczony jako zgodny ze specyfikacją CLS, jego typy są również zgodne ze specyfikacją CLS. Jeśli typ jest oznaczony jako zgodny ze specyfikacją CLS, jego zagnieżdżone typy i elementy członkowskie są również zgodne ze specyfikacją CLS.

Można wyraźnie przezwyciężyć posiadaną podatność przez zastosowanie `CLSCompliantAttribute` atrybutu to zawartego elementu programu. Na przykład, można użyć `CLSCompliantAttribute` atrybutem *isCompliant* wartość `false` do zdefiniowania niezgodnego typu w zgodnym zestawie, a, można użyć atrybutu z *isCompliant*wartość `true` do zdefiniowania zgodnego typu w zestawie niezgodnym. Można także zdefiniować niezgodnych członków w zgodnym typie. Jednak niezgodnego typu nie może mieć zgodnych członków, więc nie można użyć atrybutu z *isCompliant* wartość `true` Aby zastąpić dziedziczenie z niezgodnego typu.

Opracowując składniki, należy zawsze używać `CLSCompliantAttribute` atrybutu, aby wskazać, czy zestaw, jego typy i jego członkowie są zgodne ze specyfikacją CLS.

Aby utworzyć składniki zgodne ze specyfikacją CLS:

1. Użyj `CLSCompliantAttribute` aby oznaczyć zestaw jako zgodny ze specyfikacją CLS.

2. Oznacz zgodni typów w zestawie, które nie są zgodne ze specyfikacją CLS jako niezgodne.

3. Umożliwia oznaczenie wszystkich członków publicznie narażonych w typach zgodnych ze specyfikacją CLS jako niezgodne.

4. Zapewniają zgodne ze specyfikacją CLS alternatywę dla członków innych niż zgodne ze specyfikacją CLS.

Jeśli już pomyślnie oznaczone wszystkie niezgodne typy i elementy członkowskie, kompilator nie powinien emitować żadnych ostrzeżeń o braku zgodności. Jednakże należy wskazać składniki, które nie są zgodne ze specyfikacją CLS i wyświetlić ich alternatywy zgodne ze specyfikacją CLS w dokumentacji produktu.

W poniższym przykładzie użyto `CLSCompliantAttribute` atrybut do definiowania zgodne ze specyfikacją CLS zestawu i typu `CharacterUtilities`, która ma dwie składowe zgodne ze specyfikacją niezgodne ze specyfikacją. Ponieważ obaj członkowie są oznaczeni `CLSCompliant(false)` atrybutu, kompilator nie generuje ostrzeżeń. Ta klasa oferuje również zgodne ze specyfikacją CLS alternatywę dla obu metod. Zwykle, możemy po prostu dodać dwa przeciążenia do `ToUTF16` metody w celu zapewnienia alternatywy zgodnej ze specyfikacją CLS. Jednakże ponieważ nie można obciążać metod na podstawie wartości zwracanej, nazwy metod zgodne ze specyfikacją CLS różnią się od nazw metod niezgodnych.

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch);
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      }
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch)
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If
   End Function
End Class
```

Jeśli tworzysz aplikację, a nie bibliotekę (to znaczy, jeśli nie udostępniasz typów lub elementów członkowskich, które mogą być wykorzystane przez innych programistów aplikacji), zgodność ze specyfikacją CLS elementów programu, z których korzysta aplikacja mogą być przydatne tylko wtedy, gdy język ich nie obsługuje . W takim przypadku Twój kompilator języka wygeneruje błąd podczas próby użycia elementu innego niż zgodne ze specyfikacją CLS.

## <a name="cross-language-interoperability"></a>Współdziałanie między językami

Niezależność od języka ma wiele znaczeń. Znaczenie jeden polega na bezproblemowe korzystanie z typów napisane w jednym języku z aplikacji napisanych w innym języku. Drugi znaczenia, czyli ten artykuł koncentruje się polega na połączeniu kodu napisanego w wielu językach, w ramach pojedynczego zestawu .NET Framework.

W poniższym przykładzie pokazano współdziałanie między językami, tworząc bibliotekę klas o nazwie Utilities.dll, który zawiera dwie klasy `NumericLib` i `StringLib`. `NumericLib` Klasy został napisany w języku C# i `StringLib` klasy został napisany w języku Visual Basic. Oto kod źródłowy `StringUtil.vb`, który zawiera jeden element członkowski `ToTitleCase`w jego `StringLib` klasy.

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String)

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split()
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "
         End If
      Next
      Return result
   End Function
End Module
```

Poniżej przedstawiono kod źródłowy NumberUtil.cs, który definiuje `NumericLib` klasy, która ma dwa elementy członkowskie, `IsEven` i `NearZero`.

```csharp
using System;

public static class NumericLib
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 ||
          number is Int32 ||
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001;
   }
}
```

Aby spakować dwóch klas w jednym zestawie, należy skompilować je do modułów. Aby skompilować plik kodu źródłowego języka Visual Basic w module, użyj tego polecenia:

```console
vbc /t:module StringUtil.vb
```

Aby skompilować plik kodu źródłowego języka C# w module, użyj tego polecenia:

```console
csc /t:module NumberUtil.cs
```

Możesz następnie użyć narzędzia łącza (Link.exe) do kompilowania dwa moduły do zestawu:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Poniższy przykład następnie wywołuje `NumericLib.NearZero` i `StringLib.ToTitleCase` metody. Należy pamiętać, że zarówno kod języka Visual Basic, jak i kodu C# mają dostęp do metod w obu klasach.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

Aby skompilować kod w języku Visual Basic, użyj tego polecenia:

```console
vbc example.vb /r:UtilityLib.dll
```

Aby skompilować z C#, Zmień nazwę kompilatora z vbc do Centrum obsługi klienta i zmień rozszerzenie pliku z .vb CS:

```console
csc example.cs /r:UtilityLib.dll
```
