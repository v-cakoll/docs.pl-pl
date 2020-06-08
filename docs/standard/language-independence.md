---
title: Niezależność od języka i składniki niezależne od języka
description: 'Dowiedz się, jak można opracowywać w jednym z wielu obsługiwanych języków w programie .NET, takich jak C#, C++/CLI, F #, IronPython, VB, Visual COBOL i PowerShell.'
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 813558299b40e0b90e8047f22b788c8f1419eb5e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504657"
---
# <a name="language-independence-and-language-independent-components"></a>Niezależność od języka i składniki niezależne od języka

.NET jest niezależny od języka. Oznacza to, że jako programista można opracowywać w jednym z wielu języków przeznaczonych dla implementacji platformy .NET, takich jak C#, F # i Visual Basic. Można uzyskać dostęp do typów i elementów członkowskich bibliotek klas opracowanych dla implementacji platformy .NET bez konieczności znajomości języka, w którym zostały pierwotnie napisane, i bez konieczności przestrzegania jakichkolwiek Konwencji języka oryginalnego. Jeśli jesteś deweloperem składnika, możesz uzyskać dostęp do składnika przez dowolną aplikację platformy .NET niezależnie od jego języka.

> [!NOTE]
> W pierwszej części tego artykułu omówiono Tworzenie składników niezależnych od języka, czyli składników, które mogą być używane przez aplikacje, które są zapisywane w dowolnym języku. Możesz również utworzyć pojedynczy składnik lub aplikację z kodu źródłowego zapisaną w wielu językach. Zobacz [współdziałanie między językami](#cross-language-interoperability) w drugiej części tego artykułu.

Aby w pełni współistnieć z innymi obiektami zapisanymi w dowolnym języku, obiekty muszą uwidocznić wywołujących tylko te funkcje, które są wspólne dla wszystkich języków. Ten wspólny zestaw funkcji jest definiowany przez Common Language Specification (CLS), który jest zestawem reguł, które są stosowane do wygenerowanych zestawów. Common Language Specification jest zdefiniowany w partycji I, klauzule od 7 do 11 w [standardzie ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Jeśli składnik jest zgodny z Common Language Specification, gwarantowany jest zgodność ze specyfikacją CLS i można uzyskać do niego dostęp z kodu w zestawach pisanych w dowolnym języku programowania, który obsługuje specyfikację CLS. Można określić, czy składnik jest zgodny z Common Language Specification w czasie kompilacji, stosując atrybut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) do kodu źródłowego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute).

## <a name="cls-compliance-rules"></a>Reguły zgodności ze specyfikacją CLS

W tej sekcji omówiono reguły tworzenia składnika zgodnego ze specyfikacją CLS. Aby uzyskać pełną listę reguł, zobacz partycja I, klauzula 11 [wzorca ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> W Common Language Specification omówiono każdą zasadę zgodności ze specyfikacją CLS, która ma zastosowanie do konsumentów (deweloperzy, którzy korzystają z programistycznego dostępu do składnika, który jest zgodny ze specyfikacją CLS), platformy (deweloperzy, którzy używają kompilatora języka do tworzenia bibliotek zgodnych ze standardem ",") i rozszerzeń (deweloperzy, którzy tworzą narzędzia, takie jak kompilator języka lub parser kodu, który tworzy składniki zgodne ze specyfikacj Ten artykuł koncentruje się na regułach, które mają zastosowanie do struktur. Należy zauważyć, że niektóre reguły, które mają zastosowanie do rozszerzeń, mogą również być stosowane do zestawów, które są tworzone za pomocą [odbicia. Emituj](xref:System.Reflection.Emit).

Aby zaprojektować składnik niezależny od języka, należy zastosować reguły zgodności ze specyfikacją CLS dla interfejsu publicznego składnika. Twoja prywatna implementacja nie musi być zgodna ze specyfikacją.

> [!IMPORTANT]
> Reguły zgodności ze specyfikacją CLS mają zastosowanie tylko do interfejsu publicznego składnika, a nie do prywatnej implementacji.

Na przykład liczby całkowite bez znaku inne niż [Byte](xref:System.Byte) nie są zgodne ze specyfikacją CLS. Ponieważ `Person` Klasa w poniższym przykładzie uwidacznia `Age` Właściwość typu [UInt16](xref:System.UInt16), poniższy kod wyświetla ostrzeżenie kompilatora.

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

Można sprawić, aby Klasa osoby była zgodna ze specyfikacją CLS, zmieniając typ `Age` właściwości z `UInt16` na [Int16](xref:System.Int16), która jest zgodna ze specyfikacją CLS, 16-bitową liczbą całkowitą ze znakiem. Nie trzeba zmieniać typu `personAge` pola prywatnego.

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

Interfejs publiczny biblioteki składa się z następujących elementów:

* Definicje klas publicznych.

* Definicje publicznych członków klas publicznych oraz definicje członków dostępnych dla klas pochodnych (czyli chronionych elementów członkowskich).

* Parametry i zwracane typy metod publicznych klas publicznych oraz parametry i zwracane typy metod dostępnych dla klas pochodnych.

Reguły zgodności ze specyfikacją CLS są wymienione w poniższej tabeli. Tekst reguł jest pobierany Verbatim z [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), czyli Copyright 2012 przez Ecma International. Bardziej szczegółowe informacje o tych regułach znajdują się w poniższych sekcjach.

Kategoria | Zobacz | Reguła | Numer reguły
-------- | --- | ---- | -----------
Ułatwienia dostępu | [Ułatwienia dostępu członków](#member-accessibility) | Dostępność nie zmienia się podczas zastępowania metod dziedziczonych, z wyjątkiem sytuacji, gdy zastąpi metodę dziedziczoną z innego zestawu z ułatwieniami dostępu `family-or-assembly` . W takim przypadku przesłonięcie ma dostęp `family` . | 10
Ułatwienia dostępu | [Ułatwienia dostępu członków](#member-accessibility) | Widoczność i dostępność typów i członków jest taka, że typy w podpisie każdego elementu członkowskiego są widoczne i dostępne za każdym razem, gdy sam element członkowski jest widoczny i dostępny. Na przykład metoda publiczna widoczna poza jej zestawem nie ma argumentu, którego typ jest widoczny tylko w obrębie zestawu. Widoczność i dostępność typów tworzących typ ogólny, używany w podpisie dowolnego elementu członkowskiego, są widoczne i dostępne za każdym razem, gdy element członkowski jest widoczny i dostępny. Na przykład typ generyczny skonkretyzowany obecny w sygnaturze elementu członkowskiego, który jest widoczny poza jego zestawem, nie powinien mieć argumentu ogólnego, którego typ jest widoczny tylko w obrębie zestawu. | 12
Tablice | [Tablice](#arrays) | Tablice powinny mieć elementy z typem zgodnym ze specyfikacją CLS, a wszystkie wymiary tablicy mają dolne granice równe zero. Tylko fakt, że element jest tablicą, a typ elementu tablicy musi być wymagany do rozróżnienia między przeciążeniami. Gdy Przeciążenie jest oparte na dwóch lub większej liczbie typów tablicowych, typy elementów muszą być nazwanymi typami. | 16
Atrybuty | [Atrybuty](#attributes) | Atrybuty muszą być typu [System. Attribute](xref:System.Attribute)lub dziedziczyć po nim. | 41
Atrybuty | [Atrybuty](#attributes) | CLS zezwala tylko na podzbiór kodowań atrybutów niestandardowych. Jedyne typy, które pojawiają się w tych kodowaniach, to (zobacz partycja IV [System.Double](xref:System.Double)): [System. Type](xref:System.Type), [System. String](xref:System.String), [System. Char](xref:System.Char), [System. Boolean](xref:System.Boolean), system. [Byte](xref:System.Byte), system. [Int16](xref:System.Int16), system. [Int32](xref:System.Int32), [System.Single](xref:System.Single) [system](xref:System.Int64). | 34
Atrybuty | [Atrybuty](#attributes) | Specyfikacja CLS nie zezwala na jawne widoczne Modyfikatory ( `modreq` , zobacz partycja II), ale zezwala na Modyfikatory opcjonalne ( `modopt` , zobacz partycja II), które nie są zrozumiałe. | 35
Konstruktory | [Konstruktorów](#constructors) | Konstruktor obiektu wywołuje niektórych konstruktorów wystąpień swojej klasy podstawowej przed wszelkimi dostępami do dziedziczonych danych wystąpienia. (Nie dotyczy to typów wartości, które nie muszą mieć konstruktorów).  | 21
Konstruktory | [Konstruktorów](#constructors) | Konstruktor obiektów nie jest wywoływany, chyba że jest częścią tworzenia obiektu, a obiekt nie zostanie dwukrotnie zainicjowany. | 22
Wyliczenia | [Wyliczenia](#enumerations) | Podstawowy typ wyliczenia musi być wbudowanym typem Integer CLS, nazwa pola powinna mieć wartość "value__" i to pole powinno być oznaczone `RTSpecialName` . |  7
Wyliczenia | [Wyliczenia](#enumerations) | Istnieją dwa odrębne rodzaje typów wyliczeniowych, wskazywane przez obecność lub brak elementu [System. FlagsAttribute](xref:System.FlagsAttribute) (zobacz partycja IV Library) atrybut niestandardowy. Jeden reprezentuje nazwane wartości całkowite; Druga reprezentuje nazwane flagi bitowe, które można połączyć w celu wygenerowania nienazwanej wartości. Wartość elementu `enum` nie jest ograniczona do określonych wartości. |  8
Wyliczenia | [Wyliczenia](#enumerations) | Literałowe pola statyczne typu wyliczeniowego mają typ wyliczenia. |  9
Zdarzenia | [Zdarzenia](#events) | Metody implementujące zdarzenie należy oznaczyć `SpecialName` w metadanych. |29
Zdarzenia | [Zdarzenia](#events) | Dostępność zdarzenia i jego metod dostępu powinna być taka sama. |30
Zdarzenia | [Zdarzenia](#events) | `add`Metody i `remove` dla zdarzenia muszą być obecne lub nieobecne. |31
Zdarzenia | [Zdarzenia](#events) | `add`Metody i `remove` dla zdarzenia muszą mieć jeden parametr, którego typ definiuje typ zdarzenia i który powinien pochodzić od elementu [System. Delegate](xref:System.Delegate). |32
Zdarzenia | [Zdarzenia](#events) | Zdarzenia muszą być zgodne z określonym wzorcem nazewnictwa. Atrybut SpecialName, do którego odwołuje się reguła CLS 29, jest ignorowany w odpowiednich porównaniach nazw i stosuje się do reguł identyfikatorów.  |33
Wyjątki | [Wyjątki](#exceptions) | Obiekty, które są generowane, są typu [System. Exception](xref:System.Exception) lub dziedziczą z niego typ. Niemniej jednak metody zgodne ze specyfikacją CLS nie są wymagane do blokowania propagacji innych typów wyjątków. | 40
Ogólne | [Reguły zgodności ze specyfikacją CLS](#cls-compliance-rules) | Reguły CLS stosują się tylko do tych części typu, które są dostępne lub widoczne poza zestawem definiującym. | 1
Ogólne | [Reguły zgodności ze specyfikacją CLS](#cls-compliance-rules) | Elementy członkowskie typów niezgodnych ze specyfikacją CLS nie mogą być oznaczone jako zgodne ze specyfikacją CLS. | 2
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Zagnieżdżone typy powinny zawierać co najmniej tyle parametrów ogólnych jak typ otaczający. Parametry ogólne w typie zagnieżdżonym odpowiadają pozycjom parametrów ogólnych w jego typie otaczającym.  | 42
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Nazwa typu ogólnego zawiera kodowanie liczby parametrów typu zadeklarowanych w typie niezagnieżdżonym lub nowo wprowadzona do typu, jeśli jest zagnieżdżona, zgodnie z regułami określonymi powyżej. | 43
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Typ ogólny musi redeklarować wystarczające ograniczenia, aby zagwarantować, że wszystkie ograniczenia dotyczące typu podstawowego lub interfejsów byłyby spełnione przez ograniczenia typu ogólnego. | 44
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Typy używane jako ograniczenia parametrów ogólnych będą same w sobie zgodne ze specyfikacją CLS. | 45
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Widoczność i dostępność elementów członkowskich (w tym zagnieżdżonych typów) w typie ogólnym, który można utworzyć, jest uznawana za zakres do określonego wystąpienia, a nie jako całości deklaracji typu ogólnego. Przy założeniu, że nadal mają zastosowanie reguły widoczności i dostępności reguły CLS 12. | 46
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Dla każdej abstrakcyjnej lub wirtualnej metody ogólnej należy mieć domyślną implementację specyficzną (nieabstrakcyjną) | 47
Interfejsy | [Interfejsy](#interfaces) | Interfejsy zgodne ze specyfikacją CLS nie wymagają definicji metod niezgodnych ze specyfikacją CLS w celu ich wdrożenia. | 18
Interfejsy | [Interfejsy](#interfaces) | Interfejsy zgodne ze specyfikacją CLS nie definiują metod statycznych ani nie definiują pól. | 19
Elementy członkowskie | [Ogólnie wpisz składowe](#type-members-in-general) | Globalne pola statyczne i metody nie są zgodne ze specyfikacją CLS. | 36
Elementy członkowskie | -- | Wartość literału statycznego jest określana za pomocą metadanych inicjacji pola. Literał zgodny ze specyfikacją CLS musi mieć wartość określoną w metadanych inicjowania pola, które są dokładnie takie same jak w przypadku literału (lub typu podstawowego, jeśli ten literał to `enum` ). | 13
Elementy członkowskie | [Ogólnie wpisz składowe](#type-members-in-general) | Ograniczenie vararg nie jest częścią specyfikacji CLS, a jedyną konwencją wywoływania obsługiwaną przez specyfikację CLS jest standardowa zarządzana Konwencja wywoływania. | 15
Konwencje nazewnictwa | [Konwencje nazewnictwa](#naming-conventions) | Zespoły muszą przestrzegać załącznika 7 raportu technicznego 15 standardu Unicode 3.0 w celu określenia zestawu znaków dozwolonego do uruchomienia i dołączenia do identyfikatorów, dostępne online w [formularzach normalizacji Unicode](https://unicode.org/reports/tr15/). Identyfikatory powinny znajdować się w formacie kanonicznym zdefiniowanym przez normalizację Unicode w postaci C. W celach CLS dwa identyfikatory są takie same, jeśli ich mapowania małymi literami (zgodnie z ustawieniami regionalnymi Unicode, które różnią się od liter, jeden do jednego) są takie same. Oznacza to, że w przypadku dwóch identyfikatorów, które mają być uznawane za różne pod względem CLS, różnią się w więcej niż w ich przypadku. Jednak w celu zastąpienia definicji dziedziczonej, interfejs wiersza polecenia wymaga dokładnego kodowania oryginalnej deklaracji. | 4
Przeciążenie | [Konwencje nazewnictwa](#naming-conventions) | Wszystkie nazwy wprowadzone w zakresie zgodnym ze specyfikacją CLS powinny być odrębne niezależnie od rodzaju, z wyjątkiem sytuacji, gdy nazwy są identyczne i rozwiązywane przez przeciążanie. Oznacza to, że podczas gdy CTS zezwala na pojedynczy typ do używania tej samej nazwy dla metody i pola, CLS nie. | 5
Przeciążenie | [Konwencje nazewnictwa](#naming-conventions) | Pola i zagnieżdżone typy powinny różnić się odrębnie przez porównanie identyfikatorów, nawet jeśli CTS zezwala na rozróżnianie unikatowych podpisów. Metody, właściwości i zdarzenia, które mają taką samą nazwę (za pomocą porównania identyfikatorów), różnią się więcej niż tylko zwracanym typem, z wyjątkiem określonych w regule CLS 39 | 6
Przeciążenie | [Przeciążenia](#overloads) | Tylko właściwości i metody mogą być przeciążone. | 37
Przeciążenie | [Przeciążenia](#overloads) |Właściwości i metody mogą być przeciążone na podstawie liczby i typów ich parametrów, z wyjątkiem operatorów konwersji o nazwach `op_Implicit` i `op_Explicit` , które mogą być również przeciążone na podstawie ich typu zwracanego. | 38
Przeciążenie | -- | Jeśli dwie lub więcej metod zgodnych ze specyfikacją CLS zadeklarowanych w typie ma taką samą nazwę i, dla określonego zestawu wystąpień typu, mają one te same parametry i zwracane typy, wówczas wszystkie te metody są semantycznie równoważne w tych wystąpieniach typu. | 48
Właściwości | [Właściwości](#properties) | Metody, które implementują metody pobierającej i ustawiającej właściwość, powinny być oznaczone `SpecialName` w metadanych. | 24
Właściwości | [Właściwości](#properties) | Metody dostępu do właściwości muszą być statyczne, wszystkie być wirtualne lub być wystąpieniem. | 26
Właściwości | [Właściwości](#properties) | Typ właściwości musi być typem zwracanym metody pobierającej i typem ostatniego argumentu metody ustawiającej. Typy parametrów właściwości są typami parametrów do metody pobierającej i typami wszystkich oprócz końcowych parametrów metody ustawiającej. Wszystkie te typy muszą być zgodne ze specyfikacją CLS i nie mogą być zarządzanymi wskaźnikami (czyli nie są przesyłane przez odwołanie). | 27
Właściwości | [Właściwości](#properties) | Właściwości muszą być zgodne z określonym wzorcem nazewnictwa. `SpecialName`Atrybut, do którego odwołuje się reguła CLS, jest ignorowany w odpowiednich porównaniach nazw i przestrzega reguł identyfikatorów. Właściwość ma metodę pobierającą, metodę ustawiającą lub obie te metody. | 28
Konwersja typu | [Konwersja typu](#type-conversion) | Jeśli podano op_Implicit lub op_Explicit, należy podać alternatywny sposób dostarczenia przekształcenia. | 39
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Opakowane typy wartości nie są zgodne ze specyfikacją CLS. | 3
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Wszystkie typy występujące w podpisie muszą być zgodne ze specyfikacją CLS. Wszystkie typy tworzące typ ogólny, który tworzy wystąpienie, są zgodne ze specyfikacją CLS. | 11
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Wpisane odwołania nie są zgodne ze specyfikacją CLS. | 14
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Niezarządzane typy wskaźnika nie są zgodne ze specyfikacją CLS. | 17
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Klasy zgodne ze specyfikacją CLS, typy wartości i interfejsy nie wymagają implementacji członków niezgodnych ze specyfikacją CLS | 20
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Element [System. Object](xref:System.Object) jest zgodny ze specyfikacją CLS. Wszystkie inne klasy zgodne ze specyfikacją CLS są dziedziczone z klasy zgodnej ze specyfikacją CLS. | 23

Indeksuj do podsekcji:

* [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures)
* [Konwencje nazewnictwa](#naming-conventions)
* [Konwersja typu](#type-conversion)
* [Tablice](#arrays)
* [Interfejsy](#interfaces)
* [Wyliczenia](#enumerations)
* [Ogólnie wpisz składowe](#type-members-in-general)
* [Ułatwienia dostępu członków](#member-accessibility)
* [Typy ogólne i elementy członkowskie](#generic-types-and-members)
* [Konstruktory](#constructors)
* [Właściwości](#properties)
* [Zdarzenia](#events)
* [Przeciążenia](#overloads)
* [Wyjątki](#exceptions)
* [Atrybuty](#attributes)

### <a name="types-and-type-member-signatures"></a>Typy i podpisy elementów członkowskich typu

Typ [System. Object](xref:System.Object) jest zgodny ze specyfikacją CLS i jest typem podstawowym wszystkich typów obiektów w systemie .NET Framework typu. Dziedziczenie w .NET Framework jest niejawne (na przykład Klasa [String](xref:System.String) niejawnie dziedziczy z `Object` klasy) lub explicit (na przykład Klasa [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) jawnie dziedziczy z klasy [ArgumentException](xref:System.ArgumentException) , która jawnie dziedziczy z klasy [Exception](xref:System.Exception) . Aby typ pochodny był zgodny ze specyfikacją CLS, jego typ podstawowy również musi być zgodny ze specyfikacją CLS.

Poniższy przykład przedstawia typ pochodny, którego typ podstawowy nie jest zgodny ze specyfikacją CLS. Definiuje klasę bazową `Counter` , która używa niepodpisanej 32-bitowej liczby całkowitej jako licznika. Ponieważ Klasa udostępnia funkcje licznika przez Zawijanie liczby całkowitej bez znaku, Klasa jest oznaczona jako niezgodna ze specyfikacją CLS. W związku z tym Klasa pochodna, `NonZeroCounter` , również nie jest zgodna ze specyfikacją CLS.

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
      return $"{ctr}). ";
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
      Return $"{ctr}). "
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

Wszystkie typy, które pojawiają się w sygnaturach składowych, łącznie z typem zwracanym metody lub typem właściwości, muszą być zgodne ze specyfikacją CLS. Ponadto dla typów ogólnych:

* Wszystkie typy tworzące typ ogólny wystąpienia muszą być zgodne ze specyfikacją CLS.

* Wszystkie typy używane jako ograniczenia parametrów ogólnych muszą być zgodne ze specyfikacją CLS.

[Wspólny system typów](common-type-system.md) .NET zawiera wiele wbudowanych typów, które są obsługiwane bezpośrednio przez środowisko uruchomieniowe języka wspólnego i są specjalnie zakodowane w metadanych zestawu. Z tych typów wewnętrznych typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS.

Typ zgodny ze specyfikacją CLS | Opis
------------------ | -----------
[Bajc](xref:System.Byte) | 8-bitowa liczba całkowita bez znaku
[Int16](xref:System.Int16) | 16-bitowa liczba całkowita ze znakiem
[Int32](xref:System.Int32) | 32-bitowa liczba całkowita ze znakiem
[Int64](xref:System.Int64) | 64-bitowa liczba całkowita ze znakiem
[Single](xref:System.Single) | Wartość zmiennoprzecinkowa o pojedynczej precyzji
[Double](xref:System.Double) | Wartość zmiennoprzecinkowa o podwójnej precyzji
[Boolean](xref:System.Boolean) | Typ wartości true lub false
[Delikatn](xref:System.Char) | Jednostka kodu zakodowana w formacie UTF-16
[Dokładności](xref:System.Decimal) | Liczba dziesiętna liczb zmiennoprzecinkowych
[IntPtr](xref:System.IntPtr) | Wskaźnik lub uchwyt rozmiaru zdefiniowanego przez platformę
[Ciąg](xref:System.String) | Kolekcja zero, jeden lub więcej obiektów char

Typy wewnętrzne wymienione w poniższej tabeli są niezgodne ze specyfikacją CLS.

Niezgodny typ | Opis | Alternatywa zgodna ze specyfikacją CLS
------------------ | ----------- | -------------------------
[SByte](xref:System.SByte) | 8-bitowy typ danych ze znakiem liczb całkowitych | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16-bitowa liczba całkowita bez znaku | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32-bitowa liczba całkowita bez znaku | [Int64](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64-bitowa liczba całkowita bez znaku | [Int64](xref:System.Int64) (może przepełnić się), [BigInteger](xref:System.Numerics.BigInteger)lub [Double](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | Niepodpisany wskaźnik lub dojście | [IntPtr](xref:System.IntPtr)

Biblioteka klas .NET Framework lub jakakolwiek inna Biblioteka klas może zawierać inne typy, które nie są zgodne ze specyfikacją CLS; na przykład:

* Opakowane typy wartości. Poniższy przykład w języku C# tworzy klasę, która ma właściwość publiczną typu `int*` o nazwie `Value` . Ponieważ `int*` jest to opakowany typ wartości, kompilator flaguje go jako niezgodny ze specyfikacją CLS.

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

* Typy odwołań, które są specjalnymi konstrukcjami, które zawierają odwołanie do obiektu i odwołanie do typu.

Jeśli typ nie jest zgodny ze specyfikacją CLS, należy zastosować atrybut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) z parametrem *iszgodna* z wartością `false` do. Aby uzyskać więcej informacji, zobacz sekcję [atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute) .

Poniższy przykład ilustruje problem zgodności ze specyfikacją CLS w sygnaturze metody i w tworzeniu wystąpienia typu ogólnego. Definiuje `InvoiceItem` klasę z właściwością typu [UInt32](xref:System.UInt32), właściwością typu [Nullable (UInt32)](xref:System.Nullable%601)i konstruktorem z parametrami typu `UInt32` i `Nullable(Of UInt32)` . Podczas próby skompilowania tego przykładu uzyskasz cztery ostrzeżenia kompilatora.

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

Aby wyeliminować ostrzeżenia kompilatora, Zastąp typy niezgodne ze specyfikacją CLS w `InvoiceItem` interfejsie publicznym przy użyciu zgodnych typów:

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

Oprócz określonych typów wymienionych niektóre kategorie typów nie są zgodne ze specyfikacją CLS. Są to między innymi typy wskaźników niezarządzanych i typy wskaźników funkcji. Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej, aby utworzyć tablicę liczb całkowitych.

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

Dla klas abstrakcyjnych zgodnych ze specyfikacją CLS (czyli klas oznaczonych jako `abstract` w języku C#) wszystkie elementy członkowskie klasy muszą również być zgodne ze specyfikacją CLS.

### <a name="naming-conventions"></a>Konwencje nazewnictwa

Ponieważ w niektórych językach programowania nie jest rozróżniana wielkość liter, identyfikatory (takie jak nazwy przestrzeni nazw, typy i składowe) muszą różnić się więcej niż wielkością liter. Dwa identyfikatory są uważane za równoważne, jeśli ich mapowania małych liter są takie same. Poniższy przykład języka C# definiuje dwie klasy publiczne `Person` i `person` . Ponieważ różnią się tylko wielkością liter, kompilator języka C# flaguje je jako niezgodne ze specyfikacją CLS.

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

Identyfikatory języków programowania, takie jak nazwy przestrzeni nazw, typy i elementy członkowskie, muszą być zgodne ze [standardem Unicode](https://unicode.org/reports/tr15/). Oznacza to, że:

* Pierwszy znak identyfikatora może być dowolną wielką literą Unicode, małą literą, literą litery tytułu, literą modyfikującą, inną literą lub cyfrą. Aby uzyskać informacje dotyczące kategorii znaków Unicode, zobacz Wyliczenie [System. globalizacja. UnicodeCategory](xref:System.Globalization.UnicodeCategory) .

* Kolejne znaki mogą pochodzić z dowolnej kategorii jako pierwszy znak, a także mogą zawierać znaki niebędące odstępami, odstępy łączące znaczniki, cyfry dziesiętne, znaki interpunkcyjne łącznika i kody formatowania.

Przed porównaniem identyfikatorów należy odfiltrować kody formatowania i przekonwertować identyfikatory na postać normalizacji Unicode, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu zakodowanych w formacie UTF-16. Sekwencje znaków tworzące te same jednostki kodu w formularzu normalizacji Unicode nie są zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano właściwość o nazwie `Å` , która składa się ze znaku Angstrom znak (U + 212B), a druga właściwość o nazwie `Å` , która składa się z znaku Wielka litera a z pierścieniem powyżej (U + 00C5). Kompilator języka C# oflagowuje kod źródłowy jako niezgodny ze specyfikacją CLS.

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

Nazwy elementów członkowskich w ramach określonego zakresu (takie jak przestrzenie nazw w obrębie zestawu, typy w przestrzeni nazw lub elementy członkowskie w ramach typu) muszą być unikatowe, z wyjątkiem nazw, które są rozpoznawane za pomocą przeciążenia. To wymaganie jest bardziej rygorystyczne niż w przypadku systemu wspólnego typu, który umożliwia wielu członkom w zakresie posiadanie identycznych nazw, o ile są one różnymi rodzajami elementów członkowskich (na przykład jest to metoda, a jedna to pole). W szczególności dla elementów członkowskich typu:

* Pola i zagnieżdżone typy są rozróżniane wyłącznie nazwami.

* Metody, właściwości i zdarzenia, które mają taką samą nazwę, muszą różnić się więcej niż tylko zwracanym typem.

Poniższy przykład ilustruje wymaganie, aby nazwy elementów członkowskich muszą być unikatowe w ramach zakresu. Definiuje klasę o nazwie `Converter` , która zawiera cztery składowe o nazwie `Conversion` . Trzy to metody, a jedna jest właściwością. Metoda, która zawiera `Int64` parametr, ma unikatową nazwę, ale dwie metody z `Int32` parametrem nie są, ponieważ wartość zwracana nie jest uważana za część podpisu elementu członkowskiego. `Conversion`Właściwość również narusza to wymaganie, ponieważ właściwości nie mogą mieć takiej samej nazwy jak przeciążone metody.

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

Poszczególne języki zawierają unikatowe słowa kluczowe, dlatego Języki przeznaczone dla środowiska uruchomieniowego języka wspólnego muszą również zawierać mechanizm odwołujący się do identyfikatorów (takich jak nazwy typów), które pokrywają się ze słowami kluczowymi. Na przykład, `case` jest słowem kluczowym w języku C# i Visual Basic. Jednak poniższy Visual Basic przykład jest w stanie odróżnić klasę o nazwie `case` od `case` słowa kluczowego za pomocą otwierającego i zamykającego nawiasu klamrowego. W przeciwnym razie przykład zostanie wyświetlony komunikat o błędzie "słowo kluczowe nie jest prawidłowe jako identyfikator" i nie można go skompilować.

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

W poniższym przykładzie w języku C# można utworzyć wystąpienie `case` klasy przy użyciu znaku @, aby odróżnić identyfikator od słowa kluczowego języka. Bez niej, kompilator języka C# wyświetli dwa komunikaty o błędach, "Oczekiwano typu" i "wyrażenie" nieprawidłowego terminu "."

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

Common Language Specification definiuje dwa operatory konwersji:

* `op_Implicit`, który jest używany do rozszerzania konwersji, które nie powodują utraty danych lub dokładności. Na przykład struktura [dziesiętna](xref:System.Decimal) zawiera przeciążony `op_Implicit` operator, aby konwertować wartości typów całkowitych i wartości [char](xref:System.Char) na `Decimal` wartości.

* `op_Explicit`, który jest używany na potrzeby konwersji zawężających, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub precyzję. Na przykład `Decimal` Struktura zawiera przeciążony operator służący `op_Explicit` do konwertowania wartości [podwójnej](xref:System.Double) i [pojedynczej](xref:System.Single) na `Decimal` i w celu przekonwertowania `Decimal` na wartości całkowite, `Double` , `Single` i `Char` .

Jednak nie wszystkie języki obsługują przeciążanie operatora lub definicję operatorów niestandardowych. Jeśli zdecydujesz się zaimplementować te operatory konwersji, należy również podać alternatywny sposób wykonywania konwersji. Zalecamy podanie `From` metod XXX i `To` xxx.

W poniższym przykładzie zdefiniowano Konwersje jawne zgodne ze specyfikacją CLS. Tworzy `UDouble` klasę, która reprezentuje podpisaną liczbę zmiennoprzecinkową o podwójnej precyzji. Zapewnia to niejawne konwersje z `UDouble` do `Double` i dla jawnych konwersji z `UDouble` do `Single` , `Double` do `UDouble` , i `Single` do `UDouble` . Definiuje również `ToDouble` metodę jako alternatywę dla operatora niejawnej konwersji oraz `ToSingle` `FromDouble` metody,, i `FromSingle` jako alternatywy dla operatorów jawnej konwersji.

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

Tablice zgodne ze specyfikacją CLS są zgodne z następującymi regułami:

* Wszystkie wymiary tablicy muszą mieć dolną granicę równą zero. Poniższy przykład tworzy tablicę niezgodną ze specyfikacją CLS z dolną granicą. Pomimo obecności atrybutu [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) kompilator nie wykrywa, że tablica zwracana przez `Numbers.GetTenPrimes` metodę nie jest zgodna ze specyfikacją CLS.

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

* Wszystkie elementy tablicy muszą zawierać typy zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano dwie metody, które zwracają tablice niezgodne ze specyfikacją CLS. Pierwszy zwraca tablicę wartości [UInt32](xref:System.UInt32) . Druga zwraca tablicę [obiektów](xref:System.Object) , która zawiera [Int32](xref:System.Int32) i `UInt32` wartości. Chociaż kompilator identyfikuje pierwszą tablicę jako niezgodną ze względu na jej `UInt32` Typ, nie rozpoznaje, że druga tablica zawiera elementy niezgodne ze specyfikacją CLS.

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

* Rozpoznawanie przeciążenia dla metod, które mają parametry tablicowe, jest oparte na faktach, że są tablicami i według ich typu elementu. Z tego powodu następująca definicja przeciążonej `GetSquares` metody jest zgodna ze specyfikacją CLS.

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

Interfejsy zgodne ze specyfikacją CLS mogą definiować właściwości, zdarzenia i metody wirtualne (metody bez implementacji). Interfejs zgodny ze specyfikacją CLS nie może mieć następujących elementów:

* Metody statyczne lub pola statyczne. Kompilator języka C# generuje błędy kompilatora, jeśli zdefiniujesz statyczną składową w interfejsie.

* Pola. Kompilator języka C# generuje błędy kompilatora, jeśli zdefiniujesz pole w interfejsie.

* Metody, które nie są zgodne ze specyfikacją CLS. Na przykład następująca definicja interfejsu obejmuje metodę, `INumber.GetUnsigned` która jest oznaczona jako niezgodna ze specyfikacją CLS. Ten przykład generuje ostrzeżenie kompilatora.

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

  Ze względu na tę regułę typy zgodne ze specyfikacją CLS nie są wymagane do implementacji członków niezgodnych ze specyfikacją CLS. Jeśli struktura zgodna ze specyfikacją CLS uwidacznia klasę, która implementuje interfejs niezgodny ze specyfikacją CLS, powinien również udostępnić konkretne implementacje wszystkich członków niezgodnych ze specyfikacją CLS.

Kompilatory języka zgodne ze specyfikacją CLS muszą również zezwalać klasie na udostępnianie oddzielnych implementacji elementów członkowskich o tej samej nazwie i podpisie w wielu interfejsach. C# obsługuje jawne implementacje interfejsu, aby zapewnić różne implementacje metod o identycznych nazwach. Poniższy przykład ilustruje ten scenariusz, definiując `Temperature` klasę implementującą `ICelsius` `IFahrenheit` interfejsy i jako jawne implementacje interfejsu.

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

Wyliczenia zgodne ze specyfikacją CLS muszą być zgodne z następującymi regułami:

* Podstawowym typem wyliczenia musi być wewnętrzna liczba całkowita zgodna ze specyfikacją CLS ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32)lub [Int64](xref:System.Int64)). Na przykład poniższy kod próbuje zdefiniować Wyliczenie, którego typem podstawowym jest [UInt32](xref:System.UInt32) i generuje ostrzeżenie kompilatora.

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

* Typ wyliczenia musi mieć jedno pole wystąpienia o nazwie `Value__` , które jest oznaczone `FieldAttributes.RTSpecialName` atrybutem. Dzięki temu można odwołać się do wartości pola niejawnie.

* Wyliczenie zawiera literał pól statycznych, których typy pasują do typu wyliczenia. Na przykład, jeśli zdefiniujesz `State` Wyliczenie z wartościami `State.On` i `State.Off` , `State.On` i `State.Off` są polami literałów statycznych, których typem jest `State` .

* Istnieją dwa rodzaje wyliczeń:

  * Wyliczenie, które reprezentuje zestaw wzajemnie wykluczających się wartości o nazwach całkowitych. Ten typ wyliczenia jest wskazywany przez brak atrybutu niestandardowego [System. FlagsAttribute](xref:System.FlagsAttribute) .

  * Wyliczenie, które reprezentuje zestaw flag bitowych, które można połączyć w celu wygenerowania nienazwanej wartości. Ten typ wyliczenia jest wskazywany przez obecność atrybutu niestandardowego [System. FlagsAttribute](xref:System.FlagsAttribute) .

Aby uzyskać więcej informacji, zapoznaj się z dokumentacją struktury [enum](xref:System.Enum) .

* Wartość wyliczenia nie jest ograniczona do zakresu określonych wartości. Innymi słowy, zakres wartości w wyliczeniu jest zakresem jego wartości źródłowej. Możesz użyć metody, `Enum.IsDefined` Aby określić, czy określona wartość jest elementem członkowskim wyliczenia.

### <a name="type-members-in-general"></a>Ogólnie wpisz składowe

Common Language Specification wymaga, aby wszystkie pola i metody były dostępne jako elementy członkowskie konkretnej klasy. W związku z tym globalne pola i metody statyczne (czyli pola statyczne lub metody, które są zdefiniowane niezależnie od typu) nie są zgodne ze specyfikacją CLS. Jeśli spróbujesz dołączyć pole globalne lub metodę w kodzie źródłowym, kompilator języka C# generuje błąd kompilatora.

Common Language Specification obsługuje tylko standardową konwencję wywoływania zarządzanego. Nie obsługuje ona niezarządzanych konwencji wywoływania i metod ze zmiennymi listami argumentów oznaczonymi `varargs` słowem kluczowym. W przypadku list zmiennych argumentów, które są zgodne ze standardową konwencją wywoływania zarządzanego, Użyj atrybutu [ParamArrayAttribute](xref:System.ParamArrayAttribute) lub implementacji poszczególnych języków, takich jak `params` słowo kluczowe w języku C# i `ParamArray` słowo kluczowe w Visual Basic.

### <a name="member-accessibility"></a>Ułatwienia dostępu członków

Zastępowanie dziedziczonego elementu członkowskiego nie może zmienić dostępności tego elementu członkowskiego. Na przykład metoda publiczna w klasie bazowej nie może zostać zastąpiona przez prywatną metodę w klasie pochodnej. Istnieje jeden wyjątek: `protected internal` element członkowski (w języku C#) lub `Protected Friend` (w Visual Basic) w jednym zestawie, który jest zastępowany przez typ w innym zestawie.  W takim przypadku dostępność przesłonięcia to `Protected` .

Poniższy przykład ilustruje błąd generowany, gdy atrybut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) jest ustawiony na `true` , i `Person` , który jest klasą pochodną `Animal` , próbuje zmienić dostępność `Species` właściwości z publicznej na prywatną. Przykład został pomyślnie skompilowany, jeśli jego dostępność została zmieniona na publiczną.

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

Typy w podpisie składowej muszą być dostępne za każdym razem, gdy ten element członkowski jest dostępny. Na przykład oznacza to, że publiczna składowa nie może zawierać parametru, którego typem jest Private, protected lub internal. Poniższy przykład ilustruje błąd kompilatora, który powstaje, gdy `StringWrapper` Konstruktor klasy ujawnia wewnętrzną `StringOperationType` wartość wyliczenia, która określa, jak powinna być opakowana wartość ciągu.

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

### <a name="generic-types-and-members"></a>Typy ogólne i elementy członkowskie

Zagnieżdżone typy zawsze mają co najmniej tyle parametrów ogólnych jak ich typ otaczający. Odnoszą się one do parametrów ogólnych w typie otaczającym. Typ ogólny może również zawierać nowe parametry ogólne.

Relacja między parametrami typu ogólnego typu zawierającego i jego zagnieżdżonymi typami może być ukryta przez składnię poszczególnych języków. W poniższym przykładzie typ ogólny `Outer<T>` zawiera dwie klasy zagnieżdżone `Inner1A` i `Inner1B<U>` . Wywołania `ToString` metody, którą każda klasa dziedziczy z `Object.ToString` , pokazują, że każda klasa zagnieżdżona zawiera parametry typu klasy zawierającej.

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

Nazwy typów ogólnych są kodowane w postaci *nazwy*"*n*, gdzie *name* jest nazwą typu, *`* jest literałem znaku, a *n* to liczba parametrów zadeklarowanych w typie, lub dla zagnieżdżonych typów ogólnych, liczba nowo wprowadzonych parametrów typu. To kodowanie nazw typów ogólnych jest szczególnie przydatne dla deweloperów korzystających z odbicia w celu uzyskania dostępu do typów ogólnych z aspektami CLS w bibliotece.

Jeśli ograniczenia są stosowane do typu generycznego, wszystkie typy używane jako ograniczenia muszą również być zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano klasę o nazwie `BaseClass` , która jest niezgodna ze specyfikacją CLS, i klasę generyczną o nazwie, `BaseCollection` której parametr typu musi pochodzić od `BaseClass` . Ale ponieważ `BaseClass` nie jest zgodny ze specyfikacją CLS, kompilator emituje ostrzeżenie.

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

Jeśli typ ogólny pochodzi od generycznego typu podstawowego, musi ponownie zadeklarować wszelkie ograniczenia, aby można było zagwarantować, że ograniczenia dotyczące typu podstawowego również są spełnione. W poniższym przykładzie zdefiniowano `Number<T>` , który może reprezentować dowolny typ liczbowy. Definiuje również `FloatingPoint<T>` klasę, która reprezentuje wartość zmiennoprzecinkową. Jednak kod źródłowy nie zostanie skompilowany, ponieważ nie ma zastosowania ograniczenia `Number<T>` (to T musi być typem wartości) `FloatingPoint<T>` .

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

Przykład zostanie skompilowany pomyślnie, jeśli ograniczenie zostanie dodane do `FloatingPoint<T>` klasy.

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

Common Language Specification nakładają się na model tworzenia wystąpień dla zagnieżdżonych typów i chronionych elementów członkowskich. Otwarte typy ogólne nie mogą ujawniać pól ani członków z podpisami zawierającymi określone wystąpienie zagnieżdżonego, chronionego typu ogólnego. Typy nieogólne, które zwiększają wystąpienie określonego wystąpienia generycznej klasy podstawowej lub interfejsu, nie mogą ujawniać pól ani elementów członkowskich z podpisami zawierającymi różne wystąpienia zagnieżdżonego, chronionego typu ogólnego.

Poniższy przykład definiuje typ ogólny, `C1<T>` i chronioną klasę `C1<T>.N` . `C1<T>`ma dwie metody `M1` i `M2` . Jednakże `M1` nie jest zgodny ze specyfikacją CLS, ponieważ próbuje zwrócić `C1<int>.N` obiekt z `C1<T>` . Druga klasa, `C2` ,, pochodzi od `C1<long>` . Ma dwie metody `M3` i `M4` . `M3`nie jest zgodne ze specyfikacją CLS, ponieważ próbuje zwrócić `C1<int>.N` obiekt z podklasy `C1<long>` . Kompilatory języka mogą być jeszcze bardziej restrykcyjne. W tym przykładzie Visual Basic wyświetla błąd podczas próby skompilowania `M4` .

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

### <a name="constructors"></a>Konstruktory

Konstruktory w klasach i strukturach zgodnych ze specyfikacją CLS muszą być zgodne z następującymi regułami:

* Konstruktor klasy pochodnej musi wywoływać konstruktora wystąpienia swojej klasy bazowej przed uzyskaniem dostępu do danych dziedziczonego wystąpienia. To wymaganie wynika z faktu, że konstruktory klasy bazowej nie są dziedziczone przez ich klasy pochodne. Ta zasada nie ma zastosowania do struktur, które nie obsługują bezpośredniego dziedziczenia.

  Zazwyczaj kompilatory wymuszają tę regułę niezależnie od zgodności ze specyfikacją CLS, jak pokazano w poniższym przykładzie. Tworzy `Doctor` klasę, która jest pochodną `Person` klasy, ale `Doctor` nie wywołuje `Person` konstruktora klasy w celu zainicjowania pól dziedziczonego wystąpienia.

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

* Konstruktor obiektów nie może zostać wywołany z wyjątkiem tworzenia obiektu. Ponadto nie można dwukrotnie zainicjować obiektu. Na przykład oznacza to, że `Object.MemberwiseClone` nie może wywoływać konstruktorów.

### <a name="properties"></a>Właściwości

Właściwości typów zgodnych ze specyfikacją CLS muszą być zgodne z następującymi regułami:

* Właściwość musi mieć metody ustawiającej, pobierającej lub obu. W zestawie są one implementowane jako metody specjalne, co oznacza, że będą wyświetlane jako oddzielne metody (metoda pobierająca nosi nazwę `get` \_ *PropertyName* , a Metoda ustawiająca to `set` \_ *PropertyName*) oznaczona jako `SpecialName` w metadanych zestawu. Kompilator języka C# wymusza tę regułę automatycznie bez konieczności stosowania <xref:System.CLSCompliantAttribute> atrybutu.

* Typ właściwości jest typem zwracanym metody pobierającej właściwości i ostatnim argumentem metody ustawiającej. Te typy muszą być zgodne ze specyfikacją CLS, a argumenty nie mogą być przypisywane do właściwości przez odwołanie (oznacza to, że nie mogą być wskaźnikami zarządzanymi).

* Jeśli właściwość ma zarówno metodę pobierającą, jak i setter, muszą jednocześnie być wirtualne, zarówno statyczne, jak i oba wystąpienia. Kompilator języka C# automatycznie wymusza tę regułę za pomocą składni definicji właściwości.

### <a name="events"></a>Zdarzenia

Zdarzenie jest definiowane przy użyciu jego nazwy i typu. Typ zdarzenia jest delegatem, który jest używany do wskazania zdarzenia. Na przykład `DbConnection.StateChange` zdarzenie jest typu `StateChangeEventHandler` . Oprócz samego zdarzenia trzy metody z nazwami na podstawie nazwy zdarzenia dostarczają implementację zdarzenia i są oznaczone jako `SpecialName` w metadanych zestawu:

* Metoda dodawania obsługi zdarzeń o nazwie `add` _*EventName*. Na przykład Metoda subskrypcji zdarzeń dla `DbConnection.StateChange` zdarzenia ma nazwę `add_StateChange` .

* Metoda usuwania programu obsługi zdarzeń o nazwie `remove` _*EventName*. Na przykład metoda usuwania dla `DbConnection.StateChange` zdarzenia ma nazwę `remove_StateChange` .

* Metoda wskazująca, że zdarzenie wystąpiło o nazwie `raise` \_ *EventName*.

> [!NOTE]
> Większość reguł Common Language Specification dotyczących zdarzeń jest implementowanych przez kompilatory języka i są przezroczyste dla deweloperów składników.

Metody dodawania, usuwania i wywoływania zdarzenia muszą mieć taki sam dostęp. Muszą one również być statyczne, wystąpienia lub wirtualne. Metody dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia. Metody Add i Remove muszą być obecne lub być nieobecne.

W poniższym przykładzie zdefiniowano klasę zgodną ze specyfikacją CLS o nazwie `Temperature` , która wywołuje `TemperatureChanged` zdarzenie, jeśli zmiana temperatury między dwoma odczytami jest równa lub przekracza wartość progową. `Temperature`Klasa jawnie definiuje metodę, `raise_TemperatureChanged` Aby można było wybiórczo wykonywać procedury obsługi zdarzeń.

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

### <a name="overloads"></a>Przeciążenia

Common Language Specification nakładają następujące wymagania dotyczące przeciążonych elementów członkowskich:

* Elementy członkowskie mogą być przeciążone na podstawie liczby parametrów i typu każdego parametru. Konwencja wywoływania, zwracany typ, Modyfikatory niestandardowe stosowane do metody lub jej parametru oraz czy parametry są przesyłane przez wartość lub przez odwołanie nie są brane pod uwagę podczas różnicowania przeciążeń. Aby zapoznać się z przykładem, zobacz kod wymagający, aby nazwy muszą być unikatowe w zakresie w sekcji [konwencji nazewnictwa](#naming-conventions) .

* Tylko właściwości i metody mogą być przeciążone. Pola i zdarzenia nie mogą być przeciążone.

* Metody generyczne mogą być przeciążone na podstawie liczby parametrów ogólnych.

> [!NOTE]
> `op_Explicit`Operatory i `op_Implicit` są wyjątkami od reguły, która zwraca wartość nie jest uważana za część sygnatury metody w celu rozpoznania przeciążenia. Te dwa operatory mogą być przeciążone na podstawie zarówno ich parametrów, jak i ich wartości zwracanej.

### <a name="exceptions"></a>Wyjątki

Obiekty wyjątków muszą pochodzić od klasy [System. Exception](xref:System.Exception) lub z innego typu pochodnego od `System.Exception` . Poniższy przykład ilustruje błąd kompilatora, który powstaje, gdy Klasa niestandardowa o nazwie `ErrorClass` jest używana do obsługi wyjątków.

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

Aby naprawić ten błąd, `ErrorClass` Klasa musi dziedziczyć po elemencie `System.Exception` . Ponadto Właściwość Message musi zostać zastąpiona. Poniższy przykład koryguje te błędy, aby zdefiniować `ErrorClass` klasę, która jest zgodna ze specyfikacją CLS.

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

Zestawy platformy In.NET Framework, atrybuty niestandardowe oferują rozszerzalny mechanizm do przechowywania atrybutów niestandardowych i pobierania metadanych dotyczących obiektów programistycznych, takich jak zestawy, typy, elementy członkowskie i parametry metody. Atrybuty niestandardowe muszą pochodzić od klasy [System. Attribute](xref:System.Attribute) lub z typu pochodnego od `System.Attribute` .

Poniższy przykład narusza tę regułę. Definiuje `NumericAttribute` klasę, która nie pochodzi od `System.Attribute` . Błąd kompilatora występuje tylko wtedy, gdy jest stosowany atrybut niezgodny ze specyfikacją CLS, nie gdy Klasa jest zdefiniowana.

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

Konstruktor lub właściwości atrybutu zgodnego ze specyfikacją CLS mogą uwidaczniać tylko następujące typy:

* [Boolean](xref:System.Boolean)

* [Bajc](xref:System.Byte)

* [Delikatn](xref:System.Char)

* [Double](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Single](xref:System.Single)

* [Ciąg](xref:System.String)

* [Typ](xref:System.Type)

* Wszystkie typy wyliczeniowe, których typem podstawowym jest `Byte` , `Int16` , `Int32` , lub `Int64` .

W poniższym przykładzie zdefiniowano `DescriptionAttribute` klasę, która pochodzi od [atrybutu](xref:System.Attribute). Konstruktor klasy ma parametr typu `Descriptor` , więc Klasa nie jest zgodna ze specyfikacją CLS. Kompilator języka C# emituje ostrzeżenie, ale kompiluje się pomyślnie.

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

Atrybut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) służy do wskazywania, czy element programu jest zgodny z Common Language Specification. `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)`Konstruktor zawiera jeden wymagany parametr, *iszgodna*, który wskazuje, czy element programu jest zgodny ze specyfikacją CLS.

W czasie kompilacji kompilator wykrywa niezgodne elementy, które są zgodne ze specyfikacją CLS, i emituje ostrzeżenie. Kompilator nie emituje ostrzeżeń dla typów lub elementów członkowskich, które są jawnie zadeklarowane jako niezgodne.

Deweloperzy składników mogą używać `CLSCompliantAttribute` atrybutu na dwa sposoby:

* Do definiowania części interfejsu publicznego uwidocznionych przez składnik, który jest zgodny ze specyfikacją CLS, i części, które nie są zgodne ze specyfikacją CLS. Gdy atrybut jest używany do oznaczania określonych elementów programu jako zgodnych ze specyfikacją CLS, jego użycie gwarantuje, że te elementy są dostępne we wszystkich językach i narzędziach przeznaczonych dla .NET Framework.

* Aby zapewnić, że interfejs publiczny biblioteki składników uwidacznia tylko elementy programu, które są zgodne ze specyfikacją CLS. Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory zwykle wygenerują ostrzeżenie.

> [!WARNING]
> W niektórych przypadkach kompilatory języka wymuszają reguły zgodne ze specyfikacją CLS niezależnie od tego, czy `CLSCompliantAttribute` atrybut jest używany. Na przykład Definiowanie `*static` elementu członkowskiego w interfejsie narusza regułę CLS. Jednak w przypadku zdefiniowania `*static` elementu członkowskiego w interfejsie kompilator języka C# wyświetli komunikat o błędzie i nie będzie mógł skompilować aplikacji.

`CLSCompliantAttribute`Atrybut jest oznaczony atrybutem [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) o wartości `AttributeTargets.All` . Ta wartość umożliwia zastosowanie `CLSCompliantAttribute` atrybutu do dowolnego elementu programu, w tym zestawów, modułów, typów (klasy, struktury, wyliczenia, interfejsy i delegatów), elementów członkowskich typu (konstruktorów, metod, właściwości, pól i zdarzeń), parametrów, parametrów ogólnych i zwracanych wartości. Jednakże, w przypadku, należy zastosować atrybut tylko do zestawów, typów i elementów członkowskich typu. W przeciwnym razie kompilatory ignorują atrybut i kontynuuje generowanie ostrzeżeń kompilatora zawsze wtedy, gdy napotkają niezgodny parametr, parametr ogólny lub wartość zwracaną w interfejsie publicznym biblioteki.

Wartość `CLSCompliantAttribute` atrybutu jest dziedziczona przez zawarte elementy programu. Na przykład, jeśli zestaw jest oznaczony jako zgodny ze specyfikacją CLS, jego typy są również zgodne ze specyfikacją CLS. Jeśli typ jest oznaczony jako zgodny ze specyfikacją CLS, jego zagnieżdżone typy i elementy członkowskie są również zgodne ze specyfikacją CLS.

Dziedziczonej zgodności można jawnie zastępować przez zastosowanie `CLSCompliantAttribute` atrybutu do zawartego elementu programu. Na przykład można użyć `CLSCompliantAttribute` atrybutu z wartością *iszgodnej* , `false` Aby zdefiniować niezgodny typ w zgodnym zestawie, i można użyć atrybutu z wartością *iszgodnej* , `true` Aby zdefiniować zgodny typ w niezgodnym zestawie. Istnieje również możliwość zdefiniowania niezgodnych elementów członkowskich w typie zgodnym. Niezgodny typ nie może jednak mieć zgodnych elementów członkowskich, dlatego nie można użyć atrybutu z wartością *Iszgodnej* , `true` Aby zastąpić dziedziczenie z niezgodnego typu.

Podczas tworzenia składników należy zawsze używać `CLSCompliantAttribute` atrybutu, aby wskazać, czy zestaw, jego typy i jego elementy członkowskie są zgodne ze specyfikacją CLS.

Aby utworzyć składniki zgodne ze specyfikacją CLS:

1. Użyj, `CLSCompliantAttribute` Aby oznaczyć zestaw jako zgodny ze specyfikacją CLS.

2. Oznacz wszystkie publicznie uwidocznione typy w zestawie, które nie są zgodne ze specyfikacją CLS jako niezgodne.

3. Oznacz wszystkie publicznie uwidocznionych członków w typach zgodnych ze specyfikacją CLS jako niezgodne.

4. Podaj alternatywę zgodną ze specyfikacją CLS dla członków niezgodnych ze specyfikacją CLS.

Jeśli wszystkie niezgodne typy i elementy członkowskie zostały oznaczone pomyślnie, kompilator nie powinien emitować ostrzeżeń o braku zgodności. Należy jednak wskazać, które elementy członkowskie nie są zgodne ze specyfikacją CLS, i wyświetlić ich alternatywy zgodne ze specyfikacją CLS w dokumentacji produktu.

Poniższy przykład używa `CLSCompliantAttribute` atrybutu w celu zdefiniowania zestawu zgodnego ze specyfikacją CLS i typu, `CharacterUtilities` , który ma dwie składowe niezgodne ze specyfikacją CLS. Ponieważ oba elementy członkowskie są oznaczone `CLSCompliant(false)` atrybutem, kompilator nie generuje ostrzeżeń. Klasa zawiera również alternatywę zgodną ze specyfikacją CLS dla obu tych metod. Zwykle należy dodać dwa przeciążenia do `ToUTF16` metody, aby zapewnić alternatywy zgodne ze specyfikacją CLS. Jednak ponieważ metody nie mogą być przeciążone w oparciu o wartość zwracaną, nazwy metod zgodnych ze specyfikacją CLS różnią się od nazw metod niezgodnych.

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

Jeśli tworzysz aplikację, a nie bibliotekę (czyli jeśli nie ujawniasz typów lub elementów członkowskich, które mogą być używane przez innych deweloperów aplikacji), zgodność ze specyfikacją CLS elementów programu, których używa aplikacja, jest interesująca tylko wtedy, gdy język ich nie obsługuje. W takim przypadku kompilator języka wygeneruje błąd podczas próby użycia elementu niezgodnego ze specyfikacją CLS.

## <a name="cross-language-interoperability"></a>Współdziałanie między językami

Niezależność od języka ma wiele możliwych znaczenia. Jedno z tych problemów obejmuje bezproblemowe zużywanie typów pisanych w jednym języku z aplikacji w innym języku. Drugie znaczenie, które jest fokusem tego artykułu, obejmuje łączenie kodu pisanego w wielu językach w jeden zestaw .NET Framework.

Poniższy przykład ilustruje współdziałanie między językami przez utworzenie biblioteki klas o nazwie Utilities. dll, która zawiera dwie klasy, `NumericLib` i `StringLib` . `NumericLib`Klasa jest zapisywana w języku C#, a `StringLib` Klasa jest zapisywana w Visual Basic. Oto kod źródłowy dla `StringUtil.vb` , który zawiera pojedynczy element członkowski, `ToTitleCase` w swojej `StringLib` klasie.

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

Oto kod źródłowy dla NumberUtil.cs, który definiuje `NumericLib` klasę, która ma dwa elementy członkowskie, `IsEven` i `NearZero` .

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

Aby spakować dwie klasy w jednym zestawie, należy skompilować je do modułów. Aby skompilować plik kodu źródłowego Visual Basic do modułu, użyj tego polecenia:

```console
vbc /t:module StringUtil.vb
```

Aby skompilować plik kodu źródłowego C# do modułu, użyj tego polecenia:

```console
csc /t:module NumberUtil.cs
```

Następnie użyj narzędzia link (link. exe), aby skompilować dwa moduły do zestawu:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Poniższy przykład wywołuje `NumericLib.NearZero` `StringLib.ToTitleCase` metody i. Zarówno kod Visual Basic, jak i kod C# są w stanie uzyskać dostęp do metod w obu klasach.

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

Aby skompilować kod Visual Basic, użyj tego polecenia:

```console
vbc example.vb /r:UtilityLib.dll
```

Aby skompilować przy użyciu języka C#, Zmień nazwę kompilatora z VBC na CSC i Zmień rozszerzenie pliku z. vb na. cs:

```console
csc example.cs /r:UtilityLib.dll
```
