---
title: 'Dziedziczenie w C #'
description: Dowiedz się, jak używać dziedziczenia w bibliotekach i aplikacjach języka C#.
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: b72badb7833e018dfcbf5d2583b17f17c800c382
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156756"
---
# <a name="inheritance-in-c-and-net"></a>Dziedziczenie w języku C# i .NET

Ten samouczek wprowadza do dziedziczenia w języku C#. Dziedziczenie jest cechą języków programowania zorientowanych obiektowo, która umożliwia zdefiniowanie klasy podstawowej, która zapewnia określone funkcje (dane i zachowanie) oraz definiowanie klas pochodnych, które dziedziczą lub zastępują tę funkcję.

## <a name="prerequisites"></a>Wymagania wstępne

W tym samouczku przyjęto założenie, że zainstalowano zestaw SDK .NET Core. Odwiedź stronę [pobierania .NET Core,](https://dotnet.microsoft.com/download) aby ją pobrać. Potrzebny jest również edytor kodu. Ten samouczek używa [kodu programu Visual Studio](https://code.visualstudio.com), chociaż można użyć dowolnego edytora kodu do wyboru.

## <a name="running-the-examples"></a>Uruchamianie przykładów

Aby utworzyć i uruchomić przykłady w tym samouczku, należy użyć narzędzia [dotnet](../../core/tools/dotnet.md) z wiersza polecenia. Wykonaj następujące kroki dla każdego przykładu:

1. Utwórz katalog do przechowywania przykładu.
1. Wprowadź polecenie [dotnet new console](../../core/tools/dotnet-new.md) w wierszu polecenia, aby utworzyć nowy projekt .NET Core.
1. Skopiuj i wklej kod z przykładu do edytora kodu.
1. Wprowadź polecenie [przywracania dotnetzwy](../../core/tools/dotnet-restore.md) z wiersza polecenia, aby załadować lub przywrócić zależności projektu.

  [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Wprowadź polecenie [dotnet run,](../../core/tools/dotnet-run.md) aby skompilować i wykonać przykład.

## <a name="background-what-is-inheritance"></a>Tło: Co to jest dziedziczenie?

*Dziedziczenie* jest jednym z podstawowych atrybutów programowania obiektowego. Umożliwia zdefiniowanie klasy podrzędnej, która używa ponownie (dziedziczy), rozszerza lub modyfikuje zachowanie klasy nadrzędnej. Klasa, której elementy członkowskie są dziedziczone jest nazywany *klasy podstawowej*. Klasa, która dziedziczy członków klasy podstawowej jest nazywany *klasy pochodnej*.

C# i .NET obsługują tylko *pojedyncze dziedziczenie.* Oznacza to, że klasa może dziedziczyć tylko z jednej klasy. Dziedziczenie jest jednak przechodnie, co umożliwia zdefiniowanie hierarchii dziedziczenia dla zestawu typów. Innymi słowy, `D` typ może `C`dziedziczyć z `B`typu , który dziedziczy z typu , który dziedziczy z typu `A`klasy podstawowej . Ponieważ dziedziczenie jest przechodnie, `A` elementy członkowskie `D`typu są dostępne do typu .

Nie wszystkie elementy członkowskie klasy podstawowej są dziedziczone przez klasy pochodne. Następujące elementy członkowskie nie są dziedziczone:

- [Konstruktory statyczne](../programming-guide/classes-and-structs/static-constructors.md), które inicjują dane statyczne klasy.

- [Konstruktory wystąpienia](../programming-guide/classes-and-structs/constructors.md), które można wywołać, aby utworzyć nowe wystąpienie klasy. Każda klasa musi zdefiniować własne konstruktory.

- [Finalizatory](../programming-guide/classes-and-structs/destructors.md), które są wywoływane przez moduł zbierający elementy bezużyteczne w czasie wykonywania, aby zniszczyć wystąpienia klasy.

Podczas gdy wszystkie inne elementy członkowskie klasy podstawowej są dziedziczone przez klasy pochodne, czy są one widoczne, czy nie zależy od ich dostępności. Dostępność elementu członkowskiego wpływa na jego widoczność dla klas pochodnych w następujący sposób:

- [Elementy członkowskie prywatne](../language-reference/keywords/private.md) są widoczne tylko w klasach pochodnych, które są zagnieżdżone w ich klasie podstawowej. W przeciwnym razie nie są one widoczne w klasach pochodnych. W poniższym `A.B` przykładzie jest zagnieżdżona `C` klasa, `A`która pochodzi od `A`i pochodzi od . Pole `A.value` prywatne jest widoczne w polu A.B. Jeśli jednak usuniesz `C.GetValue` komentarze z metody i spróbujesz skompilować przykład, utworzy błąd kompilatora CS0122: "A.value" jest niedostępny ze względu na poziom ochrony."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chronione](../language-reference/keywords/protected.md) elementy członkowskie są widoczne tylko w klasach pochodnych.

- [Elementy członkowskie wewnętrzne](../language-reference/keywords/internal.md) są widoczne tylko w klasach pochodnych, które znajdują się w tym samym zestawie co klasa podstawowa. Nie są one widoczne w klasach pochodnych znajdujących się w innym zestawie niż klasa podstawowa.

- [Elementy akcyjne](../language-reference/keywords/public.md) są widoczne w klasach pochodnych i są częścią interfejsu publicznego klasy pochodnej. Publiczne dziedziczone elementy członkowskie można wywołać tak, jakby były zdefiniowane w klasie pochodnej. W poniższym przykładzie `A` klasa definiuje `Method1`metodę o `B` nazwie , `A`a klasa dziedziczy z klasy . Przykład następnie `Method1` wywołuje tak, jakby była `B`to metoda instancji na .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Klasy pochodne można również *zastąpić* dziedziczone elementy członkowskie, zapewniając implementację alternatywną. Aby można było zastąpić element członkowski, element członkowski w klasie podstawowej musi być oznaczony [wirtualnym](../language-reference/keywords/virtual.md) słowem kluczowym. Domyślnie elementy członkowskie klasy podstawowej nie są oznaczone jako `virtual` i nie można ich zastąpić. Próba zastąpienia elementu członkowskiego niewirtualnego, jak w poniższym przykładzie, generuje błąd kompilatora CS0506: "\<element członkowski> nie może zastąpić dziedziczonego członka elementu członkowskiego \<> ponieważ nie jest oznaczony jako wirtualny, abstrakcyjny lub zastępowany.

```csharp
public class A
{
    public void Method1()
    {
        // Do something.
    }
}

public class B : A
{
    public override void Method1() // Generates CS0506.
    {
        // Do something else.
    }
}
```

W niektórych przypadkach klasa pochodna *musi* zastąpić implementacji klasy podstawowej. Członkowie klasy podstawowej oznaczone [abstrakcyjne](../language-reference/keywords/abstract.md) słowo kluczowe wymagają, że klasy pochodne zastąpić je. Próba skompilowania w poniższym przykładzie generuje błąd kompilatora CS0534, "&lt;klasa&gt; nie implementuje dziedziczonego abstrakcyjnego elementu członkowskiego &lt;&gt;", ponieważ klasa `B` nie zapewnia implementacji dla `A.Method1`.

```csharp
public abstract class A
{
    public abstract void Method1();
}

public class B : A // Generates CS0534.
{
    public void Method3()
    {
        // Do something.
    }
}
```

Dziedziczenie ma zastosowanie tylko do klas i interfejsów. Inne kategorie typów (struktury, delegatów i wyliczenia) nie obsługują dziedziczenia. Ze względu na te reguły, próbując skompilować kod, jak w poniższym przykładzie tworzy błąd kompilatora CS0527: "Typ 'ValueType' na liście interfejsu nie jest interfejsem." Komunikat o błędzie wskazuje, że chociaż można zdefiniować interfejsy, które implementuje struktury, dziedziczenie nie jest obsługiwane.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Dziedziczenie niejawne

Oprócz wszelkich typów, które mogą dziedziczyć z za pośrednictwem pojedynczego dziedziczenia, wszystkie typy w systemie typu .NET niejawnie dziedziczą lub <xref:System.Object> typu pochodzącego z niego. Wspólna funkcjonalność <xref:System.Object> jest dostępna dla każdego typu.

Aby zobaczyć, co oznacza niejawne dziedziczenie, zdefiniujmy nową klasę, `SimpleClass`która jest po prostu pustą definicją klasy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Następnie można użyć odbicia (który pozwala sprawdzić metadane typu, aby uzyskać informacje o tym typie), `SimpleClass` aby uzyskać listę elementów członkowskich, które należą do typu. Mimo że nie zdefiniowano żadnych `SimpleClass` elementów członkowskich w klasie, dane wyjściowe z przykładu wskazuje, że faktycznie ma dziewięć elementów członkowskich. Jeden z tych elementów członkowskich jest konstruktorem bezparametrów (lub domyślnym), który jest automatycznie dostarczany dla `SimpleClass` typu przez kompilator C#. Pozostałe osiem są <xref:System.Object>członkami , typ, z którego wszystkie klasy i interfejsy w systemie typu .NET ostatecznie niejawnie dziedziczą.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Niejawne <xref:System.Object> dziedziczenie z klasy `SimpleClass` udostępnia te metody klasie:

- Metoda `ToString` publiczna, która konwertuje `SimpleClass` obiekt na jego reprezentację ciągu, zwraca w pełni kwalifikowaną nazwę typu. W takim przypadku `ToString` metoda zwraca ciąg "SimpleClass".

- Trzy metody, które testują na równość `Equals(Object)` dwóch obiektów: `Equals(Object, Object)` metoda wystąpienia publicznego, publiczna metoda statyczna i publiczna metoda statyczna. `ReferenceEquals(Object, Object)` Domyślnie te metody testują równość odniesienia; oznacza to, że aby być równym, dwie zmienne obiektowe muszą odwoływać się do tego samego obiektu.

- Metoda `GetHashCode` publiczna, która oblicza wartość, która umożliwia wystąpienie typu, który ma być używany w kolekcjach haszhed.

- Metoda `GetType` publiczna, która <xref:System.Type> zwraca obiekt, `SimpleClass` który reprezentuje typ.

- Metoda <xref:System.Object.Finalize%2A> chroniona, która jest przeznaczona do zwalniania zasobów niezarządzanych, zanim pamięć obiektu zostanie odzyskana przez moduł zbierający elementy bezużyteczne.

- Metoda <xref:System.Object.MemberwiseClone%2A> chroniona, która tworzy płytki klon bieżącego obiektu.

Ze względu na niejawne dziedziczenie, `SimpleClass` można wywołać dowolnego dziedziczonego elementu `SimpleClass` członkowskiego z obiektu, tak jakby był rzeczywiście element członkowski zdefiniowany w klasie. Na przykład poniższy przykład `SimpleClass.ToString` wywołuje metodę, `SimpleClass` która <xref:System.Object>dziedziczy z .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

W poniższej tabeli wymieniono kategorie typów, które można utworzyć w języku C# i typy, z których niejawnie dziedziczą. Każdy typ podstawowy udostępnia inny zestaw elementów członkowskich za pośrednictwem dziedziczenia do typów niejawnie pochodnych.

| Kategoria typu | Niejawnie dziedziczy z                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| class         | <xref:System.Object>                                                          |
| struktura         | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| delegate      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dziedziczenie i relacja "jest"

Zwykle dziedziczenie służy do wyrażania relacji "jest" między klasą podstawową a jedną lub większą liczbą klas pochodnych, gdzie klasy pochodne są wyspecjalizowanymi wersjami klasy podstawowej; klasa pochodna jest typem klasy podstawowej. Na przykład `Publication` klasa reprezentuje publikację dowolnego rodzaju, `Book` `Magazine` a i klasy reprezentują określone typy publikacji.

> [!NOTE]
> Klasa lub struktura może zaimplementować jeden lub więcej interfejsów. Podczas gdy implementacja interfejsu jest często przedstawiana jako obejście dla pojedynczego dziedziczenia lub jako sposób używania dziedziczenia z strukturami, ma na celu wyrażenie innej relacji (relacji "można zrobić") między interfejsem a jego typem implementującym niż Dziedziczenia. Interfejs definiuje podzbiór funkcji (takich jak możliwość testowania równości, porównywania lub sortowania obiektów lub obsługi analizowania i formatowania zależnego od kultury), które interfejs udostępnia swoim typom implementacji.

Należy zauważyć, że "is a" wyraża również relację między typem a określonym wystąpienia tego typu. W poniższym `Automobile` przykładzie jest to klasa, która ma `Make`trzy unikalne właściwości tylko do odczytu: , producent samochodu; `Model`, rodzaj samochodu; i `Year`, rok produkcji. Klasa `Automobile` ma również konstruktora, którego argumenty są przypisane do <xref:System.Object.ToString%2A?displayProperty=nameWithType> wartości właściwości i zastępuje metodę `Automobile` do tworzenia `Automobile` ciągu, który jednoznacznie identyfikuje wystąpienie, a nie klasy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

W takim przypadku nie należy polegać na dziedziczeniu do reprezentowania konkretnych marek samochodów i modeli. Na przykład nie trzeba definiować typu reprezentującego `Packard` samochody produkowane przez Firmę Motorową Packard. Zamiast tego można je reprezentować, tworząc `Automobile` obiekt z odpowiednimi wartościami przekazanymi do jego konstruktora klasy, tak jak w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Relacja jest oparta na dziedziczeniu najlepiej jest stosowana do klasy podstawowej i klas pochodnych, które dodają dodatkowe elementy członkowskie do klasy podstawowej lub które wymagają dodatkowych funkcji nieobecnych w klasie podstawowej.

## <a name="designing-the-base-class-and-derived-classes"></a>Projektowanie klasy podstawowej i klas pochodnych

Przyjrzyjmy się procesowi projektowania klasy podstawowej i jej klas pochodnych. W tej sekcji zdefiniujesz klasę `Publication`podstawową, która reprezentuje wszelkiego rodzaju publikacje, takie jak książka, czasopismo, gazeta, czasopismo, artykuł itp. Zdefiniujesz również `Book` klasę, która `Publication`wywodzi się z . Można łatwo rozszerzyć przykład, aby zdefiniować inne `Magazine`klasy `Journal` `Newspaper`pochodne, takie jak , , , i `Article`.

### <a name="the-base-publication-class"></a>Podstawowa klasa publikacji

Projektując swoją `Publication` klasę, musisz podjąć kilka decyzji projektowych:

- Jakie elementy członkowskie do `Publication` uwzględnienia w `Publication` klasie podstawowej i `Publication` czy członkowie zapewniają implementacje metody lub czy jest abstrakcyjną klasą podstawową, która służy jako szablon dla jego klas pochodnych.

  W takim przypadku `Publication` klasa zapewni implementacje metody. [Projektowanie abstrakcyjnych klas podstawowych i ich klasy pochodne](#abstract) sekcja zawiera przykład, który używa abstrakcyjnej klasy podstawowej do definiowania metod, które klasy pochodne należy zastąpić. Klasy pochodne mogą zapewnić dowolną implementację, która jest odpowiednia dla typu pochodnego.

  Możliwość ponownego użycia kodu (czyli wiele klas pochodnych współużytkują deklarację i implementację metod klasy podstawowej i nie muszą je zastępować) jest zaletą nieabstrakcyjnych klas podstawowych. W związku z tym `Publication` należy dodać członków, jeśli ich kod `Publication` może być współużytkowany przez niektóre lub najbardziej wyspecjalizowanych typów. Jeśli nie uda ci się zapewnić implementacje klasy podstawowej wydajnie, będziesz musiał podać w dużej mierze identyczne implementacje elementów członkowskich w klasach pochodnych, a pojedynczą implementację w klasie podstawowej. Konieczność utrzymywania zduplikowanego kodu w wielu lokalizacjach jest potencjalnym źródłem błędów.

  Zarówno w celu zmaksymalizowania ponownego użycia kodu, jak i do utworzenia logicznej i intuicyjnej hierarchii dziedziczenia, należy mieć pewność, że w `Publication` klasie są uwzględniane tylko dane i funkcje, które są wspólne dla wszystkich lub dla większości publikacji. Klasy pochodne następnie implementują elementy członkowskie, które są unikatowe dla określonych rodzajów publikacji, które reprezentują.

- Jak daleko rozszerzyć hierarchię klas. Czy chcesz opracować hierarchię trzech lub więcej klas, a nie tylko klasy podstawowej i jednej lub więcej klas pochodnych? Na przykład `Publication` może być klasą `Periodical`podstawową , która `Magazine`z `Journal` `Newspaper`kolei jest klasą podstawową , i .

  W przykładzie użyjesz małej hierarchii `Publication` klasy i pojedynczej `Book`klasy pochodnej. Można łatwo rozszerzyć przykład, aby utworzyć szereg dodatkowych `Publication`klas, `Magazine` które `Article`pochodzą z , takich jak i .

- Czy ma sens tworzenie wystąpienia klasy podstawowej. Jeśli nie, należy zastosować [abstrakcyjne](../language-reference/keywords/abstract.md) słowo kluczowe do klasy. W przeciwnym `Publication` razie klasy można utworzyć wystąpienia przez wywołanie jego konstruktora klasy. Jeśli zostanie podjęta próba utworzenia wystąpienia klasy oznaczonej `abstract` słowem kluczowym przez bezpośrednie wywołanie jego konstruktora klasy, kompilator C# generuje błąd CS0144, "Nie można utworzyć wystąpienia klasy abstrakcyjnej lub interfejsu." Jeśli zostanie podjęta próba wystąpienia klasy przy użyciu odbicia, metoda odbicia <xref:System.MemberAccessException>wyrzuci .

  Domyślnie klasy podstawowej można utworzyć wystąpienia przez wywołanie jego konstruktora klasy. Nie trzeba jawnie zdefiniować konstruktora klasy. Jeśli nie jest obecny w kodzie źródłowym klasy podstawowej, kompilator C# automatycznie udostępnia domyślny (bezparametrowy) konstruktor.

  W przykładzie oznaczysz `Publication` klasę jako [abstrakcyjną,](../language-reference/keywords/abstract.md) aby nie można było jej utworzyć.  Klasa `abstract` bez `abstract` żadnych metod wskazuje, że ta klasa reprezentuje abstrakcyjną koncepcję, `Book` `Journal`która jest współużytkowana przez kilka konkretnych klas (takich jak , ).

- Czy klasy pochodne muszą dziedziczyć implementacji klasy podstawowej określonych elementów członkowskich, czy mają możliwość zastąpienia implementacji klasy podstawowej lub czy muszą one zapewnić implementację. Użyj [abstrakcyjne](../language-reference/keywords/abstract.md) słowo kluczowe wymusić klasy pochodne, aby zapewnić implementację. Słowo kluczowe [virtual](../language-reference/keywords/virtual.md) umożliwia klasy pochodne, aby zastąpić metodę klasy podstawowej. Domyślnie metody zdefiniowane w klasie podstawowej *nie* są nadawalne.

 Klasa `Publication` nie ma `abstract` żadnych metod, ale sama `abstract`klasa jest .

- Czy klasa pochodna reprezentuje ostateczną klasę w hierarchii dziedziczenia i sama nie może być używana jako klasa podstawowa dla dodatkowych klas pochodnych. Domyślnie każda klasa może służyć jako klasa podstawowa. Można zastosować [zapieczętowane](../language-reference/keywords/sealed.md) słowo kluczowe, aby wskazać, że klasa nie może służyć jako klasa podstawowa dla żadnych dodatkowych klas. Próbując wyprowadzić z zapieczętowanej klasy wygenerowany błąd kompilatora CS0509, "nie może pochodzić z typu zapieczętowanego \<typem>".

  Na przykład oznaczysz klasę pochodną `sealed`jako .

W poniższym przykładzie przedstawiono `Publication` kod źródłowy `PublicationType` dla klasy, a także `Publication.PublicationType` wyliczenie, które jest zwracane przez właściwość. Oprócz elementów członkowskich, które dziedziczy z <xref:System.Object>, `Publication` klasa definiuje następujące unikatowe elementy członkowskie i zastąpienia elementów członkowskich:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Ponieważ `Publication` klasa `abstract`jest , nie można utworzyć wystąpienia bezpośrednio z kodu, jak w poniższym przykładzie:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Jednak jego konstruktor wystąpienia można wywołać bezpośrednio z pochodnych konstruktorów klas, jak pokazuje kod źródłowy `Book` dla klasy.

- Dwie właściwości związane z publikacją

  `Title`jest właściwością <xref:System.String> tylko do odczytu, której `Publication` wartość jest dostarczana przez wywołanie konstruktora.

  `Pages`jest właściwością <xref:System.Int32> odczytu i zapisu, która wskazuje, ile całkowita liczba stron publikacji ma. Wartość jest przechowywana w `totalPages`polu prywatnym o nazwie . Musi to być liczba <xref:System.ArgumentOutOfRangeException> dodatnia lub wyrzucona.

- Członkowie związani z wydawcą

  Dwie właściwości tylko do `Publisher` `Type`odczytu i . Wartości są pierwotnie dostarczane przez wywołanie konstruktora `Publication` klasy.

- Członkowie związani z publikowaniem

  Dwie metody `Publish` i `GetPublicationDate`, ustawić i zwrócić datę publikacji. Metoda `Publish` ustawia flagę `published` prywatną, gdy `true` jest wywoływana i przypisuje datę `datePublished` przekazaną do niej jako argument do pola prywatnego. Metoda `GetPublicationDate` zwraca ciąg "NYP", `published` jeśli `false`flaga jest , `datePublished` a wartość `true`pola, jeśli jest .

- Członkowie związani z prawami autorskimi

  Metoda `Copyright` przyjmuje nazwę posiadacza praw autorskich i rok praw autorskich `CopyrightName` jako `CopyrightDate` argumenty i przypisuje je do i właściwości.

- Zastąpienie `ToString` metody

  Jeśli typ nie zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, zwraca w pełni kwalifikowaną nazwę typu, która jest mało użyteczna w odróżnianiu jednego wystąpienia od innego. Klasa `Publication` zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> zwracać wartość `Title` właściwości.

Na poniższej ilustracji przedstawiono `Publication` relację między klasą <xref:System.Object> podstawową a jej niejawnie dziedziczoną klasą.

![Klasy Obiekt i publikacja](media/publication-class.jpg)

### <a name="the-book-class"></a>Klasa `Book`

Klasa `Book` reprezentuje książkę jako wyspecjalizowany typ publikacji. W poniższym przykładzie przedstawiono `Book` kod źródłowy dla klasy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Oprócz elementów członkowskich, które dziedziczy z `Publication`, `Book` klasa definiuje następujące unikatowe elementy członkowskie i zastąpienia elementów członkowskich:

- Dwa konstruktory

  Dwa `Book` konstruktory mają trzy wspólne parametry. Dwa, *tytuł* i *wydawca*, `Publication` odpowiadają parametrom konstruktora. Trzeci to *autor*, który jest przechowywany `Author` w publicznej nieruchomości niezmiennej. Jeden konstruktor zawiera parametr *isbn,* który jest przechowywany w `ISBN` auto-właściwości.

  Pierwszy konstruktor używa [tego](../language-reference/keywords/this.md) słowa kluczowego do wywołania innego konstruktora. Łańcuchkonstruktora jest typowym wzorcem w definiowaniu konstruktorów. Konstruktorzy z mniejszą liczbą parametrów zapewniają wartości domyślne podczas wywoływania konstruktora z największą liczbą parametrów.

  Drugi konstruktor używa [podstawowego](../language-reference/keywords/base.md) słowa kluczowego, aby przekazać tytuł i nazwę wydawcy do konstruktora klasy podstawowej. Jeśli nie wygłoszą jawne wywołanie konstruktora klasy podstawowej w kodzie źródłowym, kompilator C# automatycznie dostarcza wywołanie domyślnego lub parametrnego konstruktora klasy podstawowej.

- Właściwość tylko `ISBN` do odczytu, `Book` która zwraca obiektinternational standard book number, unikatowy numer 10- lub 13-cyfrowy. NUMER ISBN jest dostarczany jako argument `Book` do jednego z konstruktorów. Numer ISBN jest przechowywany w prywatnym polu zapasowym, które jest automatycznie generowane przez kompilator.

- Właściwość tylko `Author` do odczytu. Nazwa autora jest dostarczana jako `Book` argument do obu konstruktorów i jest przechowywana we właściwości.

- Dwie właściwości związane z ceną `Price` tylko `Currency`do odczytu i . Ich wartości są dostarczane `SetPrice` jako argumenty w wywołaniu metody. Właściwość `Currency` jest trzycyfrowym symbolem waluty ISO (na przykład USD za dolara amerykańskiego). Symbole waluty ISO można pobrać <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> z obiektu. Obie te właściwości są zewnętrznie tylko do odczytu, ale `Book` oba mogą być ustawione przez kod w klasie.

- Metoda, `SetPrice` która ustawia wartości `Price` i `Currency` właściwości. Te wartości są zwracane przez te same właściwości.

- Zastępuje `ToString` metodę (dziedziczoną `Publication` <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> z ) <xref:System.Object.GetHashCode%2A> i i metody <xref:System.Object>(dziedziczone z ).

  Chyba że jest zastąpiona, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metoda testuje dla równości referencyjnej. Oznacza to, że dwie zmienne obiektowe są uważane za równe, jeśli odnoszą się do tego samego obiektu. W `Book` klasie, z drugiej strony, dwa `Book` obiekty powinny być równe, jeśli mają ten sam ISBN.

  Podczas zastępowania <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody, należy również <xref:System.Object.GetHashCode%2A> zastąpić metodę, która zwraca wartość, która jest używana do przechowywania elementów w kolekcjach haszhed dla wydajnego pobierania. Kod skrótu powinien zwracać wartość, która jest zgodna z testem równości. Ponieważ zostały zastąpione <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> do `true` zwrócenia, jeśli isbn `Book` właściwości dwóch obiektów są równe, należy zwrócić <xref:System.String.GetHashCode%2A> kod skrótu obliczone `ISBN` przez wywołanie metody ciągu zwrócone przez właściwość.

Na poniższej ilustracji przedstawiono `Book` relację między klasą a `Publication`jej klasą podstawową.

![Zajęcia z publikacji i książek](media/book-class.jpg)

Teraz można utworzyć wystąpienia `Book` obiektu, wywołać zarówno jego unikatowe i dziedziczone elementy członkowskie i przekazać `Publication` go jako `Book`argument do metody, która oczekuje parametr typu lub typu , jak pokazano w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Projektowanie abstrakcyjnych klas podstawowych i ich klas pochodnych
<a name="abstract"></a>

W poprzednim przykładzie zdefiniowano klasę podstawową, która dostarczyła implementację dla wielu metod, aby umożliwić klasy pochodne do udostępniania kodu. W wielu przypadkach jednak klasa podstawowa nie oczekuje się, aby zapewnić implementację. Zamiast tego klasa podstawowa jest *klasą abstrakcyjną,* która deklaruje *metody abstrakcyjne;* służy jako szablon, który definiuje elementy członkowskie, które każda klasa pochodna musi zaimplementować. Zazwyczaj w abstrakcyjnej klasie podstawowej implementacja każdego typu pochodnego jest unikatowa dla tego typu. Oznaczyłeś klasę abstrakcyjnym słowem kluczowym, ponieważ nie `Publication` ma sensu utworzyć wystąpienia obiektu, mimo że klasa dostarczyła implementacji funkcji wspólnych dla publikacji.

Na przykład każdy zamknięty dwuwymiarowy kształt geometryczny zawiera dwie właściwości: obszar, wewnętrzny zakres kształtu; obwodu lub odległości wzdłuż krawędzi kształtu. Sposób obliczania tych właściwości zależy jednak całkowicie od konkretnego kształtu. Formuła obliczania obwodu (lub obwodu) okręgu różni się na przykład od wzoru trójkąta. Klasa `Shape` jest `abstract` klasą `abstract` z metodami. Oznacza to, że klasy pochodne mają te same funkcje, ale te klasy pochodne implementują tę funkcję inaczej.

W poniższym przykładzie zdefiniowano `Shape` abstrakcyjną klasę podstawową o nazwie, która definiuje dwie właściwości: `Area` i `Perimeter`. Oprócz oznaczania klasy za pomocą [abstrakcyjnego](../language-reference/keywords/abstract.md) słowa kluczowego każdy element członkowski wystąpienia jest również oznaczony [abstrakcyjnym](../language-reference/keywords/abstract.md) słowem kluczowym. W takim `Shape` przypadku zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> również metodę zwracania nazwy typu, a nie jego w pełni kwalifikowaną nazwę. Definiuje dwa statyczne elementy `GetArea` członkowskie `GetPerimeter`i , które umożliwiają wywołującym łatwo pobrać obszar i obwód wystąpienia dowolnej klasy pochodnej. Po przekazaniu wystąpienia klasy pochodnej do jednej z tych metod, czas wykonywania wywołuje zastąpienie metody klasy pochodnej.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Następnie można wyprowadzić `Shape` niektóre klasy z tych reprezentujących określone kształty. Poniższy przykład definiuje trzy `Triangle`klasy, `Rectangle` `Circle`, , i . Każdy używa formuły unikatowej dla danego kształtu do obliczania obszaru i obwodu. Niektóre klasy pochodne również zdefiniować właściwości, `Rectangle.Diagonal` `Circle.Diameter`takie jak i , które są unikatowe dla kształtu, który reprezentują.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

W poniższym przykładzie użyto obiektów pochodzących z `Shape`. Tworzy tablicę obiektów pochodzących z `Shape` i wywołuje metody statyczne `Shape` klasy, która otacza `Shape` zwraca wartości właściwości. Czas wykonywania pobiera wartości z przesłoniętych właściwości typów pochodnych. Przykład również rzutuje `Shape` każdy obiekt w tablicy do jego typu pochodnego i, jeśli rzutowany `Shape`zakończy się pomyślnie, pobiera właściwości tej określonej podklasy .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Zobacz też

- [Klasy i obiekty](../tour-of-csharp/classes-and-objects.md)
- [Dziedziczenie (Przewodnik programowania w języku C#)](../programming-guide/classes-and-structs/inheritance.md)
