---
title: Niezależność od języka i elementy niezależne od języka
description: 'Dowiedz się, jak można tworzyć w jednym z wielu języków w programie .NET, takich jak C#, C + +/ CLI, F # IronPython, VB, Visual COBOL i programu PowerShell.'
keywords: .NET, .NET Core
author: dotnet-bot
ms.author: dotnetcontent
ms.date: 07/22/2016
ms.topic: article
dev_langs:
- csharp
- vb
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2745bc67c926f50c28f5fdfb122ee94a85f020ec
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="language-independence-and-language-independent-components"></a>Niezależność od języka i elementy niezależne od języka

.NET jest niezależny od języka. Oznacza to, że deweloper, można tworzyć w jednym z wielu języków, które odnoszą się do implementacji .NET, takich jak C#, F # i Visual Basic. Dostępne typy i składniki bibliotek klas utworzonych dla implementacji .NET bez konieczności znajomości języka, w którym pierwotnie zostały zapisane i bez konieczności postępuj zgodnie z oryginalnego języka Konwencji. Jeśli jesteś deweloperem składnika składnika jest dostępna przez dowolną aplikację .NET, niezależnie od języka.

> [!NOTE]
> To pierwsza część w tym artykule omówiono tworzenie niezależny od języka składników — czyli składników, które mogą być używane przez aplikacje, które są zapisywane w dowolnym języku. Można również utworzyć pojedynczy składnik lub aplikacji z kodu źródłowego w wielu językach; zobacz [współdziałanie między językami](#cross-language-interoperability) w drugiej części tego artykułu. 

Pełni interakcję z innymi obiektami w dowolnym języku, obiektów musi ujawniać dotyczące obiektów wywołujących te funkcje, które są wspólne dla wszystkich języków. Ten zestaw typowych funkcji jest zdefiniowany przez wspólnej specyfikacji języka (CLS), który jest zestaw reguł stosowanych do zestawów wygenerowanych. Specyfikacja języka wspólnego jest zdefiniowany w partycji I klauzule 7 do 11 [ECMA-335 standardowe: wspólną infrastrukturę języka](https://www.ecma-international.org/publications/standards/Ecma-335.htm). 

Jeśli składnik spełnia specyfikacja języka wspólnego, może być zgodne ze specyfikacją CLS i są dostępne z kodu w zestawach napisane w języku programowania, który obsługuje ze specyfikacją CLS. Można określić, czy składnik jest zgodny ze specyfikacja języka wspólnego w czasie kompilacji, stosując [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutu do kodu źródłowego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute).

W tym artykule:

* [Zasady zgodności ze specyfikacją CLS](#cls-compliance-rules)

    * [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures)

    * [Konwencje nazewnictwa](#naming-conventions)
    
    * [Konwersja typów](#type-conversion)
    
    * [Tablice](#arrays)
    
    * [Interfejsy](#interfaces)
    
    * [Wyliczenia](#enumerations)
    
    * [Ogólnie rzecz biorąc wpisz elementy członkowskie](#type-members-in-general)
    
    * [Dostępność elementu członkowskiego](#member-accessibility)
    
    * [Typy ogólne i elementów członkowskich](#generic-types-and-members)
    
    * [Konstruktory](#constructors)
    
    * [Właściwości](#properties)
    
    * [Zdarzenia](#events)
    
    * [Overloads](#overloads)
    
    * [Wyjątki](#exceptions)
    
    * [Atrybuty](#attributes)
    
* [Atrybut CLSCompliant](#the-clscompliantattribute-attribute)

* [Współdziałanie między językami](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>Zasady zgodności ze specyfikacją CLS

W tej sekcji omówiono reguł do tworzenia składnika zgodne ze specyfikacją CLS. Pełną listę zasad, zobacz partycji I 11 klauzuli [ECMA-335 standardowe: wspólną infrastrukturę języka](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Specyfikacja języka wspólnego omówiono każdej reguły zgodności ze specyfikacją CLS, zastosowanie w przypadku użytkowników (deweloperów, którzy są uzyskiwania dostępu do składnika, który jest zgodny ze specyfikacją CLS), platformy (deweloperów, którzy korzystają z kompilatora języka Aby utworzyć CLS-compliant biblioteki) i rozszerzeń (deweloperów, którzy tworzą narzędzia, takiego jak kompilatora języka lub analizator kodu tworzącego składniki zgodne ze specyfikacją CLS). Ten artykuł dotyczy reguł odnoszących się do struktur. Należy pamiętać, że niektóre reguły, które dotyczą Extender mogą również dotyczyć zestawy, które są tworzone przy użyciu [Reflection.Emit](xref:System.Reflection.Emit). 

Projektowanie składnik, który jest niezależny od języka, wystarczy dotyczą zasady zgodności ze specyfikacją CLS interfejs publiczny danego składnika. Prywatnej implementacji nie ma być zgodny ze specyfikacją. 

> [!IMPORTANT]
> Zasady zgodności ze specyfikacją CLS dotyczą tylko interfejs publiczny składnika, nie można jej prywatna implementacja. 

Na przykład innych niż podpisane liczby całkowite [bajtów](xref:System.Byte) nie są zgodne ze specyfikacją CLS. Ponieważ `Person` udostępnia klasy w poniższym przykładzie `Age` właściwości typu [UInt16](xref:System.UInt16), poniższy kod wyświetla ostrzeżenie kompilatora.

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

Możesz wprowadzić klasy osoby zgodne ze specyfikacją CLS, zmieniając typ `Age` właściwość z `UInt16` do [Int16](xref:System.Int16), który jest zgodny ze specyfikacją CLS, 16-bitową liczbę całkowitą ze znakiem. Nie trzeba zmienić typ prywatna `personAge` pola. 

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

Interfejs publiczny biblioteki składa się z następujących czynności:

* Definicje klas publicznych.

* Definicje publiczne elementy członkowskie publicznych klas i definicje członków dostępne dla klas pochodnych (elementy chronione). 

* Parametry i zwracane typy metod publicznych klas publicznych i parametrów i zwracanych typów metod dostępne dla klas pochodnych. 

W poniższej tabeli wymieniono zasady zgodności ze specyfikacją CLS. Tekst reguły jest zajęta dosłownego wyrażenia z [ECMA-335 standardowe: wspólną infrastrukturę języka](https://www.ecma-international.org/publications/standards/Ecma-335.htm), czyli Copyright 2012 międzynarodowej Ecma. W poniższych sekcjach znajduje się bardziej szczegółowe informacje o tych reguł. 

Kategoria | Zobacz | Reguła | Numer reguły
-------- | --- | ---- | -----------
Ułatwienia dostępu | [Dostępność elementu członkowskiego](#member-accessibility) | Ułatwienia dostępu nie zmienia się w przypadku zastępowanie dziedziczonych metod, z wyjątkiem podczas przesłaniania metody dziedziczone z innego zestawu z ułatwieniami dostępu `family-or-assembly`. W takim przypadku zastąpienie ma ułatwień dostępu `family`. | 10
Ułatwienia dostępu | [Dostępność elementu członkowskiego](#member-accessibility) | Widoczność i dostępności typów i członków się typy w podpisie dowolnego elementu członkowskiego jest widoczny i jest dostępny zawsze, gdy ten element członkowski jest widoczny i jest dostępny. Na przykład metodę publiczną, która jest widoczny spoza jej zestawu nie ma argument o typie jest widoczna tylko w zestawie. Widoczność i dostępności typów tworzenia wystąpień typu ogólnego używane w podpisie dowolnego elementu członkowskiego jest widoczny i jest dostępny zawsze, gdy ten element członkowski jest widoczny i jest dostępny. Na przykład wystąpień typu ogólnego w podpisie elementu członkowskiego, który jest widoczny spoza jej zestawu nie posiada argumentów ogólnych, którego typ jest widoczna tylko w zestawie. | 12
Tablice | [Tablice](#arrays) | Tablice mają elementy o typie zgodnym ze specyfikacją CLS, oraz wszystkie wymiary tablicy posiada dolne granice tablicy o wartości zero. Fakt, że element jest tablicą i typ elementu tablicy wymaga aby odróżnić przeciążenia. Gdy przeładowanie opiera się na dwóch lub więcej tablicy typów typów elementów są nazw typów. | 16
Atrybuty | [Atrybuty](#attributes) | Atrybuty powinny być typu [System.Attribute](xref:System.Attribute), lub dziedziczenie z tego typu. | 41
Atrybuty | [Atrybuty](#attributes) | Ze specyfikacją CLS umożliwia tylko podzbiór kodowania atrybutów niestandardowych. Są tylko typy, które pojawia się w tych kodowania (patrz partycji IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [ System.Single](xref:System.Single), [System.Double](xref:System.Double), i dowolnego typu wyliczenie oparte na zgodne ze specyfikacją CLS typu podstawowego liczby całkowitej. | 34
Atrybuty | [Atrybuty](#attributes) | Ze specyfikacją CLS nie zezwala na Modyfikatory wymagane widocznego publicznie (`modreq`, zobacz II partycji), ale zezwala na Modyfikatory opcjonalne (`modopt`, zobacz II partycji) nie rozpoznaje. | 35
Konstruktorów | [Konstruktory](#constructors) | Konstruktor obiektu są wywołać niektórych konstruktora wystąpienia klasy podstawowej przed wystąpieniem dostęp do danych odziedziczone wystąpienie. (To nie dotyczą typów wartości, które nie muszą mieć konstruktorów.)  | 21
Konstruktorów | [Konstruktory](#constructors) | Nie jest wymagany Konstruktor obiektów z wyjątkiem w ramach tworzenia obiektu, a jest nie można zainicjować obiektu dwa razy. | 22
Wyliczenia | [Wyliczenia](#enumerations) | Podstawowy typ wyliczeniowy powinien być typem wbudowanym liczby całkowitej ze specyfikacją CLS, nazwy pola są "value__" i to pole jest oznaczone jako `RTSpecialName`. |  7
Wyliczenia | [Wyliczenia](#enumerations) | Istnieją dwa różne rodzaje wyliczenia wskazywanym przez obecności lub braku [System.FlagsAttribute](xref:System.FlagsAttribute) atrybutu niestandardowego (zobacz Biblioteka IV partycji). Reprezentuje jedną o nazwie liczby całkowite; inne reprezentuje nazwę flagi bitów, które można łączyć do generowania wartości bez nazwy. Wartość `enum` nie jest ograniczony do określonej wartości. |  8
Wyliczenia | [Wyliczenia](#enumerations) | Literał pola statyczne typu wyliczeniowego ma typ wyliczenia samej siebie. |  9
Zdarzenia | [Zdarzenia](#events) | Metody, które implementują zdarzenia są oznaczane `SpecialName` w metadanych. |29
Zdarzenia | [Zdarzenia](#events) | Dostępność zdarzenia i jego metody dostępu muszą być identyczne. |30
Zdarzenia | [Zdarzenia](#events) | `add` i `remove` metody dla zdarzenia są oba albo być obecny lub nieobecny. |31
Zdarzenia | [Zdarzenia](#events) | `add` i `remove` metody zdarzenia przyjmują jeden parametr o typie definiuje typ zdarzenia i która pochodzi z [System.Delegate](xref:System.Delegate). |32
Zdarzenia | [Zdarzenia](#events) | Zdarzenia będzie stosować się do określonego wzorca nazewnictwa. Atrybut jako SpecialName określone w regule ze specyfikacją CLS 29 nie są uwzględniane w porównania odpowiednią nazwę i są oparte na identyfikator reguły.  |33
Wyjątki | [Wyjątki](#exceptions) | Obiekty, które są generowane jest typu [System.Exception](xref:System.Exception) lub dziedziczenie z tego typu. Niemniej jednak metody zgodne ze specyfikacją CLS nie są wymagane do blokowania propagacji innych typów wyjątków. | 40
Ogólne | [Zasady zgodności ze specyfikacją CLS](#cls-compliance-rules) | Reguły ze specyfikacją CLS mają zastosowanie tylko do tych elementów typu, które są dostępne lub widoczne outsideof zestawu definiującego. | 1
Ogólne | [Zasady zgodności ze specyfikacją CLS](#cls-compliance-rules) | Elementy członkowskie typów zgodnych ze specyfikacją CLS nie jest oznaczony zgodne ze specyfikacją CLS. | 2
Typy ogólne | [Typy ogólne i elementów członkowskich](#generic-types-and-members) | Typy zagnieżdżone mają co najmniej tyle parametry ogólne, jak typ otaczający. Parametry ogólne w typu zagnieżdżonego odpowiada za pomocą pozycji do parametrów ogólnych w jego typie otaczającym.  | 42
Typy ogólne | [Typy ogólne i elementów członkowskich](#generic-types-and-members) | Nazwa typu ogólnego jest zakodowania liczba parametrów typu dla typu niezagnieżdżonego lub nowo wprowadzonych do typu, jeśli zagnieżdżony, zgodnie z regułami zdefiniowanych powyżej. | 43
Typy ogólne | [Typy ogólne i elementów członkowskich](#generic-types-and-members) | Typ ogólny jest ponownie zadeklarować ograniczenia wystarczające, aby zagwarantować, że wszystkie ograniczenia dotyczące typu podstawowego lub interfejsy będzie spełniony przez ograniczeń typu ogólnego. | 44
Typy ogólne | [Typy ogólne i elementów członkowskich](#generic-types-and-members) | Typy używane jako ograniczenia dotyczące parametrów ogólnych są się zgodne ze specyfikacją CLS. | 45
Typy ogólne | [Typy ogólne i elementów członkowskich](#generic-types-and-members) | Widoczność i dostępności elementów członkowskich (w tym typy zagnieżdżone) w ogólnym typem skonkretyzowanym uznaje się ograniczyć zakres konkretnego wystąpienia zamiast deklaracji typu ogólnego jako całość. Zakładając, że to, widoczność i dostępności reguły ze specyfikacją CLS 12 nadal zastosowanie zasady. | 46
Typy ogólne | [Typy ogólne i elementów członkowskich](#generic-types-and-members) | Dla każdej metodzie abstrakcyjnej ani wirtualnej ogólny jest domyślną konkretną implementację (nieabstrakcyjnej) | 47
Interfejsy | [Interfejsy](#interfaces) | Interfejsy zgodne ze specyfikacją CLS nie wymagają definicji compliantmethods niezgodny ze specyfikacją CLS w celu ich wdrożenia. | 18
Interfejsy | [Interfejsy](#interfaces) | Interfejsy zgodne ze specyfikacją CLS nie określają metody statyczne nie są one Definiowanie pól. | 19
Elementy członkowskie | [Ogólnie rzecz biorąc wpisz elementy członkowskie](#type-members-in-general) | Globalne pola statyczne i metod nie są zgodne ze specyfikacją CLS. | 36
Elementy członkowskie | -- | Przy użyciu metadanych inicjowania pola określona jest wartość literału statycznego. Literał zgodne ze specyfikacją CLS muszą mieć określoną wartość w polu inicjowania metadanych, które jest taki sam typ, jak literał (lub podstawowego typu, jeśli ten literał `enum`). | 13
Elementy członkowskie | [Ogólnie rzecz biorąc wpisz elementy członkowskie](#type-members-in-general) | Ograniczenie vararg nie jest częścią ze specyfikacją CLS, a tylko Konwencja wywoływania obsługiwane przez ze specyfikacją CLS jest standardowego zarządzanych konwencję wywołania. | 15
Konwencje nazewnictwa | [Konwencje nazewnictwa](#naming-conventions) | Zestawy postępuje zgodnie z załącznikiem 7 z techniczne raportu 15 Unicode Standard3.0 regulujące zestaw znaków mogą uruchomić i zawarte w identyfikatorach dostępnych online w [formuły normalizacji Unicode](http://www.unicode.org/unicode/reports/tr15/tr15-18.html). Identyfikatory jest w formacie canonical zdefiniowane przez Unicode normalizacji formularza C. Do celów ze specyfikacją CLS, identifiersare dwa takie same, jeśli ich mapowania małe litery (zgodnie z instrukcjami w Unicode niezależne od ustawień regionalnych, jeden do jednego małe mapowania) są takie same. Oznacza to, że dla dwóch identyfikatorów wziąć pod uwagę różne zgodnie ze specyfikacją CLS są różnią się tylko w ich przypadku. Jednak aby można było zastąpić dziedziczone definicji interfejsu wiersza polecenia wymaga dokładne kodowanie oryginalnej deklaracji. | 4
Przeciążenie | [Konwencje nazewnictwa](#naming-conventions) | Nazwy wszystkich wprowadzonych w zakresie zgodne ze specyfikacją CLS są różne niezależnie od rodzaju, z wyjątkiem przypadków, w których nazwy są identyczne i rozwiązane za pomocą przeciążenia. Oznacza to, że chociaż CTS pozwala na jednym typie, do korzystania z tej samej nazwy dla metody i pole, ze specyfikacją CLS nie. | 5
Przeciążenie | [Konwencje nazewnictwa](#naming-conventions) | Pola i typy zagnieżdżone powinna różnić się przez porównanie identyfikator samodzielnie, eventhough CTS pozwala odrębnych podpisów rozróżnienie. Metody, właściwości i zdarzenia, które mają taką samą nazwę (przez porównanie identyfikator) może różnić się nie tylko typem zwracanym, z wyjątkiem określonych w 39 reguły ze specyfikacją CLS | 6
Przeciążenie | [Overloads](#overloads) | Tylko właściwości i metody może być przeciążony. | 37
Przeciążenie | [Overloads](#overloads) |Właściwości i metody mogą być przeciążone tylko na podstawie liczby i typów ich parametrów, z wyjątkiem operatory konwersji o nazwie `op_Implicit` i `op_Explicit`, które również można przeciążać na podstawie ich zwracanego typu. | 38
Przeciążenie | -- | Co najmniej dwie metody zgodne ze specyfikacją CLS zadeklarowana w typie ma tego samego nameand, dla określonej grupy wystąpień typu mają ten sam parametr i typy zwracane, a następnie tych metod jest semantycznie równoważne w tych wystąpień typu. | 48
Właściwości | [Właściwości](#properties) | Metody, które implementują metody pobierającej i ustawiającej właściwość jest oznaczona jako `SpecialName` w metadanych. | 24
Właściwości | [Właściwości](#properties) | Metody dostępu właściwości zostaje być wszystkie statyczne, wszystkie wirtualne lub wszystkie można instancji. | 26
Właściwości | [Właściwości](#properties) | Typ właściwości jest zwracany typ metody pobierającej i typ ostatni argument metody ustawiającej. Typy parametrów właściwości są typy parametrów metody pobierającej i wszystkie typy, ale ostatni parametr metody ustawiającej. Wszystkie te typy są zgodne ze specyfikacją CLS, a nie są zarządzane wskaźników (to znaczy nie mogą być przekazywane przez odwołanie). | 27
Właściwości | [Właściwości](#properties) | Właściwości będzie stosować się do określonego wzorca nazewnictwa. `SpecialName` Atrybut określone w regule ze specyfikacją CLS 24 nie będą uwzględniane w porównania odpowiednią nazwę i będzie stosować się do identyfikatora reguły. Właściwość ma metodę metody pobierającej i/lub metody ustawiającej. | 28
Konwersja typów | [Konwersja typów](#type-conversion) | Jeśli podano op_Implicit lub op_Explicit dostarcza alternatywne metody udostępniania wymuszenia. | 39
Types | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Spakowane typy wartości nie są zgodne ze specyfikacją CLS. | 3
Types | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Wszystkie typy w podpis jest zgodne ze specyfikacją CLS. Wszystkie typy tworzenia wystąpień typu ogólnego jest zgodne ze specyfikacją CLS. | 11
Types | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Odwołania do typu nie są zgodne ze specyfikacją CLS. | 14
Types | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Typy wskaźników niezarządzanych nie są zgodne ze specyfikacją CLS. | 17
Types | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | Klasy zgodne ze specyfikacją CLS, typy wartości i interfejsy nie wymagają wykonania elementy członkowskie z systemem innym niż zgodne-ze specyfikacją CLS | 20
Types | [Typy i podpisy elementów członkowskich typu](#types-and-type-member-signatures) | [System.Object](xref:System.Object) jest zgodne ze specyfikacją CLS. Inne klasy zgodne ze specyfikacją CLS są dziedziczy z klasy, zgodne ze specyfikacją CLS. | 23

### <a name="types-and-type-member-signatures"></a>Typy i podpisy elementów członkowskich typu

[System.Object](xref:System.Object) typ jest zgodny ze specyfikacją CLS i jest podstawowym typem wszystkie typy obiektów w systemie typów .NET Framework. Dziedziczenia w programie .NET Framework jest albo niejawne (na przykład [ciąg](xref:System.String) klasy niejawnie dziedziczy `Object` klasy) bezpośredniego lub pośredniego (na przykład [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) Klasa jawnie dziedziczy [ArgumentException](xref:System.ArgumentException) klasy, która dziedziczy po jawnie [wyjątek](xref:System.Exception) klasy. Typ pochodny być zgodne ze specyfikacją CLS jego typ podstawowy również musi być zgodne ze specyfikacją CLS. 

W poniższym przykładzie przedstawiono typem pochodnym, którego typ podstawowy nie jest zgodne ze specyfikacją CLS. Definiuje podstawowej `Counter` klasy, która używa jako licznik całkowitą bez znaku 32-bitowych. Ponieważ ta klasa dostarcza funkcje licznika zawijania całkowitą bez znaku, klasa jest oznaczona jako niezgodne-ze specyfikacją CLS. W rezultacie Klasa pochodna `NonZeroCounter`, również jest niezgodny ze specyfikacją CLS. 

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

Wszystkie typy, które pojawiają się w podpisach elementu członkowskiego, w tym zwracany typ metody lub typ właściwości musi być zgodne ze specyfikacją CLS. Ponadto dla typów ogólnych: 

* Wszystkie typy, które tworzą ogólnego typu musi być zgodne ze specyfikacją CLS.

* Wszystkie typy używane jako ograniczenia dotyczące parametrów ogólnych musi być zgodne ze specyfikacją CLS. 

.NET [wspólny system typów](common-type-system.md) zawiera kilka wbudowanych typów, które są obsługiwane bezpośrednio przez środowisko uruchomieniowe języka wspólnego i specjalnie są zakodowane w metadanych zestawu. Te typy wewnętrzne typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS. 


Typie zgodnym ze specyfikacją CLS | Opis
------------------ | -----------
[Byte](xref:System.Byte) | 8-bitową liczbę całkowitą bez znaku 
[Int16](xref:System.Int16) | 16-bitową liczbę całkowitą ze znakiem 
[Int32](xref:System.Int32) | 32-bitowej liczby całkowitej ze znakiem 
[Int64](xref:System.Int64) | 64-bitowej liczby całkowitej ze znakiem
[Pojedynczy](xref:System.Single) | Wartość zmiennoprzecinkową o pojedynczej dokładności
[Double](xref:System.Double) | Wartość zmiennoprzecinkową podwójnej precyzji
[Boolean](xref:System.Boolean) | Typ wartości PRAWDA lub FAŁSZ 
[char](xref:System.Char) | Jednostka zakodowanego kodu UTF-16
[Decimal](xref:System.Decimal) | Liczba dziesiętna non--zmiennoprzecinkowych
[IntPtr](xref:System.IntPtr) | Wskaźnika lub dojścia o rozmiarze określone platformy
[Ciąg](xref:System.String) | Kolekcja zero, co najmniej jeden obiekt Char 
 
Typy wewnętrzne wymienione w poniższej tabeli nie są zgodne ze specyfikacją CLS.


Niezgodny typ | Opis | Alternatywnym, zgodnym ze specyfikacją CLS
------------------ | ----------- | -------------------------
[SByte](xref:System.SByte) | Typ danych 8-bitową liczbę całkowitą ze znakiem | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16-bitową liczbę całkowitą bez znaku | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32-bitowa liczba całkowita bez znaku | [Int64](xref:System.Int64)
[UInt64 —](xref:System.UInt64) | 64-bitowej liczby całkowitej bez znaku | [Int64](xref:System.Int64) (może przepełnienie), [BigInteger](xref:System.Numerics.BigInteger), lub [podwójne](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | Niepodpisane wskaźnika lub dojścia | [IntPtr](xref:System.IntPtr)
 
 Biblioteka klas programu .NET Framework lub inne biblioteki klas może zawierać innych typów, które nie są zgodne z CLS; na przykład: 
 
 * Spakowanymi typami wartości. W poniższym przykładzie C# tworzy klasę, która ma właściwości publicznej typu `int`* o nazwie `Value`. Ponieważ `int`* jest opakowanym typem wartościowym, kompilator flagi go jako niezgodne-ze specyfikacją CLS.

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

* Odwołania typu, które są specjalne konstrukcje, które zawierają odwołania do obiektu i odwołania do typu.

Jeśli typ nie jest zgodne ze specyfikacją CLS, należy zastosować [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutem *isCompliant* parametru z wartością `false` do niego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute) sekcji.  

Poniższy przykład przedstawia problem zgodności ze specyfikacją CLS w podpisie metody i podczas tworzenia wystąpienia typu ogólnego. Definiuje `InvoiceItem` z właściwością typu [UInt32](xref:System.UInt32), właściwość typu [Nullable (z UInt32)](xref:System.Nullable%601)ani konstruktora z parametrami typu `UInt32` i `Nullable(Of UInt32)`. Otrzymasz cztery ostrzeżeń kompilatora podczas kompilowania w tym przykładzie.

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

Aby wyeliminować ostrzeżeń kompilatora, Zastąp ze specyfikacją CLS-niezgodnych typów w `InvoiceItem` interfejs publiczny z typów zgodnych:

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

Oprócz folderów dla określonych typów wymienionych niektóre kategorie typów nie są zgodne ze specyfikacją CLS. Obejmują one typy niezarządzanych wskaźników i typów wskaźnika funkcji. Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej w celu utworzenia tablicy liczb całkowitych. 

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

```vb
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

Klasy abstrakcyjne dla zgodne ze specyfikacją CLS (czyli oznaczenie klasy `abstract` w języku C#), wszystkie elementy członkowskie klasy również musi być zgodne ze specyfikacją CLS. 

### <a name="naming-conventions"></a>Konwencje nazewnictwa

Ponieważ niektóre języki programowania jest rozróżniana wielkość liter, identyfikatory (takich jak nazwy przestrzeni nazw, typy i składniki) musi się różnić tylko wielkością liter. Dwa identyfikatory są traktowane jako równoważne, jeśli ich małe mapowania są takie same. W poniższym przykładzie C# definiuje dwie klasy publicznej, `Person` i `person`. Ponieważ różnią się tylko wielkością liter, kompilator języka C# flagi je jako nie zgodne z CLS. 

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

Programowanie identyfikatorów języka, takich jak nazwy przestrzeni nazw, typów i członków, musi być zgodna z [Unicode Standard 3.0, techniczne 15 raportu, załącznik 7](https://www.unicode.org/reports/tr15/tr15-18.html). Oznacza to, że:

* Pierwszy znak identyfikatora mogą być dowolnej Unicode wielkie litery, małe litery, tytuł wielkość list, litera modyfikatora, innego litery lub list numer. Aby uzyskać informacje na kategorie znaków Unicode, zobacz [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) wyliczenia. 

* Kolejne znaki mogą pochodzić z jednej z kategorii jako pierwszy znak i mogą również obejmować znaczniki bez spacji, odstępy łączenie znaki, liczby dziesiętne, łączące znaki interpunkcyjne i kody formatowania. 

Przed porównywania identyfikatorów, należy odfiltrować kody formatowania i dokonać konwersji identyfikatory C formularza normalizacji Unicode, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu algorytmem UTF-16. Sekwencje znaków, które powodują powstanie tej samej jednostki kodu w języku C formularza normalizacji Unicode nie są zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano właściwość o nazwie `Å`, który składa się z znaku ANGSTROM znak (U + 212B) i drugi właściwość o nazwie `Å` składające się z znak LATIN litera A z PIERŚCIEŃ powyżej (U + 00 C 5). Kompilator języka C# flagi kodu źródłowego jako niezgodne-ze specyfikacją CLS.

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

Nazwy elementów członkowskich z określonego zakresu (na przykład przestrzeni nazw w zestawie, typy w przestrzeni nazw lub elementy członkowskie w określonym typie) musi być unikatowa, z wyjątkiem nazw, które są rozpoznawane za pomocą przeciążenia. To wymaganie jest bardziej rygorystyczne niż wspólny system typów, dzięki czemu wiele elementów członkowskich w zakresie mają identyczne nazwy tak długo, jak są one różne rodzaje elementów członkowskich (na przykład, jeden to metoda i jedna jest polem). W szczególności dla elementów członkowskich typu: 

* Pola i typy zagnieżdżone są rozróżnianych na podstawie samej nazwy. 

* Metody, właściwości i zdarzenia, które mają taką samą nazwę musi się różnić się bardziej niż tylko typem zwracanym. 

Poniższy przykład przedstawia wymaganie, że nazwy składników muszą być unikatowe w ich zakresie. Definiuje klasę o nazwie `Converter` który obejmuje cztery elementy członkowskie o nazwie `Conversion`. Są trzy metody, a jeden z nich jest właściwością. Metoda, która obejmuje `Int64` parametru jest unikatowo o nazwie, ale te dwie metody z `Int32` parametru są, ponieważ wartość zwrotna nie jest uznawany za część podpisu elementu członkowskiego. `Conversion` Właściwość również narusza to wymaganie, ponieważ właściwości nie mogą mieć taką samą nazwę jak przeciążonej metody. 

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

Poszczególne języki unikatowych słów kluczowych, więc języków przeznaczonych środowisko uruchomieniowe języka wspólnego należy również podać mechanizmu dla odwołania do identyfikatorów (na przykład wpisz nazwy), które pokrywają się z słów kluczowych. Na przykład `case` jest słowem kluczowym w języku C# i Visual Basic. Jednak w poniższym przykładzie w języku Visual Basic jest w stanie odróżnić klasę o nazwie `case` z `case` — słowo kluczowe przy użyciu otwierające i zamykające nawiasy klamrowe. W przeciwnym razie przykładzie tworzy komunikat o błędzie, "— słowo kluczowe nie jest prawidłowe jako identyfikator" i nie można skompilować. 

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

W poniższym przykładzie C# jest w stanie utworzyć wystąpienia `case` przy użyciu symbolu, aby usunąć niejednoznaczność identyfikator ze słowem kluczowym języka @. Bez tego kompilatora C# będzie wyświetlane dwa komunikaty o błędach, "Oczekiwano typu" i "nieprawidłowe wyrażenie termin"case"." 

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

### <a name="type-conversion"></a>Konwersja typów

Specyfikacja języka wspólnego definiuje dwa operatory konwersji:

* `op_Implicit`, używany dla rozszerzanie konwersji, które nie powodują utratę danych lub dokładności. Na przykład [dziesiętną](xref:System.Decimal) struktura zawiera przeciążone `op_Implicit` operator do konwersji wartości typów całkowitych i [Char](xref:System.Char) wartości do `Decimal` wartości. 

* `op_Explicit`, używany dla zawężanie konwersji, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub dokładności. Na przykład `Decimal` struktura zawiera przeciążone `op_Explicit` operatora, aby przekonwertować [podwójne](xref:System.Double) i [pojedynczego](xref:System.Single) wartości do `Decimal` i konwertowania `Decimal` wartości do wartości całkowite `Double`, `Single`, i `Char`. 

Jednak nie obsługuje wszystkich języków przeładowania operatora lub definicję operatorów niestandardowych. Jeśli wybierzesz do wdrożenia tych operatorów konwersji, musisz także podać innym sposobem wykonania konwersji. Firma Microsoft zaleca, aby podać `From`Xxx i `To`metody Xxx. 

W poniższym przykładzie zdefiniowano zgodne ze specyfikacją CLS Konwersje jawne i niejawne. Tworzy `UDouble` klasa, która reprezentuje numer podpisem podwójnej precyzji, zmiennoprzecinkowych. Zapewnia niejawną konwersję z `UDouble` do `Double` i jawne konwersje z `UDouble` do `Single`, `Double` do `UDouble`, i `Single` do `UDouble`. Definiuje również `ToDouble` metody zamiast operatora niejawnej konwersji i `ToSingle`, `FromDouble`, i `FromSingle` metod jako alternatywy dla operatory jawnej konwersji. 

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

Tablice zgodne ze specyfikacją CLS spełniać następujące reguły: 

* Wszystkie wymiary tablicy muszą mieć dolna granica zero. Poniższy przykład tworzy specyfikacją CLS tablicy z dolną granicą jednego. Należy zauważyć, że mimo występowania [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutu, kompilator nie wykrywa czy tablica zwrócona przez `Numbers.GetTenPrimes` metody nie jest zgodne ze specyfikacją CLS. 

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

* Wszystkie elementy tablicy muszą składać się z typów zgodnych ze specyfikacją CLS. W poniższym przykładzie zdefiniowano dwie metody zwracające tablice niezgodnym-ze specyfikacją CLS. Pierwszy zwraca tablicę [UInt32](xref:System.UInt32) wartości. Zwraca drugie [obiektu](xref:System.Object) tablicy, która obejmuje [Int32](xref:System.Int32) i `UInt32` wartości. Mimo że kompilator identyfikuje pierwszy tablicy jako niezgodne z powodu jego `UInt32` typu, nie rozpoznaje, że druga tablica zawiera elementy niezgodnym-ze specyfikacją CLS. 

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

* Rozpoznanie przeciążenia dla metod, które mają tablicy parametrów jest opiera się na fakt, że są one tablicami i na ich typ elementu. Z tego powodu definicji następujące przeciążone `GetSquares` metody jest zgodne ze specyfikacją CLS. 

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

Interfejsy zgodne ze specyfikacją CLS można określić właściwości, zdarzeń i metody wirtualne (metody z żadnej implementacji). Interfejsie zgodnym ze specyfikacją CLS nie może mieć jedną z następujących czynności: 

* Metody statycznej lub pola statyczne. Błędy kompilatora C# generatse kompilatora w przypadku definiowania statycznego elementu członkowskiego w interfejsie. 

* Pola. C# acompiler generuje błędy kompilatora w przypadku definiowania pola w interfejsie.

* Metody, które nie są zgodne ze specyfikacją CLS. Na przykład następujący definicji interfejsu zawiera metodę, `INumber.GetUnsigned`, która jest oznaczona jako specyfikacją CLS. W tym przykładzie generuje ostrzeżenie kompilatora. 

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

  Z powodu działania tej reguły typów zgodnych ze specyfikacją CLS nie są wymagane do zaimplementowania elementy członkowskie z systemem innym niż zgodne-ze specyfikacją CLS. Jeśli zgodne ze specyfikacją CLS framework ujawnia klasy, która implementuje interfejsie zgodnym ze specyfikacją CLS, on również zawierał konkretnych implementacje wszystkich członków z systemem innym niż — zgodne z CLS. 

Kompilatory języka zgodne ze specyfikacją CLS, należy także zezwolić klasę, aby zapewnić oddzielne implementacje elementów członkowskich, które mają taką samą nazwę i sygnaturę w wielu interfejsach. C# obsługuje jawne implementacje interfejsu zapewnienie różnych implementacji metody o identycznej nazwie. Poniższy przykład przedstawia tego scenariusza, definiując `Temperature` klasa implementująca `ICelsius` i `IFahrenheit` interfejsy jako jawne implementacje interfejsu. 

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

Wyliczenia zgodne ze specyfikacją CLS, należy wykonać następujące czynności: 

* Podstawowy typ wyliczenia musi być całkowitą wewnętrzne zgodne ze specyfikacją CLS ([bajtów](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), lub [Int64](xref:System.Int64)). Na przykład następujący kod próbuje zdefiniowanie wyliczenia o typie podstawowym [UInt32](xref:System.UInt32) i generuje ostrzeżenie kompilatora. 

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

* Typ wyliczenia musi mieć pojedynczego wystąpienia pola o nazwie `Value__` który jest oznaczony atrybutem `FieldAttributes.RTSpecialName` atrybutu. Dzięki temu można jawnie odwoływać wartość pola. 

* Wyliczenie zawiera literału pól statycznych, których typ zgodny z typem wyliczenia samej siebie. Na przykład w przypadku definiowania `State` wyliczenie z wartościami `State.On` i `State.Off`, `State.On` i `State.Off` to statycznego pola literału typu `State`. 

* Istnieją dwa rodzaje wyliczenia: 
    
    * Reprezentuje zestaw wykluczają się wzajemnie, wyliczenie o nazwie wartości będące liczbami całkowitymi. Ten typ wyliczenia jest określane przez braku [System.FlagsAttribute](xref:System.FlagsAttribute) atrybutu niestandardowego.
    
    * Wyliczenie reprezentuje zestaw flagi bitów, które można łączyć do generowania wartości bez nazwy. Ten typ wyliczenia jest określane przez obecności [System.FlagsAttribute](xref:System.FlagsAttribute) atrybutu niestandardowego.
    
 Aby uzyskać więcej informacji, zobacz dokumentację [wyliczenia](xref:System.Enum) struktury. 

* Wartość wyliczenia nie jest ograniczona do jego określonej wartości z zakresu. Innymi słowy zakres wartości podstawowej jest zakres wartości wyliczenia. Można użyć `Enum.IsDefined` metodę, aby ustalić, czy określona wartość elementu członkowskiego wyliczenia. 

### <a name="type-members-in-general"></a>Ogólnie rzecz biorąc wpisz elementy członkowskie

Specyfikacja języka wspólnego wymaga wszystkich pól i metod można uzyskać dostępu do jako członków konkretnej klasy. W związku z tym globalnych pola statyczne i metody (czyli pola statyczne lub metody, które są zdefiniowane oprócz typu) nie są zgodne ze specyfikacją CLS. Jeśli spróbujesz obejmują pole lub metoda globalna w kodzie źródłowym kompilatora C# generuje błąd kompilatora. 

Specyfikacja języka wspólnego obsługuje tylko standardowe zarządzanych konwencję wywołania. Nie obsługuje niezarządzane konwencji wywoływania i metody z listami zmiennych argumentów oznaczony atrybutem `varargs` — słowo kluczowe. Listy zmiennych argumentów, które są zgodne z standardowej konwencji wywoływania zarządzanych, można użyć [ParamArrayAttribute](xref:System.ParamArrayAttribute) lub atrybutu implementacji poszczególnych języków, takich jak `params` — słowo kluczowe języka C# i `ParamArray` słów kluczowych w języku Visual Basic. 

### <a name="member-accessibility"></a>Dostępność elementu członkowskiego

Zastępowanie dziedziczonego elementu członkowskiego nie można zmienić dostępności tego członka. Na przykład publiczną metodę w klasie podstawowej nie mogą zostać zastąpione przez prywatnej metody w klasie pochodnej. Istnieje jeden wyjątek: `protected internal` (w języku C#) lub `Protected Friend` (w języku Visual Basic) elementu członkowskiego w jednym zestawie, który jest zastępowany przez typ w innym zestawie.  W takim przypadku jest dostępność zastąpienie `Protected`. 

Poniższy przykład pokazuje błąd, który jest generowany, gdy [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybut ma ustawioną `true`, i `Person`, które jest klasą pochodną `Animal`, próbuje zmienić dostępność `Species` właściwości z publicznej, prywatnej. Przykład pomyślnie kompiluje zmiana jego dostępność publiczną. 

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

Typy w podpisie elementu członkowskiego musi być dostępny zawsze, gdy ten element członkowski jest dostępny. Na przykład oznacza to, że publicznego elementu członkowskiego nie może zawierać parametru, którego typ jest prywatny, chronionych lub wewnętrzny. Poniższy przykład przedstawia błąd kompilatora, która powoduje podczas `StringWrapper` konstruktora klasy uwidacznia wewnętrzny `StringOperationType` wartość wyliczenia, która określa, jak powinien być zawijany wartość ciągu. 

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

### <a name="generic-types-and-members"></a>Typy ogólne i elementów członkowskich

Zagnieżdżone typy zawsze mieć co najmniej tyle parametrów ogólnych jak ich typ otaczający. Te odpowiada za pomocą pozycji do parametrów ogólnych w typ otaczający. Typ ogólny mogą również obejmować nowe parametry ogólne. 

Relacja między typ zawierający parametry typu ogólnego i jego zagnieżdżone typy mogą być ukryte przez składnię poszczególnych języków. W poniższym przykładzie typu ogólnego `Outer<T>` zawiera dwie klasy zagnieżdżonej `Inner1A` i `Inner1B<U>`. Wywołania `ToString` metodę, która dziedziczy po każdej klasy `Object.ToString`, Pokaż, że każda klasa zagnieżdżona zawiera parametry typu zawierająca go klasa. 

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

Nazwy typu ogólnego są zakodowane w postaci *nazwa*"*n*, gdzie *nazwa* jest nazwą typu *`* jest literałem, znak i *n* jest liczba parametrów zadeklarowana w typie lub dla zagnieżdżone ogólnych typów, liczba parametrów typu nowo wprowadzonych. To kodowanie nazwy typu ogólnego jest głównie deweloperom, którzy zgodne ze specyfikacją CLS typy ogólne w bibliotece dostęp do za pomocą odbicia. 

Jeśli ograniczenia są stosowane do ogólnego typu żadnych typów, używany jako ograniczenia również musi być zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano klasę o nazwie `BaseClass` czyli nie zgodne ze specyfikacją CLS i rodzajowy klasę o nazwie `BaseCollection` których parametru typu muszą pochodzić od `BaseClass`. Jednak ponieważ `BaseClass` nie jest zgodny z CLS, kompilator emituje ostrzeżenie. 

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

Jeśli typem ogólnym pochodzi od typu podstawowego ogólny, go ponownie zadeklarować żadnych ograniczeń, dzięki czemu można zagwarantować, że spełnione są również ograniczenia dotyczące typu podstawowego. W poniższym przykładzie zdefiniowano `Number<T>` reprezentujące dowolnego typu liczbowego. Definiuje również `FloatingPoint<T>` klasa, która reprezentuje zmiennoprzecinkową wartości. Jednak kod źródłowy nie powiedzie się do kompilacji, ponieważ nie ma zastosowania ograniczenie na `Number<T>` (czy T musi być typem wartości) do `FloatingPoint<T>`.

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
// The attempt to comple the example displays the following output:
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
' The attempt to comple the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'    
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

Przykład kompiluje pomyślnie dodany do ograniczenia `FloatingPoint<T>` klasy.

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

Specyfikacja języka wspólnego nakłada model wystąpienia zachowawcze zagnieżdżone typy i chronione elementy członkowskie. Otwórz typy ogólne nie może ujawnić pól lub elementy członkowskie o podpisy zawierające konkretnego wystąpienia typu ogólnego zagnieżdżone, chronionych. Inne niż ogólne typy, które rozszerzają konkretnego wystąpienia metody rodzajowe klasy podstawowej lub interfejsu nie może ujawnić pól lub elementy członkowskie o podpisy zawierające inną podczas tworzenia wystąpienia typu ogólnego zagnieżdżone, chronionych.

W poniższym przykładzie zdefiniowano typu ogólnego, `C1<T>`i Klasa chroniona, `C1<T>.N`. `C1<T>` ma dwie metody `M1` i `M2`. Jednak `M1` nie jest zgodne ze specyfikacją CLS, ponieważ próbuje przywrócić `C1<int>.N` obiekt z `C1<T>`. W drugiej klasy `C2`, jest określana na podstawie `C1<long>`. Składa się z dwóch metod `M3` i `M4`. `M3` nie jest zgodne ze specyfikacją CLS, ponieważ próbuje przywrócić `C1<int>.N` obiektu z podklasą `C1<long>`. Należy pamiętać, że Kompilatory języka można jeszcze bardziej restrykcyjne. W tym przykładzie Visual Basic jest wyświetlany błąd przy próbie skompilować `M4`. 

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

Konstruktory zgodne ze specyfikacją CLS klas i struktur muszą wykonać następujące czynności: 

* Konstruktora klasy pochodnej musi wywołać konstruktora wystąpień klasy podstawowej, zanim uzyskuje dostęp do danych wystąpienia dziedziczone. To wymaganie dotyczy faktu, że konstruktorów klasy podstawowej nie są dziedziczone przez ich klas pochodnych. Ta zasada dotyczy struktur, które nie obsługują bezpośredniego dziedziczenia. 

  Zazwyczaj kompilatory wymuszania tej reguły, niezależnie od zgodności ze specyfikacją CLS, jak przedstawiono na poniższym przykładzie. Tworzy `Doctor` klasy, która jest pochodną `Person` klasy, ale `Doctor` klasa nie może wywołać `Person` konstruktora klasy w celu zainicjowania pól wystąpień dziedziczone. 

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
    
* Nie można wywołać konstruktora obiektów z wyjątkiem tworzenia obiektu. Ponadto nie można zainicjować obiektu dwa razy. Oznacza to, że na przykład `Object.MemberwiseClone` nie mogą wywoływać konstruktorów.  

### <a name="properties"></a>Właściwości

Właściwości typów zgodnych ze specyfikacją CLS, należy wykonać następujące czynności:

* Właściwość musi mieć metody ustawiającej i/lub metody pobierającej. W zestawie te są zaimplementowane jako specjalnych metod, co oznacza, że będą wyświetlane jako osobne metody (nosi nazwę metody pobierającej `get` \_ *propertyname* i metodę ustawiającą `set*\_*propertyname*) marked as `jako SpecialName "w metadane zestawu. Ta reguła automatycznie bez konieczności zastosowania wymusza kompilatora C# [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutu. 

* Typ właściwości jest zwracany typ metody pobierającej właściwości i ostatni argument metody ustawiającej. Te typy muszą być zgodne ze specyfikacją CLS, oraz argumentów nie można przypisać do właściwości przez odwołanie (oznacza to, nie może być wskaźniki zarządzanych). 

* Jeśli właściwość ma metodę pobierającą i metody ustawiającej, oba muszą być wirtualny, statycznym lub oba wystąpienia. Kompilator języka C# wymusza automatycznie tej reguły za pomocą składni definicji właściwości. 

### <a name="events"></a>Zdarzenia

Zdarzenie jest definiowane przez jego nazwa i jej typie. Typ zdarzenia jest delegata, który służy do wskazywania zdarzenia. Na przykład `DbConnection.StateChange` zdarzenie jest typu `StateChangeEventHandler`. Oprócz samym zdarzeniu trzy metody z nazw na podstawie nazwy zdarzenia implementacji zdarzeń i są oznaczone jako `SpecialName` w metadanych zestawu: 

* Dodawanie obsługi zdarzeń, o nazwie metodę `add`_*EventName*. Na przykład metoda subskrypcji zdarzeń dla `DbConnection.StateChange` nosi nazwę zdarzenia `add_StateChange`. 

* Metoda usuwania program obsługi zdarzeń o nazwie `remove`_*EventName*. Na przykład metoda usuwania dla `DbConnection.StateChange` nosi nazwę zdarzenia `remove_StateChange`.

* Metoda wskazującą, w której wystąpiło zdarzenie, o nazwie `raise`_*EventName*. 

> [!NOTE]
> Większość specyfikacja języka wspólnego zasady dotyczące zdarzenia są implementowane przez Kompilatory języka i są niewidoczne dla deweloperów składnika. 

Metody dodawania, usuwania i wywoływanie zdarzeń musi mieć tą samą dostępnością. One również wszystkie muszą być statyczne, wystąpienie, lub wirtualnych. Metody do dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia. Dodawanie i usuwanie metody muszą być obecne jednocześnie lub nieobecne. 

W poniższym przykładzie zdefiniowano klasę zgodne ze specyfikacją CLS o nazwie `Temperature` który zgłasza `TemperatureChanged` zdarzeń, jeśli zmiana temperatury między dwa odczyty jest równa lub przekracza wartość progową. `Temperature` Klasa jawnie definiuje `raise_TemperatureChanged` metodę, tak aby selektywnie można wykonać procedury obsługi zdarzeń.

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

Specyfikacja języka wspólnego nakłada się na przeciążone elementy członkowskie następujące wymagania: 

* Elementy członkowskie można przeciążać, na podstawie liczby parametrów i typ żadnego parametru. Wywoływanie Konwencji, zwracany typ niestandardowy Modyfikatory stosowane do metody lub jej parametr i określa, czy parametry są przekazywane przez wartości lub według odwołania nie są uznawane za podczas rozróżnianie między przeciążenia. Na przykład, zobacz kod z wymaganiem, aby nazwy musi być unikatowa w zakresie w [konwencje nazewnictwa](#naming-conventions) sekcji. 

* Tylko właściwości i metody może być przeciążony. Pola i zdarzenia nie może być przeciążony. 

* Metody ogólne można przeciążać, na podstawie liczby ich parametry ogólne. 

> [!NOTE]
>`op_Explicit` i `op_Implicit` operatory są wyjątki od reguły, które zwracają wartość nie jest uznawany za część sygnatury metody Rozpoznanie przeciążenia. Te dwa operatory można przeciążać, na podstawie zarówno ich parametrów i ich wartości zwracanej. 

### <a name="exceptions"></a>Wyjątki

Obiekty wyjątków muszą pochodzić od [System.Exception](xref:System.Exception) lub inny typ pochodny typu `System.Exception`. Poniższy przykład przedstawia błąd kompilatora, która powoduje podczas niestandardowej klasy o nazwie `ErrorClass` służy do obsługi wyjątków.

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

Aby rozwiązać ten problem, `ErrorClass` musi dziedziczyć po klasie `System.Exception`. Ponadto właściwości wiadomości musi zostać zastąpiona. Poniższy przykład poprawia te błędy, aby zdefiniować `ErrorClass` klasy, która jest zgodna ze specyfikacją CLS.  

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

Zestawy struktury In.NET, atrybuty niestandardowe udostępnić extensible mechanizm do przechowywania niestandardowych atrybutów i pobierania metadanych dotyczących programowania obiekty, takie jak zestawy, typy elementów członkowskich i parametrów metody. Atrybuty niestandardowe musi pochodzić od [System.Attribute](xref:System.Attribute) lub typ pochodny typu `System.Attribute`.

Poniższy przykład narusza tę regułę. Definiuje `NumericAttribute` klasy, która nie pochodzi od `System.Attribute`. Należy pamiętać, że wystąpi błąd kompilatora wyniki, tylko gdy specyfikacją CLS atrybut jest stosowany, nie, jeśli klasa jest zdefiniowana. 

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

Konstruktor lub właściwości atrybutu zgodne ze specyfikacją CLS mogą uwidaczniać tylko następujących typów:

* [Boolean](xref:System.Boolean)

* [Byte](xref:System.Byte)

* [char](xref:System.Char)

* [Double](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Pojedynczy](xref:System.Single)

* [Ciąg](xref:System.String)

* [Typ](xref:System.Type)

* Dowolnego typu wyliczenia o typie podstawowym `Byte`, `Int16`, `Int32`, lub `Int64`. 

W poniższym przykładzie zdefiniowano `DescriptionAttribute` klasą pochodzącą z [atrybutu](xref:System.Attribute). Konstruktor klasy ma parametr typu `Descriptor`, więc klasa nie jest zgodne ze specyfikacją CLS. Zauważ, że kompilator języka C# emituje ostrzeżenie, który kompiluje się pomyślnie. 

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

## <a name="the-clscompliantattribute-attribute"></a>Atrybut CLSCompliant

[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybut używany do określenia, czy program element spełnia specyfikacja języka wspólnego. `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` Konstruktor zawiera jeden wymagany parametr *isCompliant*, który wskazuje, czy program element jest zgodne ze specyfikacją CLS. 

W czasie kompilacji kompilatorowi wykrywa niezgodne elementy, które są uważane za zgodne ze specyfikacją CLS i emituje ostrzeżenie. Kompilator nie Emituj ostrzeżenia dla typów albo elementów członkowskich, które są jawnie uznane za niezgodne. 

Składnik deweloperzy mogą używać `CLSCompliantAttribute` atrybutu na dwa sposoby: 

* Aby zdefiniować części interfejs publiczny udostępnianych przez składnik, które są zgodne ze specyfikacją CLS i części, które nie są zgodne ze specyfikacją CLS. W przypadku atrybutu można oznaczyć jako zgodnego ze specyfikacją CLS elementy określonego programu użytkowania gwarantuje, że te elementy są dostępne ze wszystkich języków i narzędzi przeznaczonych dla platformy .NET Framework. 

* Aby upewnić się, że biblioteka składnik publiczny interfejs przedstawia tylko elementy programu, które są zgodne ze specyfikacją CLS. Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory będzie zazwyczaj ostrzeżenie.

> [!WARNING]
> W niektórych przypadkach Kompilatory języka wymuszania reguł zgodne ze specyfikacją CLS, niezależnie od tego, czy `CLSCompliantAttribute` atrybut jest używany. Na przykład definiowanie `*static` elementu członkowskiego w interfejsie narusza regułę ze specyfikacją CLS. Jednak w przypadku definiowania `*static` elementu członkowskiego w interfejsie, kompilator języka C# Wyświetla komunikat o błędzie i kończy się niepowodzeniem, aby skompilować aplikację.

`CLSCompliantAttribute` Atrybut jest oznaczony atrybutem [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) atrybut, który ma wartość `AttributeTargets.All`. Ta wartość umożliwia stosowanie `CLSCompliantAttribute` atrybut do dowolnych programów, zestawy, moduły, w tym typów (klasy, struktury, wyliczenia, interfejsów i delegatów), typy elementów członkowskich (konstruktorów, metod, właściwości, pól i zdarzenia), Parametry, parametry ogólne i wartości zwracanych. Jednak w praktyce, powinien zastosować atrybut tylko do zestawów, typy i elementy członkowskie typu. W przeciwnym razie kompilatory Ignoruj ten atrybut i nadal generować ostrzeżenia kompilatora zawsze, gdy wystąpi parametrem niezgodnych parametru ogólnego lub zwróć wartość interfejs publiczny biblioteki.  

Wartość `CLSCompliantAttribute` atrybutu jest dziedziczona przez program zawartych w niej elementów. Na przykład jeśli zestaw jest oznaczony jako zgodnego ze specyfikacją CLS, jego typów także są zgodne ze specyfikacją CLS. Typ jest oznaczony jako zgodnego ze specyfikacją CLS, jego zagnieżdżone typy i elementy członkowskie nie są zgodne ze specyfikacją CLS. 

Można jawnie przesłonić odziedziczonego zgodności, stosując `CLSCompliantAttribute` atrybutu element zawartych w niej program. Na przykład można użyć `CLSCompliantAttribute` atrybutem *isCompliant* wartość `false` można użyć do definiowania niezgodnych typów w zestawie zgodne, a atrybut o *isComplian*wartość `true` do definiowania zgodny typ w zestawie niezgodnych. Można również zdefiniować niezgodnych elementów członkowskich w typie zgodnym. Jednak niezgodnych typów nie może mieć elementy członkowskie zgodne, więc nie można użyć atrybutu o *isCompliant* wartość `true` do przesłonięcia dziedziczenia z typem niezgodnych. 

Gdy tworzysz składników, zawsze należy używać `CLSCompliantAttribute` atrybutu, aby wskazać, czy używanemu zestawowi, jego typów i jej elementów członkowskich są zgodne ze specyfikacją CLS. 

Aby utworzyć zgodny z CLS składniki: 

1. Użyj `CLSCompliantAttribute` aby oznaczyć możesz zestawu jako zgodnego ze specyfikacją CLS.

2. Oznacz publicznie ujawnionych typów w zestawie, które nie są zgodne z CLS jako niezgodne. 

3. Oznacz żadnych publicznie ujawnionych elementów członkowskich w typach zgodne ze specyfikacją CLS jako niezgodne. 

4. Podaj alternatywnym, zgodnym ze specyfikacją CLS elementy członkowskie z systemem innym niż zgodne-ze specyfikacją CLS. 

Jeśli pomyślnie zostały oznaczone jako niezgodne typy i elementy członkowskie, kompilujący powinien nie Emituj wszelkie ostrzeżenia o braku zgodności. Jednak należy wskazać elementów członkowskich, które nie są zgodne ze specyfikacją CLS i wyświetlać ich zgodne ze specyfikacją CLS alternatyw w dokumentacji produktu. 

W poniższym przykładzie użyto `CLSCompliantAttribute` atrybut do definiowania zgodne ze specyfikacją CLS zestawu i typu `CharacterUtilities`, która ma dwa elementy członkowskie z systemem innym niż — zgodne z CLS. Ponieważ oba elementy są oznaczane `CLSCompliant(false)` atrybutu, kompilator generuje żadnych ostrzeżeń. Ta klasa dostarcza również alternatywnym, zgodnym ze specyfikacją CLS dla obu metod. Zwykle po prostu dodamy dwa przeciążenia do `ToUTF16` metodę w celu zapewnienia alternatywnych zgodne ze specyfikacją CLS. Jednak ponieważ metody nie może zostać przeciążony oparte na wartości zwracanej, nazwy metody zgodne ze specyfikacją CLS różnią się od nazwy metod niezgodnych.  

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

Jeśli opracowujesz aplikację, a nie w bibliotece (Jeśli nie są udostępnianie typów albo elementów członkowskich, które mogą być używane przez innych aplikacji), zgodności ze specyfikacją CLS elementów programu, które korzysta z aplikacji mogą być przydatne tylko wtedy, gdy język nie obsługuje ich . W takim przypadku kompilujący języka zostanie wygenerowany błąd podczas próby użycia elementu niezgodnym-ze specyfikacją CLS. 

## <a name="cross-language-interoperability"></a>Współdziałanie między językami

Niezależność od języka ma liczbę możliwych znaczenie. Znaczenie co obejmuje bezproblemowo używające typów napisane w języku jednej z aplikacji w języku innym. Drugi znaczenie, które ma fokus w tym artykule, polega na połączeniu kod napisany w wielu językach w ramach jednego zestawu .NET Framework. 

Poniższy przykład przedstawia współdziałanie między językami przez tworzenia biblioteki klas o nazwie Utilities.dll, który zawiera dwie klasy `NumericLib` i `StringLib`. `NumericLib` Klasy jest napisany w języku C# i `StringLib` klasy jest napisany w języku Visual Basic. Oto kod źródłowy `StringUtil.vb`, zawierające jeden element członkowski `ToTitleCase`w jego `StringLib` klasy.

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

Oto kod źródłowy NumberUtil.cs, który definiuje `NumericLib` klasy, która ma dwa elementy członkowskie, `IsEven` i `NearZero`.

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

Aby pakiet dwóch klas w jednym zestawie, należy skompilować je w modułach. Aby skompilować pliku kodu źródłowego języka Visual Basic w module, użyj tego polecenia: 

```
vbc /t:module StringUtil.vb 
```

Aby skompilować pliku kodu źródłowego C# w module, użyj tego polecenia:

```
csc /t:module NumberUtil.cs
```

Następnie skompilować dwa moduły do zestawu jest używane narzędzie łącza (Link.exe): 

```
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Poniższy przykład wywołuje `NumericLib.NearZero` i `StringLib.ToTitleCase` metody. Należy zauważyć, że zarówno kod Visual Basic, jak i kodu C# możliwość dostępu metody w obu klasach.

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

```
vbc example.vb /r:UtilityLib.dll
```

Aby skompilować w języku C#, Zmień nazwę kompilatora z vbc do csc i zmień rozszerzenie pliku z .vb CS:

```
csc example.cs /r:UtilityLib.dll
```

