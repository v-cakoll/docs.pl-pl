---
title: Niezależność językowa i składniki niezależne od języka
description: Dowiedz się, jak można tworzyć w jednym z wielu obsługiwanych języków w .NET, takich jak C#, C++/CLI, F#, IronPython, VB, Visual COBOL i PowerShell.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: e1f419dd57c1e90d7ebb57ef572f338a34d1c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73423635"
---
# <a name="language-independence-and-language-independent-components"></a>Niezależność językowa i składniki niezależne od języka

.NET jest niezależny od języka. Oznacza to, że jako deweloper można rozwijać w jednym z wielu języków, które są przeznaczone dla implementacji .NET, takich jak C#, F#i Visual Basic. Można uzyskać dostęp do typów i elementów członkowskich bibliotek klas opracowanych dla implementacji .NET bez konieczności znać język, w którym zostały pierwotnie napisane i bez konieczności przestrzegania żadnych konwencji języka oryginalnego. Jeśli jesteś deweloperem składników, składnik może być dostępny dla dowolnej aplikacji .NET, niezależnie od jego języka.

> [!NOTE]
> W pierwszej części tego artykułu omówiono tworzenie składników niezależnych od języka — oznacza to, że składniki, które mogą być używane przez aplikacje, które są napisane w dowolnym języku. Można również utworzyć pojedynczy składnik lub aplikację z kodu źródłowego napisanego w wielu językach; zobacz [Interoperacyjność między językami](#cross-language-interoperability) w drugiej części tego artykułu.

Aby w pełni wchodzić w interakcje z innymi obiektami napisanymi w dowolnym języku, obiekty muszą uwidaczniać do wywoływania tylko te funkcje, które są wspólne dla wszystkich języków. Ten wspólny zestaw funkcji jest zdefiniowany przez specyfikację języka wspólnego (CLS), który jest zestawem reguł, które mają zastosowanie do wygenerowanych zestawów. Specyfikacja języka wspólnego jest zdefiniowana w partycji I, klauzule 7 do 11 [standardu ECMA-335: Wspólna infrastruktura językowa](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Jeśli składnik jest zgodny ze specyfikacją języka wspólnego, jest gwarantowana, aby być zgodne z CLS i można uzyskać dostęp z kodu w zestawach napisanych w dowolnym języku programowania, który obsługuje CLS. Można określić, czy składnik jest zgodny ze specyfikacją języka wspólnego w czasie kompilacji, stosując [clscompliantattribute](xref:System.CLSCompliantAttribute) atrybut do kodu źródłowego. Aby uzyskać więcej informacji, zobacz [CLSCompliantAttribute atrybut .](#the-clscompliantattribute-attribute)

W tym artykule:

* [Reguły zgodności z CLS](#cls-compliance-rules)

  * [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures)

  * [Konwencje nazewnictwa](#naming-conventions)

  * [Konwersja typu](#type-conversion)

  * [Tablice](#arrays)

  * [Interfejsy](#interfaces)

  * [Wyliczenia](#enumerations)

  * [Wpisywanie elementów członkowskich w ogóle](#type-members-in-general)

  * [Dostępność elementów członkowskich](#member-accessibility)

  * [Typy ogólne i elementy członkowskie](#generic-types-and-members)

  * [Konstruktory](#constructors)

  * [Właściwości](#properties)

  * [Zdarzenia](#events)

  * [Overloads](#overloads)

  * [Wyjątki](#exceptions)

  * [Atrybuty](#attributes)

* [Atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute)

* [Współdziałanie między językami](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>Reguły zgodności z CLS

W tej sekcji omówiono reguły tworzenia składnika zgodnego ze specyfikacją CLS. Aby uzyskać pełną listę reguł, zobacz partycja I, klauzula 11 [standardu ECMA-335: Wspólna infrastruktura językowa](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Specyfikacja języka wspólnego omawia każdą regułę zgodności z usługą CLS, ponieważ ma ona zastosowanie do konsumentów (deweloperzy, którzy programowo uzyskują dostęp do składnika, który jest zgodny ze specyfikacją CLS), struktur (deweloperzy, którzy używają kompilatora języka do tworzenia Biblioteki zgodne ze specyfikacją CLS) i extendery (deweloperzy, którzy tworzą narzędzie, takie jak kompilator języka lub analizator kodu, który tworzy składniki zgodne ze specyfikacją CLS). W tym artykule skupiono się na zasadach, które mają zastosowanie do struktur. Należy jednak zauważyć, że niektóre reguły, które mają zastosowanie do extenders mogą również mieć zastosowanie do zestawów, które są tworzone przy użyciu [Reflection.Emit](xref:System.Reflection.Emit).

Aby zaprojektować składnik niezależny od języka, należy zastosować tylko reguły zgodności z cls do interfejsu publicznego składnika. Implementacja prywatna nie musi być zgodna ze specyfikacją.

> [!IMPORTANT]
> Reguły zgodności z cls mają zastosowanie tylko do interfejsu publicznego składnika, a nie do jego prywatnej implementacji.

Na przykład niepodpisane liczby całkowite inne niż [Bajt](xref:System.Byte) nie są zgodne ze specyfikacją CLS. Ponieważ `Person` klasa w poniższym przykładzie `Age` udostępnia właściwość typu [UInt16](xref:System.UInt16), poniższy kod wyświetla ostrzeżenie kompilatora.

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

Klasę person zgodną ze specyfikacją CLS `Age` można `UInt16` wprowadzić, zmieniając typ właściwości z [Int16](xref:System.Int16), która jest zgodną ze specyfikacją CLS, 16-bitową liczbą całkowitą z podpisem. Nie trzeba zmieniać typu pola `personAge` prywatnego.

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

* Definicje publicznych członków klas publicznych i definicje elementów członkowskich dostępne dla klas pochodnych (czyli członków chronionych).

* Parametry i zwracatypy metod publicznych klas publicznych oraz parametry i zwracane typy metod dostępnych dla klas pochodnych.

Reguły zgodności z cls są wymienione w poniższej tabeli. Tekst zasad jest dosłownie zaczerpnięty ze [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), czyli Copyright 2012 by Ecma International. Bardziej szczegółowe informacje na temat tych reguł można znaleźć w poniższych sekcjach.

Kategoria | Zobacz | Reguła | Numer reguły
-------- | --- | ---- | -----------
Ułatwienia dostępu | [Dostępność elementów członkowskich](#member-accessibility) | Ułatwienia dostępu nie mogą być zmieniane podczas zastępowania metod dziedziczonych, `family-or-assembly`z wyjątkiem sytuacji, gdy zastępowanie metody dziedziczonej z innego zestawu z ułatwieniami dostępu . W takim przypadku zastąpienie ma `family`dostępność . | 10
Ułatwienia dostępu | [Dostępność elementów członkowskich](#member-accessibility) | Widoczność i dostępność typów i elementów członkowskich musi być taka, aby typy w podpisie każdego członka były widoczne i dostępne w każdym przypadku, gdy sam członek jest widoczny i dostępny. Na przykład metoda publiczna, która jest widoczna poza jego zestaw nie ma argumentu, którego typ jest widoczny tylko w zestawie. Widoczność i dostępność typów tworzących wystąpienie typu ogólnego używanego w podpisie każdego członka muszą być widoczne i dostępne za każdym razem, gdy sam element członkowski jest widoczny i dostępny. Na przykład uprzedzony typ ogólny obecny w podpisie elementu członkowskiego, który jest widoczny poza jego zestawem, nie może mieć ogólnego argumentu, którego typ jest widoczny tylko w zestawie. | 12
Tablice | [Tablice](#arrays) | Tablice mają elementy o typie zgodnym ze specyfikacją CLS, a wszystkie wymiary tablicy mają dolne granice zera. Tylko fakt, że element jest tablicą i typ elementu tablicy jest wymagane do rozróżnienia przeciążeń. Gdy przeciążenie jest oparte na dwóch lub więcej typów tablicy typy elementów mają być nazwane typy. | 16
Atrybuty | [Atrybuty](#attributes) | Atrybuty mają typ [System.Attribute](xref:System.Attribute)lub typ dziedziczący z niego. | 41
Atrybuty | [Atrybuty](#attributes) | CLS zezwala tylko podzbiór kodowania atrybutów niestandardowych. Jedynymi typami, które pojawią się w tych kodowaniach są (patrz Partycja IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), oraz każdy typ wyliczenia oparty na podstawowym typie całkowitym zgodnym ze specyfikacją CLS. | 34
Atrybuty | [Atrybuty](#attributes) | CLS nie zezwala na publicznie widoczne wymagane`modreq`modyfikatory ( , patrz partycja`modopt`II), ale zezwala na opcjonalne modyfikatory ( , patrz Partycja II) nie rozumie. | 35
Konstruktorów | [Konstruktory](#constructors) | Konstruktor obiektu wywołaniektóre konstruktora wystąpienia jego klasy podstawowej, zanim nastąpi dostęp do danych wystąpienia dziedziczonego. (Nie dotyczy to typów wartości, które nie muszą mieć konstruktorów).  | 21
Konstruktorów | [Konstruktory](#constructors) | Konstruktora obiektu nie może być wywoływana z wyjątkiem jako część tworzenia obiektu, a obiekt nie może być inicjowany dwukrotnie. | 22
Wyliczenia | [Wyliczenia](#enumerations) | Podstawowym typem wyliczenia jest wbudowany typ całkowity CLS, nazwa pola jest "value__", a pole to `RTSpecialName`jest oznaczone. |  7
Wyliczenia | [Wyliczenia](#enumerations) | Istnieją dwa różne rodzaje wyliczenia, wskazane przez obecność lub brak [System.FlagsAttribute](xref:System.FlagsAttribute) (zobacz Partition IV Library) atrybut niestandardowy. Jeden reprezentuje nazwane wartości całkowite; drugi reprezentuje nazwane flagi bitowe, które można połączyć w celu wygenerowania wartości bez nazwy. Wartość nie `enum` jest ograniczona do określonych wartości. |  8
Wyliczenia | [Wyliczenia](#enumerations) | Literały pola statyczne wyliczenia mają typ samego wyliczenia. |  9
Zdarzenia | [Zdarzenia](#events) | Metody implementowania zdarzenia są oznaczone `SpecialName` w metadanych. |29
Zdarzenia | [Zdarzenia](#events) | Dostępność zdarzenia i jego dostępu jest identyczna. |30
Zdarzenia | [Zdarzenia](#events) | Metody `add` `remove` i metody zdarzenia są obecne lub nieobecne. |31
Zdarzenia | [Zdarzenia](#events) | I `add` `remove` metody zdarzenia każdy przyjmuje jeden parametr, którego typ określa typ zdarzenia i które są wyprowadzone z [System.Delegate](xref:System.Delegate). |32
Zdarzenia | [Zdarzenia](#events) | Zdarzenia muszą być zgodne z określonym wzorcem nazewnictwa. Atrybut SpecialName, o którym mowa w zasadzie CLS 29, jest ignorowany w odpowiednich porównaniach nazw i stosuje się do reguł identyfikatora.  |33
Wyjątki | [Wyjątki](#exceptions) | Obiekty, które są generowane jest typu [System.Exception](xref:System.Exception) lub typu dziedziczenia z niego. Niemniej jednak metody zgodne ze specyfikacją CLS nie są wymagane do blokowania propagacji innych typów wyjątków. | 40
Ogólne | [Reguły zgodności z CLS](#cls-compliance-rules) | Reguły CLS mają zastosowanie tylko do tych części typu, które są dostępne lub widoczne poza zestawem definiującym. | 1
Ogólne | [Reguły zgodności z CLS](#cls-compliance-rules) | Członkowie typów niezgodnych ze specyfikacją CLS nie mogą być oznaczani zgodnie z CLS. | 2
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Typy zagnieżdżone mają co najmniej tyle parametrów ogólnych, co typ otaczający. Parametry ogólne w typie zagnieżdżonym odpowiadają położeniu parametrom ogólnym w jego typie otaczającym.  | 42
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Nazwa typu ogólnego koduje liczbę parametrów typu zadeklarowanych na typ ie niezagnieżdżonym lub nowo wprowadzonych do typu, jeśli są zagnieżdżone, zgodnie z regułami określonymi powyżej. | 43
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Typ rodzajowy deklaruje wystarczające ograniczenia, aby zagwarantować, że wszelkie ograniczenia dotyczące typu podstawowego lub interfejsów byłyby spełnione przez ograniczenia typu ogólnego. | 44
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Typy stosowane jako ograniczenia parametrów ogólnych same w sobie muszą być zgodne ze specyfikacją CLS. | 45
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Widoczność i dostępność elementów członkowskich (w tym typów zagnieżdżonych) w uprzednio typogólny uważa się za zakres do konkretnej wystąpienia, a nie ogólnej deklaracji typu jako całości. Zakładając, że to, zasady widoczności i dostępności reguły CLS 12 nadal mają zastosowanie. | 46
Typy ogólne | [Typy ogólne i elementy członkowskie](#generic-types-and-members) | Dla każdej abstrakcyjnej lub wirtualnej metody ogólnej musi istnieć domyślna konkretna (nieabstrakcyjna) implementacja | 47
Interfejsy | [Interfejsy](#interfaces) | Interfejsy zgodne ze specyfikacją CLS nie wymagają definiowania metod niezgodnych ze specyfikacją CLS w celu ich wdrożenia. | 18
Interfejsy | [Interfejsy](#interfaces) | Interfejsy zgodne ze specyfikacją CLS nie definiują metod statycznych ani nie definiują pól. | 19
Elementy członkowskie | [Wpisywanie elementów członkowskich w ogóle](#type-members-in-general) | Globalne pola statyczne i metody nie są zgodne ze specyfikacją CLS. | 36
Elementy członkowskie | -- | Wartość literału statycznego jest określona za pomocą metadanych inicjowania pola. Literału zgodnego ze specyfikacją CLS musi mieć wartość określoną w metadanych inicjowania pola, która jest dokładnie tego `enum`samego typu co literał (lub typu źródłowego, jeśli ten literał jest ). | 13
Elementy członkowskie | [Wpisywanie elementów członkowskich w ogóle](#type-members-in-general) | Ograniczenie vararg nie jest częścią CLS, a jedyną konwencją wywołującą obsługiwaną przez cls jest standardowa konwencja wywoływania zarządzanego. | 15
Konwencje nazewnictwa | [Konwencje nazewnictwa](#naming-conventions) | Zespoły następują po załączniku 7 do raportu technicznego 15 Standardu Unicode3.0, regulującego zestaw znaków dopuszczonych do uruchamiania i umieszczania ich w identyfikatorach, dostępnych online na [formularzach normalizacji Unicode.](https://www.unicode.org/unicode/reports/tr15/tr15-18.html) Identyfikatory są w formacie kanonicznym zdefiniowanym przez unicode normalization form C. Dla celów CLS dwa identyfikatory są takie same, jeśli ich małe mapowania (określone przez mapowania niewrażliwe na ustawienia regionalne Unicode, jeden do jednego małe litery) są takie same. Oznacza to, że aby w ramach CLS dwa identyfikatory były uważane za różne, różnią się one w większym niż tylko ich przypadku. Jednak w celu zastąpienia dziedziczonej definicji interfejsu i rdzenia cli wymaga precyzyjnego kodowania oryginalnej deklaracji. | 4
Przeciążenie | [Konwencje nazewnictwa](#naming-conventions) | Wszystkie nazwy wprowadzone w zakresie zgodnym ze specyfikacją CLS powinny być odrębne niezależnie od rodzaju, z wyjątkiem przypadków, gdy nazwy są identyczne i rozwiązane poprzez przeciążenie. Oznacza to, że podczas gdy CTS umożliwia jeden typ używać tej samej nazwy dla metody i pola, CLS nie. | 5
Przeciążenie | [Konwencje nazewnictwa](#naming-conventions) | Pola i typy zagnieżdżone różnią się tylko od porównania identyfikatorów, nawet jeśli CTS umożliwia odróżnienie odrębnych podpisów. Metody, właściwości i zdarzenia, które mają taką samą nazwę (przez porównanie identyfikatorów) różnią się o więcej niż tylko typ zwracany, z wyjątkiem przypadków określonych w zasadzie CLS 39 | 6
Przeciążenie | [Overloads](#overloads) | Tylko właściwości i metody mogą być przeciążone. | 37
Przeciążenie | [Overloads](#overloads) |Właściwości i metody mogą być przeciążone tylko na podstawie liczby i typów `op_Implicit` ich `op_Explicit`parametrów, z wyjątkiem operatorów konwersji o nazwie i , które mogą być również przeciążone na podstawie ich typu zwracanego. | 38
Przeciążenie | -- | Jeżeli dwie lub więcej metod zgodnych ze specyfikacją CLS zadeklarowanych w typie ma taką samą nazwę, a dla określonego zestawu wystąpień typu mają one ten sam parametr i typy zwracane, wszystkie te metody muszą być semantycznie równoważne w tych wystąpieniach typu. | 48
Właściwości | [Właściwości](#properties) | The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata. | 24
Właściwości | [Właściwości](#properties) | Akcesory właściwości muszą być statyczne, wszystkie są wirtualne lub wszystkie są wystąpieniem. | 26
Właściwości | [Właściwości](#properties) | Typ właściwości jest zwracany typu getter i typ ostatniego argumentu ustawiającego. Typy parametrów właściwości są typy parametrów do getter i typy wszystkich, ale parametr końcowy ustawiania. Wszystkie te typy muszą być zgodne ze specyfikacją CLS i nie mogą być zarządzane wskaźnikami (to oznacza, że nie są przekazywane przez odniesienie). | 27
Właściwości | [Właściwości](#properties) | Właściwości muszą być zgodne z określonym wzorcem nazewnictwa. Atrybut, `SpecialName` o którym mowa w zasadzie CLS 24, jest ignorowany w odpowiednich porównaniach nazw i stosuje się do zasad identyfikatora. Właściwość ma metodę metody getter, metodę ustawiania lub obie te metody. | 28
Konwersja typu | [Konwersja typu](#type-conversion) | Jeżeli zapewnione są op_Implicit lub op_Explicit, należy zapewnić alternatywne środki przymusu. | 39
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Typy wartości pudełkowych nie są zgodne ze specyfikacją CLS. | 3
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Wszystkie typy pojawiające się w podpisie muszą być zgodne ze specyfikacją CLS. Wszystkie typy tworzące wystąpienie typu ogólnego muszą być zgodne ze specyfikacją CLS. | 11
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Wpisane odwołania nie są zgodne ze specyfikacją CLS. | 14
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Typy wskaźników niezarządzanych nie są zgodne ze specyfikacją CLS. | 17
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Klasy, typy wartości i interfejsy zgodne ze specyfikacją CLS nie wymagają implementacji elementów członkowskich niezgodnych ze specyfikacją CLS | 20
Typy | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | [System.Object](xref:System.Object) jest zgodny ze specyfikacją CLS. Każda inna klasa zgodna ze specyfikacją CLS dziedziczy z klasy zgodnej ze specyfikacją CLS. | 23

### <a name="types-and-type-member-signatures"></a>Typy i podpisy elementów członkowskich typu

Typ [System.Object](xref:System.Object) jest zgodny ze specyfikacją CLS i jest typem podstawowym wszystkich typów obiektów w systemie typu .NET Framework. Dziedziczenie w .NET Framework jest niejawne (na przykład `Object` [String](xref:System.String) klasy niejawnie dziedziczy z klasy) lub jawne (na przykład [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) klasy jawnie dziedziczy z [ArgumentException](xref:System.ArgumentException) klasy, która jawnie dziedziczy z [Exception](xref:System.Exception) klasy. Aby typ pochodny był zgodny ze specyfikacją CLS, jego typ podstawowy musi być również zgodny ze specyfikacją CLS.

W poniższym przykładzie przedstawiono typ pochodny, którego typ podstawowy nie jest zgodny ze specyfikacją CLS. Definiuje klasę podstawową, `Counter` która używa niepodpisanej 32-bitowej liczby całkowitej jako licznika. Ponieważ klasa zapewnia funkcjonalność licznika przez zawijanie niepodpisanej liczby całkowitej, klasa jest oznaczona jako niezgodna ze specyfikacją CLS. W rezultacie klasa pochodna `NonZeroCounter`, również nie jest zgodna ze specyfikacją CLS.

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

Wszystkie typy, które pojawiają się w podpisach elementów członkowskich, w tym typ zwracany metody lub typ właściwości, muszą być zgodne ze specyfikacją CLS. Ponadto dla typów ogólnych:

* Wszystkie typy, które tworzą wystąpienie typu ogólnego musi być zgodny ze specyfikacją CLS.

* Wszystkie typy używane jako ograniczenia parametrów ogólnych muszą być zgodne ze specyfikacją CLS.

[System typowego typu](common-type-system.md) .NET zawiera szereg wbudowanych typów, które są obsługiwane bezpośrednio przez wspólny program językowy i są specjalnie zakodowane w metadanych zestawu. Z tych typów wewnętrznych typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS.

Typ zgodny ze specyfikacją CLS | Opis
------------------ | -----------
[Byte](xref:System.Byte) | 8-bitowa liczba całkowita bez znaku
[Int16](xref:System.Int16) | 16-bitowa liczba całkowita podpisana
[Int32](xref:System.Int32) | 32-bitowa liczba całkowita podpisana
[Int64 (int64)](xref:System.Int64) | 64-bitowa liczba całkowita podpisana
[Single](xref:System.Single) | Pojedyncza precyzja wartość zmiennoprzecinkową
[Podwójne](xref:System.Double) | Podwójna precyzja wartości zmiennoprzecinkowej
[Wartość logiczna](xref:System.Boolean) | typ wartości prawda lub fałsz
[Char](xref:System.Char) | Jednostka kodu kodowego zakodowanego uTF-16
[Dziesiętnych](xref:System.Decimal) | Liczba dziesiętna niezmienno-zmienna
[Intptr](xref:System.IntPtr) | Wskaźnik lub uchwyt rozmiaru zdefiniowanego przez platformę
[Ciąg](xref:System.String) | Kolekcja obiektów zero, jeden lub więcej Char

Typy wewnętrzne wymienione w poniższej tabeli nie są zgodne ze specyfikacją CLS.

Typ niezgodny | Opis | Alternatywa zgodna ze specyfikacją CLS
------------------ | ----------- | -------------------------
[Sbyte](xref:System.SByte) | 8-bitowy podpisany typ danych całkowitych | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16-bitowa liczba całkowita bez znaku | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32-bitowa liczba całkowita bez znaku | [Int64 (int64)](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64-bitowa liczba całkowita bez znaku | [Int64](xref:System.Int64) (może przepełnić), [BigInteger](xref:System.Numerics.BigInteger)lub [Double](xref:System.Double)
[Uintptr](xref:System.UIntPtr) | Niepodpisany wskaźnik lub uchwyt | [Intptr](xref:System.IntPtr)

Biblioteka klas .NET Framework lub inne biblioteki klas mogą zawierać inne typy, które nie są zgodne ze specyfikacją CLS; na przykład:

* Typy wartości w pudełku. Poniższy przykład języka C# tworzy klasę, która `int`ma `Value`właściwość publiczną typu * o nazwie . Ponieważ `int`* jest typu wartości zapakowane, kompilator flagi go jako niezgodne z CLS.

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

* Wpisane odwołania, które są specjalne konstrukcje, które zawierają odwołanie do obiektu i odwołanie do typu.

Jeśli typ nie jest zgodny ze specyfikacją CLS, należy zastosować atrybut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) z parametrem *isCompliant* z wartością `false` do niego. Aby uzyskać więcej informacji, zobacz [sekcję atrybutu CLSCompliantAttribute.](#the-clscompliantattribute-attribute)

Poniższy przykład ilustruje problem zgodności cls w podpisie metody i w funkcji wystąpienia typu ogólnego. Definiuje `InvoiceItem` klasę z właściwością typu [UInt32](xref:System.UInt32), właściwość typu [Nullable(Of UInt32)](xref:System.Nullable%601)i konstruktora z parametrami typu `UInt32` i `Nullable(Of UInt32)`. Otrzymasz cztery ostrzeżenia kompilatora podczas próby skompilowania tego przykładu.

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

Aby wyeliminować ostrzeżenia kompilatora, zastąp typy `InvoiceItem` niezgodne ze specyfikacją CLS w interfejsie publicznym zgodnymi typami:

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

Oprócz określonych typów wymienionych, niektóre kategorie typów nie są zgodne ze specyfikacją CLS. Należą do nich typy wskaźników niezarządzanych i typy wskaźników funkcji. Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej, aby utworzyć tablicę liczb całkowitych.

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

Dla klas abstrakcyjnych zgodnych ze specyfikacją `abstract` CLS (czyli klas oznaczonych jako c#), wszystkie elementy członkowskie klasy muszą być również zgodne ze specyfikacją CLS.

### <a name="naming-conventions"></a>Konwencje nazewnictwa

Ponieważ niektóre języki programowania są bez uwzględniania wielkości liter, identyfikatory (takie jak nazwy przestrzeni nazw, typy i elementy członkowskie) muszą się różnić o więcej niż wielkość liter. Dwa identyfikatory są uważane za równoważne, jeśli ich małe mapowania są takie same. Poniższy przykład języka C# definiuje `Person` dwie `person`klasy publiczne i . Ponieważ różnią się one tylko przez przypadek, kompilator C# flagi je jako niezgodne ze specyfikacją CLS.

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

Identyfikatory języka programowania, takie jak nazwy przestrzeni nazw, typów i elementów członkowskich, muszą być zgodne ze [standardem Unicode 3.0, sprawozdaniem technicznym 15, załącznikiem 7](https://www.unicode.org/reports/tr15/tr15-18.html). Oznacza to, że:

* Pierwszym znakiem identyfikatora może być dowolna litera jednoliterowa Unicode, mała litera, litera tytułu, litera modyfikatora, inna litera lub litera. Aby uzyskać informacje na temat kategorii znaków Unicode, zobacz [wyliczenie System.Globalization.UnicodeCategory.](xref:System.Globalization.UnicodeCategory)

* Kolejne znaki mogą pochodzić z dowolnej kategorii jako pierwszy znak, a także mogą zawierać znaki bez odstępów, odstępy łączące znaczniki, liczby dziesiętne, znaki interpunkcyjne łączników i kody formatowania.

Przed porównaniem identyfikatorów należy odfiltrować kody formatowania i przekonwertować identyfikatory na formularz Normalizacji Unicode C, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu zakodowanego w utf-16. Sekwencje znaków, które produkują te same jednostki kodu w unicode normalizacji formularza C nie są zgodne ze specyfikacją CLS. Poniższy przykład definiuje właściwość `Å`o nazwie , która składa się ze znaku ZNAK ANGSTROM SIGN `Å` (U +212B) i drugą właściwość o nazwie, która składa się ze znaku LATIN LITERA A z pierścieniem POWYŻEJ (U + 00C5). Kompilator C# oznacza kod źródłowy jako niezgodny ze specyfikacją CLS.

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

Nazwy elementów członkowskich w określonym zakresie (takie jak obszary nazw w zestawie, typy w obszarze nazw lub elementy członkowskie w obrębie typu) muszą być unikatowe, z wyjątkiem nazw, które są rozpoznawane przez przeciążenie. To wymaganie jest bardziej rygorystyczne niż w systemie typu wspólnego, co pozwala wielu elementów członkowskich w zakresie mają identyczne nazwy, o ile są one różne rodzaje elementów członkowskich (na przykład jeden jest metodą, a jeden jest pole). W szczególności dla członków typu:

* Pola i typy zagnieżdżone różnią się samą nazwą.

* Metody, właściwości i zdarzenia, które mają taką samą nazwę musi się różnić o więcej niż tylko zwracać typ.

W poniższym przykładzie przedstawiono wymóg, że nazwy elementów członkowskich muszą być unikatowe w ich zakresie. Definiuje klasę o `Converter` nazwie, która `Conversion`zawiera cztery elementy członkowskie o nazwie . Trzy są metody, a jeden jest właściwością. Metoda, która `Int64` zawiera parametr jest jednoznacznie nazwany, ale `Int32` dwie metody z parametrem nie są, ponieważ wartość zwracana nie jest uważany za część podpisu członka. Właściwość `Conversion` również narusza to wymaganie, ponieważ właściwości nie mogą mieć taką samą nazwę jak przeciążone metody.

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

Poszczególne języki zawierają unikatowe słowa kluczowe, więc języki, które są kierowane do wspólnego języka runtime musi również zapewnić pewien mechanizm odwoływania się do identyfikatorów (takich jak nazwy typów), które pokrywają się ze słowami kluczowymi. Na przykład `case` jest słowem kluczowym w języku C# i Visual Basic. Jednak w poniższym przykładzie języka Visual Basic jest w stanie `case` rozróżnić klasę o nazwie od słowa kluczowego `case` przy użyciu otwierania i zamykania nawiasów klamrowych. W przeciwnym razie w przykładzie może wywołać komunikat o błędzie "Słowo kluczowe nie jest prawidłowy jako identyfikator" i nie można skompilować.

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

Poniższy przykład języka C# jest w `case` stanie utworzyć wystąpienia klasy przy użyciu symbolu @ do rozróżniania identyfikatora od słowa kluczowego języka. Bez niego kompilator Języka C# wyświetlałby dwa komunikaty o błędach: "Typ oczekiwany" i "Nieprawidłowe wyrażenie termin "case".

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

Specyfikacja języka wspólnego definiuje dwa operatory konwersji:

* `op_Implicit`, który jest używany do rozszerzania konwersji, które nie powodują utraty danych lub precyzji. Na przykład struktura [dziesiętna](xref:System.Decimal) zawiera `op_Implicit` przeciążony operator do konwersji wartości `Decimal` typów całkowitych i wartości [Char](xref:System.Char) do wartości.

* `op_Explicit`, który jest używany do zawężania konwersji, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub precyzji. Na przykład `Decimal` struktura zawiera przeciążony `op_Explicit` operator do konwersji `Decimal` [double](xref:System.Double) i [single](xref:System.Single) wartości do `Single`i `Char`do konwersji `Decimal` wartości do wartości całkowitych, `Double`, , i .

Jednak nie wszystkie języki obsługują przeciążenie operatora lub definicji operatorów niestandardowych. Jeśli zdecydujesz się zaimplementować te operatory konwersji, należy również podać alternatywny sposób wykonania konwersji. Zalecamy podanie `From`metod Xxx `To`i Xxx.

W poniższym przykładzie zdefiniowano konwersje niejawne zgodne ze specyfikacją CLS. Tworzy `UDouble` klasę, która reprezentuje podpisaną podwójną precyzję, numer zmiennoprzecinkowy. Przewiduje ona konwersje `UDouble` `Double` niejawne z `UDouble` do `Single` `Double` i `UDouble`dla `Single` `UDouble`jawnych konwersji z do , do , i do . `ToDouble` Definiuje również metodę jako alternatywę dla niejawnego `ToSingle` `FromDouble`operatora `FromSingle` konwersji i , i metody jako alternatywy dla jawnych operatorów konwersji.

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

* Wszystkie wymiary tablicy muszą mieć dolną obwiednię zerową. Poniższy przykład tworzy tablicę niezgodną ze specyfikacją CLS z dolną obwiednią. Należy zauważyć, że pomimo obecności [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybut, kompilator nie wykrywa, że tablica zwracana przez `Numbers.GetTenPrimes` metodę nie jest zgodna ze specyfikacją CLS.

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

* Wszystkie elementy tablicy muszą składać się z typów zgodnych ze specyfikacją CLS. W poniższym przykładzie zdefiniowano dwie metody, które zwracają tablice niezgodne ze specyfikacją CLS. Pierwszy zwraca tablicę [wartości UInt32.](xref:System.UInt32) Drugi zwraca [object](xref:System.Object) tablicy, która zawiera `UInt32` [Int32](xref:System.Int32) i wartości. Mimo że kompilator identyfikuje pierwszą tablicę jako niezgodną ze względu na jej `UInt32` typ, nie rozpoznaje, że druga tablica zawiera elementy niezgodne ze specyfikacją CLS.

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

* Rozpoznawanie przeciążenia dla metod, które mają parametry tablicy opiera się na fakcie, że są one tablice i na ich typ elementu. Z tego powodu następująca definicja `GetSquares` metody przeciążonej jest zgodna ze specyfikacją CLS.

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

Interfejsy zgodne ze specyfikacją CLS mogą definiować właściwości, zdarzenia i metody wirtualne (metody bez implementacji). Interfejs zgodny ze specyfikacją CLS nie może mieć żadnej z następujących czynności:

* Metody statyczne lub pola statyczne. Kompilator C# generuje błędy kompilatora, jeśli zdefiniujesz statyczny element członkowski w interfejsie.

* Pola. C# kompilator generuje błędy kompilatora, jeśli zdefiniujesz pole w interfejsie.

* Metody, które nie są zgodne ze specyfikacją CLS. Na przykład następująca definicja interfejsu `INumber.GetUnsigned`zawiera metodę, która jest oznaczona jako niezgodna ze specyfikacją CLS. W tym przykładzie generuje ostrzeżenie kompilatora.

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

  Z powodu tej reguły typy zgodne ze specyfikacją CLS nie są wymagane do implementowania elementów członkowskich niezgodnych ze specyfikacją CLS. Jeśli struktura zgodna ze specyfikacją CLS udostępnia klasę, która implementuje interfejs zgodny ze specyfikacją CLS, powinna również zapewnić konkretne implementacje wszystkich elementów członkowskich niezgodnych ze specyfikacją CLS.

Kompilatory języka zgodne ze specyfikacją CLS muszą również zezwalać klasie na dostarczanie oddzielnych implementacji elementów członkowskich, które mają taką samą nazwę i podpis w wielu interfejsach. C# obsługuje implementacje interfejsu jawnego, aby zapewnić różne implementacje metod o identycznej nazwie. W poniższym przykładzie przedstawiono ten `Temperature` scenariusz, definiując klasę, która implementuje `ICelsius` i `IFahrenheit` interfejsy jako implementacje interfejsu jawnego.

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

* Podstawowym typem wyliczenia musi być wewnętrzna liczba całkowita zgodna ze specyfikacją CLS ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32)lub [Int64](xref:System.Int64)). Na przykład poniższy kod próbuje zdefiniować wyliczenie, którego podstawowym typem jest [UInt32](xref:System.UInt32) i generuje ostrzeżenie kompilatora.

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

* Typ wyliczenia musi mieć pole `Value__` pojedynczego wystąpienia `FieldAttributes.RTSpecialName` o nazwie oznaczone atrybutem. Dzięki temu można odwoływać się do wartości pola niejawnie.

* Wyliczenie zawiera literały pola statyczne, których typy są zgodne z typem samego wyliczenia. Na przykład, jeśli `State` zdefiniujesz wyliczenie `State.On` z wartościami `State.Off`i , `State.On` i `State.Off` są zarówno literały pola statyczne, których typem jest `State`.

* Istnieją dwa rodzaje wyliczeń:

  * Wyliczenie, które reprezentuje zestaw wzajemnie się wykluczają, nazwane wartości całkowite. Ten typ wyliczenia jest wskazywany przez brak atrybutu niestandardowego [System.FlagsAttribute.](xref:System.FlagsAttribute)

  * Wyliczenie, które reprezentuje zestaw flag bitowych, które można połączyć, aby wygenerować wartość bez nazwy. Ten typ wyliczenia jest wskazywany przez obecność Atrybutu niestandardowego [System.FlagsAttribute.](xref:System.FlagsAttribute)

Aby uzyskać więcej informacji, zobacz dokumentację struktury [wyliczenia.](xref:System.Enum)

* Wartość wyliczenia nie jest ograniczona do zakresu jego określonych wartości. Innymi słowy zakres wartości w wyliczeniu jest zakres jego wartości bazowej. Metoda służy `Enum.IsDefined` do określenia, czy określona wartość jest członkiem wyliczenia.

### <a name="type-members-in-general"></a>Wpisywanie elementów członkowskich w ogóle

Specyfikacja języka wspólnego wymaga dostępu do wszystkich pól i metod jako członków określonej klasy. W związku z tym globalne pola statyczne i metody (czyli pola statyczne lub metody, które są zdefiniowane z wyjątkiem typu) nie są zgodne ze specyfikacją CLS. Jeśli spróbujesz uwzględnić globalne pole lub metodę w kodzie źródłowym, kompilator C# generuje błąd kompilatora.

Specyfikacja języka wspólnego obsługuje tylko standardową konwencję wywoływania zarządzanego. Nie obsługuje niezarządzanych konwencji i metod wywoływania z listami argumentów zmiennych oznaczonych `varargs` słowem kluczowym. W przypadku list argumentów zmiennych, które są zgodne ze standardową konwencją wywoływania zarządzanego, należy użyć `ParamArray` atrybutu [ParamArrayAttribute](xref:System.ParamArrayAttribute) lub implementacji poszczególnych języków, takich jak `params` słowo kluczowe w języku C# i słowo kluczowe w języku Visual Basic.

### <a name="member-accessibility"></a>Dostępność elementów członkowskich

Zastąpienie dziedziczonego elementu członkowskiego nie może zmienić dostępności tego elementu członkowskiego. Na przykład metoda publiczna w klasie podstawowej nie może zostać zastąpiona metodą prywatną w klasie pochodnej. Istnieje jeden wyjątek: `protected internal` (w języku `Protected Friend` C#) lub (w języku Visual Basic) element członkowski w jednym zestawie, który jest zastępowany przez typ w innym zestawie.  W takim przypadku dostępność zastąpienia wynosi `Protected`.

W poniższym przykładzie przedstawiono błąd generowany, gdy atrybut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) jest ustawiony na `true`, i `Person`, który jest klasą wyprowadzoną z `Animal`, próbuje zmienić dostępność `Species` właściwości z publicznych na prywatne. Przykład kompiluje się pomyślnie, jeśli jego dostępność zostanie zmieniona na publiczne.

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

Typy w podpisie elementu członkowskiego muszą być dostępne, gdy ten element członkowski jest dostępny. Na przykład oznacza to, że element członkowski nie może zawierać parametru, którego typ jest prywatny, chroniony lub wewnętrzny. W poniższym przykładzie przedstawiono błąd kompilatora, który powoduje, że konstruktor `StringWrapper` klasy udostępnia wewnętrzną `StringOperationType` wartość wyliczenia, która określa, jak wartość ciągu powinna być opakowana.

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

Typy zagnieżdżone zawsze mają co najmniej tyle parametrów ogólnych, co ich typ otaczający. Odpowiadają one według pozycji parametrów ogólnych w typie otaczającym. Typ ogólny może również zawierać nowe parametry ogólne.

Relacja między parametrami typu ogólnego typu zawierającego i jego zagnieżdżonymi typami może być ukryta przez składnię poszczególnych języków. W poniższym przykładzie typ `Outer<T>` ogólny zawiera dwie `Inner1A` `Inner1B<U>`klasy zagnieżdżone i . Wywołania `ToString` metody, z której dziedziczy każda `Object.ToString`klasa, pokazują, że każda klasa zagnieżdżona zawiera parametry typu jej klasy zawierającej.

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

Nazwy typów ogólnych są kodowane w *nazwie*formularza '*n*, gdzie *nazwa* jest nazwą typu, *`* jest literałznaku, a *n* jest liczbą parametrów zadeklarowanych dla typu lub, dla zagnieżdżonych typów ogólnych, liczbą nowo wprowadzonych parametrów typu. To kodowanie nazw typów ogólnych jest szczególnie interesujące dla deweloperów, którzy używają odbicia, aby uzyskać dostęp do typów ogólnych skarg CLS w bibliotece.

Jeśli ograniczenia są stosowane do typu ogólnego, wszystkie typy używane jako ograniczenia muszą być również zgodne ze specyfikacją CLS. Poniższy przykład definiuje klasę `BaseClass` o nazwie, która nie jest zgodna ze specyfikacją CLS i klasę ogólną o nazwie, `BaseCollection` której parametr typu musi pochodzić od `BaseClass`. Ale `BaseClass` ponieważ nie jest zgodny ze specyfikacją CLS, kompilator emituje ostrzeżenie.

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

Jeśli typ ogólny pochodzi z ogólnego typu podstawowego, musi ponownie zadeklarować wszelkie ograniczenia, aby zagwarantować, że ograniczenia typu podstawowego są również spełnione. Poniższy przykład definiuje, `Number<T>` który może reprezentować dowolny typ liczbowy. Definiuje również `FloatingPoint<T>` klasę, która reprezentuje wartość zmiennoprzecinkową. Jednak kod źródłowy nie może skompilować, ponieważ nie `Number<T>` stosuje ograniczenia na (że `FloatingPoint<T>`T musi być typem wartości) do .

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

Przykład kompiluje pomyślnie, jeśli ograniczenie jest `FloatingPoint<T>` dodawany do klasy.

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

Specyfikacja języka wspólnego nakłada konserwatywny model wystąpienia dla typów zagnieżdżonych i chronionych elementów członkowskich. Otwórz typy ogólne nie można uwidaczniać pól lub elementów członkowskich z podpisami, które zawierają określone wystąpienia zagnieżdżonego, chronionego typu ogólnego. Typy nierodzajowe, które rozszerzają określony wystąpienia ogólnej klasy podstawowej lub interfejsu nie można uwidaczniać pól lub elementów członkowskich z podpisów, które zawierają różne wystąpienia zagnieżdżonego, chronionego typu ogólnego.

W poniższym przykładzie zdefiniowano typ ogólny `C1<T>` `C1<T>.N`i klasę chronioną . `C1<T>`ma dwie metody `M1` `M2`i . Jednak `M1` nie jest zgodny ze specyfikacją `C1<int>.N` CLS, `C1<T>`ponieważ próbuje zwrócić obiekt z . Druga klasa, `C2`pochodzi od `C1<long>`. Ma dwie metody `M3` i `M4`. `M3`nie jest zgodny ze specyfikacją `C1<int>.N` CLS, ponieważ próbuje `C1<long>`zwrócić obiekt z podklasy . Należy zauważyć, że kompilatory języka mogą być jeszcze bardziej restrykcyjne. W tym przykładzie visual basic wyświetla błąd podczas `M4`próby skompilowania .

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

Konstruktory w klasach i strukturach zgodnych ze specyfikacją CLS muszą być zgodne z następującymi regułami:

* Konstruktor klasy pochodnej musi wywołać konstruktora wystąpienia jego klasy podstawowej, zanim uzyskuje dostęp do danych wystąpienia dziedziczonego. Wymaganie to wynika z faktu, że konstruktory klasy podstawowej nie są dziedziczone przez ich klas pochodnych. Ta reguła nie ma zastosowania do struktur, które nie obsługują dziedziczenia bezpośredniego.

  Zazwyczaj kompilatory wymuszają tę regułę niezależnie od zgodności z cls, jak pokazano w poniższym przykładzie. Tworzy `Doctor` klasę, która jest pochodną `Person` klasy, `Doctor` ale klasa `Person` nie może wywołać konstruktora klasy, aby zainicjować pola wystąpienia dziedziczone.

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

* Nie można wywołać konstruktora obiektu, z wyjątkiem utworzenia obiektu. Ponadto obiekt nie może zostać zainicjowany dwukrotnie. Na przykład oznacza `Object.MemberwiseClone` to, że nie może wywoływać konstruktorów.

### <a name="properties"></a>Właściwości

Właściwości w typach zgodnych ze specyfikacją CLS muszą być zgodne z następującymi regułami:

* Właściwość musi mieć ustawiacz, getter lub obu. W zestawie są one implementowane jako metody specjalne, co oznacza, że będą one `get` \_wyświetlane jako oddzielne metody (getter `SpecialName` nosi nazwę *właściwości,* a setter jest `set` \_ *propertyname)* oznaczone jako w metadanych zestawu. Kompilator Języka C# wymusza tę regułę <xref:System.CLSCompliantAttribute> automatycznie bez konieczności stosowania atrybutu.

* Typ właściwości jest zwracany typ getter właściwości i ostatni argument setter. Te typy muszą być zgodne ze specyfikacją CLS, a argumenty nie mogą być przypisane do właściwości przez odwołanie (oznacza to, że nie mogą być zarządzane wskaźniki).

* Jeśli właściwość ma zarówno metody święceń, jak i metody ustawiania, muszą być zarówno wirtualne, statyczne lub oba wystąpienia. Kompilator C# automatycznie wymusza tę regułę za pomocą składni definicji właściwości.

### <a name="events"></a>Zdarzenia

Zdarzenie jest definiowane przez jego nazwę i typ. Typ zdarzenia jest pełnomocnikiem, który jest używany do wskazania zdarzenia. Na przykład `DbConnection.StateChange` zdarzenie jest `StateChangeEventHandler`typu . Oprócz samego zdarzenia trzy metody z nazwami opartymi na nazwie zdarzenia zapewniają implementację zdarzenia i są oznaczone jako `SpecialName` w metadanych zestawu:

* Metoda dodawania programu obsługi `add`zdarzeń o nazwie _*EventName*. Na przykład metoda subskrypcji zdarzeń `DbConnection.StateChange` dla `add_StateChange`zdarzenia nosi nazwę .

* Metoda usuwania programu obsługi zdarzeń `remove`o nazwie _*EventName*. Na przykład metoda usuwania `DbConnection.StateChange` zdarzenia nosi `remove_StateChange`nazwę .

* Metoda wskazująca, że zdarzenie wystąpiło, `raise` \_o nazwie *EventName*.

> [!NOTE]
> Większość reguł specyfikacji języka wspólnego dotyczące zdarzeń są implementowane przez kompilatory języka i są przezroczyste dla deweloperów składników.

Metody dodawania, usuwania i podnoszenia zdarzenia muszą mieć taką samą dostępność. Muszą być również statyczne, wystąpienia lub wirtualne. Metody dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia. Metody dodawania i usuwania muszą być obecne lub oba muszą być nieobecne.

W poniższym przykładzie zdefiniowano klasę `Temperature` zgodną `TemperatureChanged` ze specyfikacją CLS o nazwie, która wywołuje zdarzenie, jeśli zmiana temperatury między dwoma odczytami jest równa lub przekracza wartość progową. Klasa `Temperature` jawnie definiuje `raise_TemperatureChanged` metodę, dzięki czemu można selektywnie wykonywać programy obsługi zdarzeń.

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

Specyfikacja języka wspólnego nakłada następujące wymagania na przeciążone elementy członkowskie:

* Elementy członkowskie mogą być przeciążone na podstawie liczby parametrów i typu dowolnego parametru. Konwencja wywołująca, typ zwracany, modyfikatory niestandardowe stosowane do metody lub jej parametru i czy parametry są przekazywane przez wartość lub przez odwołanie nie są brane pod uwagę podczas rozróżniania między przeciążenia. Na przykład zobacz kod wymagania, że nazwy muszą być unikatowe w zakresie w [konwencji nazewnictwa](#naming-conventions) sekcji.

* Tylko właściwości i metody mogą być przeciążone. Pola i zdarzenia nie mogą być przeciążone.

* Metody ogólne mogą być przeciążone na podstawie liczby ich parametrów ogólnych.

> [!NOTE]
> I `op_Explicit` `op_Implicit` operatory są wyjątki od reguły, że wartość zwracana nie jest uważana za część podpisu metody dla rozpoznawania przeciążenia. Te dwa operatory mogą być przeciążone na podstawie zarówno ich parametrów, jak i ich wartości zwracanej.

### <a name="exceptions"></a>Wyjątki

Obiekty wyjątku muszą pochodzić z [System.Exception](xref:System.Exception) `System.Exception`lub z innego typu pochodzącego z . W poniższym przykładzie przedstawiono błąd kompilatora, który powoduje, że klasa niestandardowa o nazwie `ErrorClass` jest używany do obsługi wyjątków.

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

Aby poprawić ten `ErrorClass` błąd, klasa `System.Exception`musi dziedziczyć z . Ponadto Message właściwość musi zostać zastąpiona. W poniższym przykładzie poprawiono `ErrorClass` te błędy, aby zdefiniować klasę, która jest zgodna ze specyfikacją CLS.

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

In.NET zestawów Framework, atrybuty niestandardowe zapewniają rozszerzalny mechanizm przechowywania atrybutów niestandardowych i pobierania metadanych dotyczących obiektów programowania, takich jak zestawy, typy, elementy członkowskie i parametry metody. Atrybuty niestandardowe muszą pochodzić z [System.Attribute](xref:System.Attribute) lub `System.Attribute`z typu pochodzącego z .

Poniższy przykład narusza tę regułę. Definiuje `NumericAttribute` klasę, która nie pochodzi `System.Attribute`od . Należy zauważyć, że błąd kompilatora powoduje tylko wtedy, gdy atrybut niezgodny ze specyfikacją CLS jest stosowany, a nie po zdefiniowaniu klasy.

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

* [Wartość logiczna](xref:System.Boolean)

* [Byte](xref:System.Byte)

* [Char](xref:System.Char)

* [Podwójne](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64 (int64)](xref:System.Int64)

* [Single](xref:System.Single)

* [Ciąg](xref:System.String)

* [Typ](xref:System.Type)

* Każdy typ wyliczenia, `Byte`którego `Int16` `Int32`typem `Int64`bazowym jest , , lub .

W poniższym `DescriptionAttribute` przykładzie definiuje klasę, która pochodzi od [atrybutu](xref:System.Attribute). Konstruktor klasy ma `Descriptor`parametr typu, więc klasa nie jest zgodna ze specyfikacją CLS. Należy zauważyć, że kompilator Języka C# emituje ostrzeżenie, ale pomyślnie kompiluje.

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

[ClSCompliantAttribute](xref:System.CLSCompliantAttribute) Atrybut atrybut służy do wskazania, czy element programu jest zgodny ze specyfikacją języka wspólnego. Konstruktor `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` zawiera pojedynczy wymagany parametr, *isCompliant*, który wskazuje, czy element programu jest zgodny ze specyfikacją CLS.

W czasie kompilacji kompilator wykrywa niezgodne elementy, które są uważane za zgodne ze specyfikacją CLS i emituje ostrzeżenie. Kompilator nie emituje ostrzeżenia dla typów lub elementów członkowskich, które są jawnie uznane za niezgodne.

Deweloperzy składników `CLSCompliantAttribute` mogą używać tego atrybutu na dwa sposoby:

* Aby zdefiniować części interfejsu publicznego udostępniane przez składnik, które są zgodne ze specyfikacją CLS i części, które nie są zgodne ze specyfikacją CLS. Gdy atrybut jest używany do oznaczania określonych elementów programu jako zgodny chezb, jego użycie gwarantuje, że te elementy są dostępne ze wszystkich języków i narzędzi, które są przeznaczone dla .NET Framework.

* Aby upewnić się, że interfejs publiczny biblioteki składników udostępnia tylko elementy programu, które są zgodne ze specyfikacją CLS. Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory zazwyczaj wystawiają ostrzeżenie.

> [!WARNING]
> W niektórych przypadkach kompilatory języka wymuszają reguły `CLSCompliantAttribute` zgodne ze specyfikacją CLS, niezależnie od tego, czy atrybut jest używany. Na przykład definiowanie elementu członkowskiego `*static` w interfejsie narusza regułę CLS. Jednak jeśli zdefiniujesz element członkowski `*static` w interfejsie, kompilator C# wyświetla komunikat o błędzie i nie można skompilować aplikacji.

Atrybut `CLSCompliantAttribute` jest oznaczony atrybutem [AttributeUsageAttribute,](xref:System.AttributeUsageAttribute) który `AttributeTargets.All`ma wartość . Ta wartość umożliwia zastosowanie `CLSCompliantAttribute` atrybutu do dowolnego elementu programu, w tym zestawów, modułów, typów (klas, struktur, wyliczeń, interfejsów i delegatów), elementów członkowskich typu (konstruktorów, metod, właściwości, pól i zdarzeń), parametrów, parametrów ogólnych i wartości zwracanych. Jednak w praktyce należy zastosować atrybut tylko do zestawów, typów i elementów członkowskich typu. W przeciwnym razie kompilatory ignorują atrybut i nadal generują ostrzeżenia kompilatora, gdy napotkają niezgodny parametr, parametr ogólny lub wartość zwracaną w interfejsie publicznym biblioteki.

Wartość atrybutu `CLSCompliantAttribute` jest dziedziczona przez zawarte elementy programu. Na przykład jeśli złożenie jest oznaczone jako zgodne ze specyfikacją CLS, jego typy są również zgodne ze specyfikacją CLS. Jeśli typ jest oznaczony jako zgodny ze specyfikacją CLS, jego typy zagnieżdżone i elementy członkowskie są również zgodne ze specyfikacją CLS.

Dziedziczoną zgodność można jawnie `CLSCompliantAttribute` zastąpić, stosując atrybut do elementu programu zawartego. Na przykład można użyć `CLSCompliantAttribute` atrybutu z *isCompliant* wartość do definiowania `false` niezgodny typ w zestawie zgodnym i można użyć atrybutu z *isCompliant* wartość zdefiniowania zgodnego `true` typu w zestawie niezgodnym. Można również zdefiniować niezgodne elementy członkowskie w typie zgodnym. Jednak niezgodny typ nie może mieć zgodnych elementów członkowskich, więc nie `true` można użyć atrybutu z wartością *isCompliant,* aby zastąpić dziedziczenie z typu niezgodnego.

Podczas opracowywania składników, należy zawsze `CLSCompliantAttribute` używać atrybutu, aby wskazać, czy zestaw, jego typy i jego elementy członkowskie są zgodne ze specyfikacją CLS.

Aby utworzyć składniki zgodne ze specyfikacją CLS:

1. Użyj `CLSCompliantAttribute` oznaczenia złożenia jako zgodnego ze specyfikacją CLS.

2. Oznacz wszystkie publicznie uwidocznione typy w zestawie, które nie są zgodne ze specyfikacją CLS jako niezgodne.

3. Oznacz wszystkie publicznie uwycone elementy członkowskie w typach zgodnych ze specyfikacją CLS jako niezgodne.

4. Podaj alternatywę zgodną ze specyfikacją CLS dla elementów członkowskich niezgodnych ze specyfikacją CLS.

Jeśli pomyślnie oznaczyłeś wszystkie niezgodne typy i elementy członkowskie, kompilator nie powinien emitować żadnych ostrzeżeń o niezgodnościach. Należy jednak wskazać, którzy członkowie nie są zgodni ze specyfikacją CLS i wymienić ich alternatywy zgodne ze specyfikacją CLS w dokumentacji produktu.

W poniższym `CLSCompliantAttribute` przykładzie użyto atrybutu do zdefiniowania zestawu zgodnego ze specyfikacją CLS i typu, `CharacterUtilities`który ma dwa elementy członkowskie niezgodne ze specyfikacją CLS. Ponieważ oba elementy członkowskie `CLSCompliant(false)` są oznaczone atrybutem, kompilator nie generuje żadnych ostrzeżeń. Klasa zapewnia również alternatywę zgodną ze specyfikacją CLS dla obu metod. Zwykle dodalibyśmy dwa przeciążenia do `ToUTF16` metody, aby zapewnić alternatywy zgodne ze specyfikacją CLS. Ponieważ jednak metody nie mogą być przeciążone na podstawie wartości zwracanej, nazwy metod zgodnych ze specyfikacją CLS różnią się od nazw metod niezgodnych.

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

Jeśli tworzysz aplikację, a nie bibliotekę (to znaczy, jeśli nie ujawniasz typów lub elementów członkowskich, które mogą być używane przez innych deweloperów aplikacji), zgodność cls elementów programu, które zużywa aplikacja są interesujące tylko wtedy, gdy język ich nie obsługuje . W takim przypadku kompilator języka wygeneruje błąd podczas próby użycia elementu niezgodnego ze specyfikacją CLS.

## <a name="cross-language-interoperability"></a>Współdziałanie między językami

Niezależność językowa ma wiele możliwych znaczeń. Jedno znaczenie polega na bezproblemowym używaniu typów napisanych w jednym języku z aplikacji napisanej w innym języku. Drugie znaczenie, które jest przedmiotem tego artykułu, polega na łączeniu kodu napisanego w wielu językach w jeden zestaw .NET Framework.

W poniższym przykładzie przedstawiono współdziałanie międzyjęzykowe, tworząc bibliotekę klas o `NumericLib` `StringLib`nazwie Utilities.dll, która zawiera dwie klasy i . Klasa `NumericLib` jest napisana w języku C#, a klasa jest napisana `StringLib` w języku Visual Basic. Oto kod źródłowy dla `StringUtil.vb`, który `ToTitleCase`zawiera `StringLib` jeden element członkowski, w swojej klasie.

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

Oto kod źródłowy dla NumberUtil.cs, `NumericLib` który definiuje klasę, `NearZero`która ma dwa elementy członkowskie i `IsEven` .

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

Aby spakować dwie klasy w jednym zestawie, należy skompilować je do modułów. Aby skompilować plik kodu źródłowego języka Visual Basic do modułu, użyj następującego polecenia:

```console
vbc /t:module StringUtil.vb
```

Aby skompilować plik kodu źródłowego Języka C# do modułu, użyj następującego polecenia:

```console
csc /t:module NumberUtil.cs
```

Następnie użyj narzędzia Łącze (Link.exe), aby skompilować dwa moduły do zestawu:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Poniższy przykład następnie `NumericLib.NearZero` wywołuje `StringLib.ToTitleCase` i metody. Należy zauważyć, że zarówno kod języka Visual Basic, jak i kod Języka C# mają dostęp do metod w obu klasach.

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

Aby skompilować kod języka Visual Basic, użyj następującego polecenia:

```console
vbc example.vb /r:UtilityLib.dll
```

Aby skompilować z C#, zmień nazwę kompilatora z vbc na csc i zmień rozszerzenie pliku z .vb na .cs:

```console
csc example.cs /r:UtilityLib.dll
```
