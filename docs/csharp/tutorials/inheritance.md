---
title: Dziedziczenie w języku C#
description: Sposoby używania dziedziczenia w aplikacjach i bibliotek C#.
author: rpetrusha
ms.author: ronpet
ms.date: 08/16/2017
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 1476425594e55531fdb56de531ee61808dccd7db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365764"
---
# <a name="inheritance-in-c-and-net"></a>Dziedziczenie w języku C# i .NET

W tym samouczku przedstawiono dziedziczenia w języku C#. Dziedziczenie jest funkcją zorientowane obiektowo języków programowania, która służy do definiowania klasy podstawowej, która zapewnia funkcje (dane i zachowanie) oraz do definiowania klas pochodnych, które dziedziczą lub Zastąp te funkcje.

## <a name="prerequisites"></a>Wymagania wstępne

Ten samouczek zakłada, że po zainstalowaniu platformy .NET Core. Aby uzyskać instrukcje instalacji, zobacz [Przewodnik instalacji platformy .NET Core](https://www.microsoft.com/net/core). Należy również edytora kodu. W tym samouczku używana [Visual Studio Code](https://code.visualstudio.com), chociaż można użyć dowolnego wybranego edytora kodu.

## <a name="running-the-examples"></a>Uruchamianie przykładów

Do tworzenia i uruchamiania przykładów w tym samouczku, użyj [dotnet](../../core/tools/dotnet.md) narzędzie z wiersza polecenia. Wykonaj następujące kroki na każdym przykład:

1. Utwórz katalog do przechowywania w przykładzie.
1. Wprowadź [dotnet nowej konsoli](../../core/tools/dotnet-new.md) polecenie w wierszu polecenia, aby utworzyć nowy projekt platformy .NET Core.
1. Skopiuj i Wklej kod w przykładzie do edytora kodu.
1. Wprowadź [przywracania dotnet](../../core/tools/dotnet-restore.md) polecenia z wiersza polecenia do ładowania lub Przywróć zależności projektu.

  [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Wprowadź [dotnet Uruchom](../../core/tools/dotnet-run.md) polecenie, aby skompilować i wykonać przykładzie.


## <a name="background-what-is-inheritance"></a>Tło: Co to jest dziedziczenia?

*Dziedziczenie* jest jednym z podstawowych atrybuty programowanie zorientowane obiektowo. Można zdefiniować klasy podrzędnej, które używa ponownie (dziedziczy) rozszerza lub modyfikuje zachowanie klasy nadrzędnej. Klasa, której członkami są dziedziczone jest nazywana *klasa podstawowa*. Klasa, która dziedziczy elementów członkowskich klasy podstawowej jest nazywany *klasy*.

C# i .NET obsługuje *pojedyncze dziedziczenie* tylko. Oznacza to, że klasa może dziedziczyć tylko z jednej klasy. Jednak dziedziczenia jest przechodnie, co pozwala na określanie hierarchii dziedziczenia dla zestawu typów. Innymi słowy, wpisz `D` może dziedziczyć z typu `C`, który dziedziczy z typu `B`, który dziedziczy z klasy podstawowej typu `A`. Ponieważ dziedziczenia jest przechodnie, elementy członkowskie typu `A` są dostępne dla typów `D`.

Nie wszystkie elementy członkowskie klasy podstawowej są dziedziczone przez klasy pochodnej. Następujące elementy członkowskie nie są dziedziczone:

- [Konstruktory statyczne](../programming-guide/classes-and-structs/static-constructors.md), który zainicjować danych statycznej klasy.

- [Konstruktory wystąpień](../programming-guide/classes-and-structs/constructors.md), które należy wywołać, aby utworzyć nowe wystąpienie klasy. Każda klasa musi definiować własnego konstruktorów.

- [Finalizatory](../programming-guide/classes-and-structs/destructors.md), które są wywoływane przez moduł Garbage Collector środowiska uruchomieniowego do zniszczenia wystąpienia klasy.

Podczas wszystkich innych członków klasy podstawowej są dziedziczone przez klasy pochodnej, czy są one widoczne czy nie zależy od ich dostępności. Dostępność elementu członkowskiego wpływa na jej widoczność klas pochodnych w następujący sposób:

- [Prywatne](../language-reference/keywords/private.md) elementy są widoczne tylko w klasach pochodnych, które są zagnieżdżone w ich klasy podstawowej. W przeciwnym razie nie są widoczne w klasach pochodnych. W poniższym przykładzie `A.B` jest zagnieżdżona klasa, która jest pochodną `A`, i `C` pochodną `A`. Prywatna `A.value` pole jest widoczne w A.B. Jednak jeśli Usuń komentarze z `C.GetValue` metody, a następnie spróbuj skompilować w przykładzie generuje błąd kompilatora CS0122: "" A.value"jest niedostępny z powodu swojego poziomu ochrony."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chronione](../language-reference/keywords/protected.md) elementy są widoczne tylko w klasach pochodnych.

- [Wewnętrzny](../language-reference/keywords/internal.md) elementy są widoczne tylko w klasach pochodnych, które znajdują się w tym samym zestawie co klasy podstawowej. Nie są widoczne w klasach pochodnych znajduje się w innym zestawie od klasy podstawowej.

- [Publiczny](../language-reference/keywords/public.md) elementy członkowskie są widoczne w klasach pochodnych i są częścią interfejs publiczny klasy pochodnej. Tak jak gdyby zostały one zdefiniowane w klasie pochodnej można wywołać publicznej dziedziczone elementy członkowskie. W poniższym przykładzie klasa `A` definiuje metodę o nazwie `Method1`, a klasa `B` dziedziczy z klasy `A`. Przykład wywołuje `Method1` tak jakby był on metodę wystąpienia `B`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Klasy pochodne mogą również *zastąpienia* dziedziczone elementy członkowskie, dostarczając implementację alternatywny. Aby można było zastąpić członka, muszą być oznaczone element członkowski w klasie podstawowej [wirtualnego](../language-reference/keywords/virtual.md) — słowo kluczowe. Domyślnie elementów członkowskich klasy podstawowej nie są oznaczone jako `virtual` i nie może zostać zastąpiona. Próba zastąpienia Niewirtualny element członkowski, tak jak w poniższym przykładzie, generuje błąd kompilatora CS0506: "<member> nie można przesłonić dziedziczonego elementu członkowskiego <member> , ponieważ nie jest oznaczona wirtualny, abstrakcyjny lub zastąpienie.

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

W niektórych przypadkach, w klasie pochodnej *musi* zastąpienia implementacji klasy podstawowej. Oznaczonej jako elementów członkowskich klasy podstawowej [abstrakcyjny](../language-reference/keywords/abstract.md) — słowo kluczowe wymagają klas pochodnych zastąpić je. Próba skompilowania w poniższym przykładzie generuje błąd kompilatora CS0534, "<class> nie implementuje odziedziczonego abstrakcyjnego elementu członkowskiego <member>", ponieważ klasa `B` zapewnia implementacji `A.Method1`.

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

Dziedziczenie ma zastosowanie tylko do klasy i interfejsy. Innych kategorii typu (struktur, delegatów i typy wyliczeniowe) nie obsługuje dziedziczenia. Z tego powodu próby kompilowania kodu podobnie do następującej powoduje błąd kompilatora CS0527: "Typu"ValueType"na liście interfejsów nie jest interfejsem." Komunikat o błędzie oznacza, że chociaż można zdefiniować interfejsów, które implementuje struktury, dziedziczenia nie jest obsługiwany.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Niejawne dziedziczenia

Oprócz żadnych typów, które mogą dziedziczyć przez pojedyncze dziedziczenie, wszystkie typy w systemie typów .NET niejawnie dziedziczyć po <xref:System.Object> lub typ pochodzący od niego. Dzięki temu, że typowe funkcje są dostępne do dowolnego typu.

Aby zobaczyć, jakie niejawne dziedziczenia oznacza, że zdefiniujmy nową klasę `SimpleClass`, to po prostu definicja pustej klasy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Następnie wykorzystamy odbicia (co pozwala nam sprawdzić metadanych typów, aby uzyskać informacje o tym typie) w celu uzyskania listy elementów członkowskich, które należą do `SimpleClass` typu. Mimo że firma Microsoft nie zdefiniowano żadnych elementów członkowskich w naszym `SimpleClass` klasy, dane wyjściowe z przykładu wskazuje, że faktycznie ma dziewięciu członków. Jednym z nich jest konstruktora (domyślny lub bezparametryczny), który jest automatycznie udostępniane dla `SimpleClass` typu za pomocą kompilatora C#. Pozostałe osiem są elementami członkowskimi <xref:System.Object>, dziedziczą typu, w którym wszystkie klasy i interfejsy, w ramach platformy .NET system typów ostatecznie niejawnie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Niejawne dziedziczenia z <xref:System.Object> klasy udostępnia następujące metody `SimpleClass` klasy:

- Publicznego `ToString` metodę, która konwertuje `SimpleClass` obiektu do reprezentacji ciągu zwraca w pełni kwalifikowana nazwa typu. W takim przypadku `ToString` metoda zwraca ciąg "SimpleClass".

- Trzy metody, które testu równości dwóch obiektów: wystąpienia publicznego `Equals(Object)` metoda, publiczne statyczne `Equals(Object, Object)` — metoda i publiczne statyczne `ReferenceEquals(Object, Object)` metody. Domyślnie te metody testowanie równości odwołań; oznacza to aby być taka sama, dwie zmienne obiektu musi odwoływać się do tego samego obiektu.

- Publicznego `GetHashCode` metodę, która oblicza wartość, która umożliwia wystąpienie typu do użycia w formie skrótu kolekcjach.

- Publicznego `GetType` metody, która zwraca <xref:System.Type> obiekt, który reprezentuje `SimpleClass` typu.

- Chronionej <xref:System.Object.Finalize%2A> metodę, która jest przeznaczona do zwolnić zasoby niezarządzane, zanim pamięci obiektu jest odzyskana przez moduł garbage collector.

- Chronionej <xref:System.Object.MemberwiseClone%2A> metodę, która tworzy pobieżnego klonu bieżącego obiektu.

Z powodu niejawne dziedziczenia, mogą nazywa się żadnych dziedziczonego elementu członkowskiego z `SimpleClass` obiekt tak, jakby był faktycznie elementu członkowskiego zdefiniowany w `SimpleClass` klasy. Na przykład poniższy przykład wywołuje `SimpleClass.ToString` — metoda, która `SimpleClass` dziedziczy <xref:System.Object>.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

W poniższej tabeli wymieniono kategorie typów, które możesz utworzyć w języku C# i typów, z których niejawnie dziedziczą. Każdy typ podstawowy udostępnia zestaw elementów członkowskich poprzez dziedziczenie typów pochodnych niejawnie.

| Typ kategorii | Niejawnie dziedziczy                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| class         | <xref:System.Object>                                                          |
| struktura         | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| delegate      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dziedziczenie i "to" relacji

Zwykle dziedziczenia jest używany do wyrażenia "jest" relację między klasą bazową i co najmniej jednej klasy pochodnej, gdzie klas pochodnych są specjalne wersje klasy podstawowej; Klasa pochodna jest typem klasy podstawowej. Na przykład `Publication` klasa reprezentuje publikacji dowolnego rodzaju i `Book` i `Magazine` klasy reprezentują określonych rodzajów publikacji.

> [!NOTE]
> Co więcej interfejsów można zaimplementować w klasie lub strukturze. Podczas implementacji interfejsu często jest przedstawiony jako obejścia pojedyncze dziedziczenie lub sposób korzystania ze struktury dziedziczenia, jest on przeznaczony do innej relacji (relację "można wykonać") między interfejs i jej typ implementujący niż express dziedziczenie. Interfejs definiuje podzbiór funkcji (na przykład możliwości testu równości do porównywania lub sortowania obiektów, lub do obsługi zależne od kultury analizowania i formatowanie), która udostępnia interfejs do jego implementującej typów.

Należy pamiętać, że "jest" wyraża również relacji między typem i konkretnego wystąpienia tego typu. W poniższym przykładzie `Automobile` jest klasa, która ma trzy unikatowe właściwości tylko do odczytu: `Make`, producenta samochodów; `Model`, rodzaj samochodów; i `Year`, rok produkcji. Nasze `Automobile` klasa ma również konstruktora, którego argumenty są przypisane do wartości właściwości i zastępuje on <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, aby utworzyć ciąg, który unikatowo identyfikuje `Automobile` wystąpienia zamiast `Automobile` klasy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

W takim przypadku firma Microsoft nie miały dziedziczenia do reprezentowania sprawia, że określonego samochód i modeli. Na przykład nie musimy zdefiniować `Packard` typu do reprezentowania wyprodukowanych przez firmę samochodu motocykla Packard samochodów. Zamiast tego, firma Microsoft może reprezentować je przez utworzenie `Automobile` obiektu z odpowiednimi wartościami przekazanych do jego konstruktora klasy, tak jak w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Relację a jest oparte na dziedziczenia najlepiej jest stosowany do klasy podstawowej i pochodnej klasy dodatkowych członków dodaje do klasy podstawowej lub wymagających dodatkowe funkcje, które nie znajduje się w klasie podstawowej.

## <a name="designing-the-base-class-and-derived-classes"></a>Projektowanie klasy podstawowej i klasy pochodne

Oto proces projektowania klasy podstawowej i jej klas pochodnych. W tej sekcji zdefiniujemy klasę podstawową `Publication`, reprezentuje publikacji dowolnego rodzaju, takie jak książkę, magazynu, gazecie, arkusz, artykułu itp. Zdefiniujemy również `Book` klasą pochodzącą z `Publication`. Firma Microsoft może łatwo rozszerzyć przykład zdefiniuj inne klas pochodnych, takich jak `Magazine`, `Journal`, `Newspaper`, i `Article`.

### <a name="the-base-publication-class"></a>Klasa podstawowa publikacji

W projektowaniu naszych `Publication` klasy, należy podjąć kilka decyzje dotyczące projektu:

- Jakie elementy członkowskie do uwzględnienia w naszej bazie `Publication` klasy oraz tego, czy `Publication` członków Podaj implementacji metody, lub czy `Publication` jest abstrakcyjna klasa podstawowa, która służy jako szablon dla jej klas pochodnych.

  W takim przypadku `Publication` klasy zapewni implementacje metod. [Opracowywania abstrakcyjnych klas podstawowych i ich pochodne](#abstract) sekcji przedstawiono przykładową, która używa abstrakcyjnego klasy podstawowej w celu zdefiniowania metody, które klasy pochodne muszą przesłaniać. Klasy pochodne mogą się do żadnych implementacji, które jest odpowiednie dla typu pochodnego.

  Możliwość ponownego użycia kodu (oznacza to, wielu klas pochodnych udział deklaracji i implementacji podstawowej metody klasy i nie powinny być one zastąpione) jest zaletą nieabstrakcyjnej klasy podstawowej. W związku z tym należy dodawać członków do `Publication` w przypadku ich kod może być współużytkowane przez niektóre lub najbardziej specjalizowany `Publication` typów. Jeśli firma Microsoft nie powiedzie się w tym celu wydajnie, firma Microsoft będzie przechodzili konieczności podawania implementacje przeważającej mierze identyczny elementów członkowskich w klasach pochodnych raczej pojedynczą implementacją w klasie podstawowej. To konieczności obsługiwania zduplikowany kod w wielu lokalizacjach jest źródłem potencjalnych błędów.

  Zarówno do zmaksymalizowania kodu ponownemu i utwórz hierarchię dziedziczenia logicznych i intuicyjne, chcemy należy upewnić się, że przeprowadzamy w `Publication` klasy tylko dane i funkcje, które są wspólne dla wszystkich lub do większości publikacji. Klasy pochodne następnie implementacji elementów członkowskich, które są unikatowe dla określonego rodzaju publikacji, które reprezentują.

- Jak do tej pory rozszerzyć naszych hierarchii klas. Czy chcemy tworzenie hierarchii co najmniej trzech klas, a nie po prostu klasy podstawowej i co najmniej jednej klasy pochodnej? Na przykład `Publication` może być klasą podstawową `Periodical`, który z kolei jest klasą podstawową `Magazine`, `Journal` i `Newspaper`.

  W naszym przykładzie użyjemy proste hierarchię `Publication` klasy i jednej klasy pochodne `Book`. Firma Microsoft może łatwo rozszerzyć przykład, aby utworzyć wiele dodatkowych klas, które pochodzą z `Publication`, takich jak `Magazine` i `Article`.

- Czy warto utworzyć wystąpienia klasy podstawowej. Jeśli nie, firma Microsoft stosuje [abstrakcyjny](../language-reference/keywords/abstract.md) — słowo kluczowe do klasy. Jeśli do utworzenia wystąpienia klasy oznaczonej jako podejmowana jest próba `abstract` — słowo kluczowe przez bezpośrednie wywołanie dla jego konstruktora klasy kompilatora C# generuje błąd CS0144 "Nie można utworzyć wystąpienia klasy abstrakcyjnej lub interfejsu". Jeśli do utworzenia wystąpienia tej klasy przy użyciu odbicia, zgłasza metody odbicia podejmowana jest próba <xref:System.MemberAccessException>. W przeciwnym razie naszych `Publication` można tworzyć wystąpienia klasy przez wywołanie jego konstruktora klasy.

  Domyślnie klasy podstawowej można wdrożyć przez wywołanie jego konstruktora klasy. Należy pamiętać, że firma Microsoft nie trzeba jawnie definiować konstruktora klasy. Jeśli jedno nie jest obecny w kodzie źródłowym klasy podstawowej, kompilator języka C# automatycznie zapewnia domyślnego (bezparametrowego) konstruktora.

  W naszym przykładzie firma Microsoft będzie oznaczyć `Publication` klasy [abstrakcyjny](../language-reference/keywords/abstract.md) tak, aby nie można utworzyć wystąpienia.

- Czy klasy pochodne muszą dziedziczyć wykonania określonych elementów członkowskich klasy podstawowej, lub czy mają możliwość zastąpienia implementacji klasy podstawowej. Mamy użyj [wirtualnego](../language-reference/keywords/virtual.md) — słowo kluczowe, aby umożliwić klasy pochodne zastąpić metody klasy podstawowej. Domyślnie jest zdefiniowana w klasie podstawowej metody *nie* możliwym do zastąpienia.

- Określa, czy klasa pochodna reprezentuje klasę końcowe w hierarchii dziedziczenia i nie może sam służyć jako klasę podstawową dla dodatkowych klas pochodnych. Domyślnie każda klasa może służyć jako klasę podstawową. Możemy zastosować [zapieczętowanego](../language-reference/keywords/sealed.md) — słowo kluczowe, aby wskazać, że klasa nie może służyć jako klasę podstawową dla wszystkich dodatkowych klas. Podjęto próbę pochodzi od klasy zapieczętowanej wygenerowany błąd kompilatora CS0509, "nie może pochodzić od typu zapieczętowanego <typeName>".

  W naszym przykładzie mamy oznaczyć naszej klasy pochodnej jako `sealed`.

W poniższym przykładzie pokazano kod źródłowy `Publication` klasy, a także `PublicationType` wyliczenia, która jest zwracana w wyniku `Publication.PublicationType` właściwości. Oprócz elementów członkowskich, które dziedziczy on z <xref:System.Object>, `Publication` klasa definiuje następujące unikatowych elementów członkowskich i element członkowski zastępuje element:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Ponieważ `Publication` jest klasa `abstract`, nie można utworzyć wystąpienia bezpośrednio z kodu podobnie do następującej:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Jednak można wywołać jej konstruktora wystąpienia bezpośrednio z konstruktorów w klasie pochodnej, jako kod źródłowy `Book` pokazuje klasy.

- Dwie właściwości związanych z publikacji

  `Title` jest tylko do odczytu <xref:System.String> właściwości, której wartość jest dostarczana przez wywołanie `Publication` konstruktora.

  `Pages` jest odczytu i zapisu <xref:System.Int32> ma właściwość, która wskazuje, ile łączna liczba stron publikacji. Wartość jest przechowywana w polu prywatnej o nazwie `totalPages`. Musi być liczbą dodatnią lub <xref:System.ArgumentOutOfRangeException> jest generowany.

- Wydawca związane z członków

  Dwie właściwości tylko do odczytu, `Publisher` i `Type`. Wartości pierwotnie są dostarczane przez wywołanie `Publication` konstruktora klasy.

- Dotyczące publikowania elementów członkowskich

  Dwie metody `Publish` i `GetPublicationDate`, ustawianie i zwracanie dat publikacji. `Publish` Metoda ustawia prywatnej `published` flaga `true` gdy jest wywoływana i przypisuje daty do niej przekazany jako argument prywatna `datePublished` pola. `GetPublicationDate` Metoda zwraca ciąg "NYP", jeśli `published` flaga jest `false`i wartość `datePublished` pola, jeśli jest `true`.

- Pokrewnych elementów członkowskich

  `Copyright` Metoda przyjmuje jako argumenty nazwę autorskich oraz roku praw autorskich i przypisuje je do `CopyrightName` i `CopyrightDate` właściwości.

- Zastępowanie `ToString` — metoda

  Jeśli typ nie przesłania <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda zwraca w pełni kwalifikowana nazwa typu, który jest rzadko używane w rozróżnianie jedno wystąpienie z innej. `Publication` Klasy zastąpienia <xref:System.Object.ToString%2A?displayProperty=nameWithType> do zwracania wartości `Title` właściwości.

Na poniższym rysunku przedstawiono relacje między naszych base `Publication` klasy i jego niejawnie dziedziczenia <xref:System.Object> klasy.

![Klasy obiektów i publikacji](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book` — Klasa

`Book` Klasa reprezentuje książkę jako specjalistyczną odmianą publikacji. W poniższym przykładzie pokazano kod źródłowy `Book` klasy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Oprócz elementów członkowskich, które dziedziczy on z `Publication`, `Book` klasa definiuje następujące unikatowych elementów członkowskich i element członkowski zastępuje element:

- Dwa konstruktory

  Dwa `Book` konstruktorów udostępnianie trzy typowych parametrów. Dwa, *tytuł* i *wydawcy*, odpowiadają parametrom `Publication` konstruktora. Trzeci jest *autora*, który jest przechowywany prywatną `authorName` pola. Zawiera jeden konstruktor *isbn* parametr, który jest przechowywany w `ISBN` auto właściwością.

  Używa pierwszego konstruktora [to](../language-reference/keywords/this.md) — słowo kluczowe do wywoływania innego konstruktora. Jest to wspólnego wzorca podczas definiowania konstruktorów. Konstruktorów z parametrami mniej podać wartości domyślne podczas wywoływania konstruktora z największą liczbą parametrów.

  Drugi Konstruktor korzysta [podstawowej](../language-reference/keywords/base.md) — słowo kluczowe do przekazania do konstruktora klasy podstawowej nazwy stanowiska i wydawcy. Jeśli nie wprowadzisz jawnym wywołaniem konstruktora klasy podstawowej w kodzie źródłowym, kompilator języka C# automatycznie dostarcza wywołanie domyślnego lub konstruktora klasy podstawowej.

- Tylko do odczytu `ISBN` właściwość, która zwraca `Book` obiektu Międzynarodowy Znormalizowany Numer książki, unikatowe 10 - lub 13-cyfrowy numer. ISBN jest podana jako argument do jednego z `Book` konstruktorów. ISBN są przechowywane w polem zapasowym prywatny, który został wygenerowany automatycznie przez kompilator.

- Tylko do odczytu `Author` właściwości. Imię i nazwisko autora jest podana jako argument do obu `Book` konstruktory i jest przechowywany w prywatnej `authorName` pola.

- Dwie właściwości tylko do odczytu dotyczące cen, `Price` i `Currency`. Ich wartości są przekazywane jako argumenty `SetPrice` wywołania metody. Cena jest przechowywany w prywatnej pola, `bookPrice`. `Currency` Jest symbol waluty ISO cyfry (na przykład USD dla dolara amerykańskiego) i jest przechowywany w prywatnej `ISOCurrencySymbol` pola. ISO waluty symboli może zostać pobrany z <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> właściwości.

- A `SetPrice` metodę, która ustawia wartości `bookPrice` i `ISOCurrencySymbol` pól. Są to wartości zwracanych przez `Price` i `Currency` właściwości.

- Zastąpień w celu `ToString` — metoda (dziedziczone z `Publication`) i <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> i <xref:System.Object.GetHashCode%2A> metod (dziedziczone z <xref:System.Object>).

  Jeśli nie zostanie on przesłonięty <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> testy metoda równości odwołań. Oznacza to, że dwie zmienne obiektu są traktowane jako równe odnoszące się do tego samego obiektu. W przypadku liczby `Book` klasy, z drugiej strony, dwa `Book` obiekty powinny być takie same, jeśli mają tego samego ISBN.

  Jeśli zastąpienie <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody, należy również zmienić <xref:System.Object.GetHashCode%2A> metody, która zwraca wartość, która środowiska uruchomieniowego używa do przechowywania elementów w kolekcjach skrótem wydajne pobierania. Wartość skrótu powinien zwrócić wartość, która jest zgodna z testowanie równości. Ponieważ firma Microsoft została zastąpiona <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> do zwrócenia `true` Jeśli właściwości ISBN dwóch `Book` obiekty są takie same, zostanie zwrócona wartość skrótu obliczana przez wywołanie metody <xref:System.String.GetHashCode%2A> ciąg zwracany przez metodę `ISBN` właściwości.

Na poniższym rysunku przedstawiono relacje między `Book` klasy i `Publication`, jej klasy podstawowej.

![Klasy publikacji i książki](media/book-class.jpg)

Mamy teraz utworzyć wystąpienia `Book` obiektów, wywołanie jej unikatowy i dziedziczonych członków i przekaż go jako argument do metody, która oczekuje parametru typu `Publication` lub typu `Book`, jak pokazano na poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Opracowywania abstrakcyjnych klas podstawowych i ich pochodne
<a name="abstract"></a>

W poprzednim przykładzie zdefiniowanego przewidzianego implementację metody umożliwiają klasy pochodne udostępnić kod klasy podstawowej. W wielu przypadkach jednak klasy podstawowej nie powinien zapewniać implementację. Klasa podstawowa jest *klasy abstrakcyjnej*; służy jako szablon, który definiuje elementy każdej klasie pochodnej musi implementować. Zwykle w przypadku abstrakcyjna klasa podstawowa implementacja każdego typu pochodnego jest unikatowa dla tego typu.

Na przykład zamknięty kształt dwuwymiarowy geometrycznych zawiera dwie właściwości: obszar, wewnętrzny zakres kształtu; i obwodowej lub odległości wzdłuż krawędzi kształtu. Sposób, w którym mają być obliczane te właściwości, jednak zależy całkowicie określonego kształtu. Obliczanie obwodowej (lub obwodu) koło, na przykład bardzo różni się od elementu trójkąt.

W poniższym przykładzie zdefiniowano abstrakcyjna klasa podstawowa o nazwie `Shape` definiuje dwie właściwości: `Area` i `Perimeter`. Należy zauważyć, że oprócz oznaczyć klasę atrybutem [abstrakcyjny](../language-reference/keywords/abstract.md) — słowo kluczowe, każdy element członkowski wystąpienia również jest oznaczony atrybutem [abstrakcyjny](../language-reference/keywords/abstract.md) — słowo kluczowe. W takim przypadku `Shape` zastępuje również <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, aby zwrócić nazwę typu, a nie w pełni kwalifikowanej nazwy. I definiuje dwa elementy członkowskie static, `GetArea` i `GetPerimeter`, który zezwalać elementom wywołującym można łatwo pobrać i obwód wystąpienie klasy pochodnej. Gdy wystąpienie klasy pochodnej jest przekazywana do żadnej z tych metod, środowisko urchomieniowe wywołuje metodę zastępującą klasy pochodnej.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Firma Microsoft może następnie wyprowadzać niektóre klasy z `Shape` reprezentujące określonych kształtów. W poniższym przykładzie zdefiniowano trzech klas `Triangle`, `Rectangle`, i `Circle`. Formuła unikatowe dla tego konkretnego kształtu każdego używa do wyliczenia powierzchni i obwodu. Niektóre z klasy pochodnej także zdefiniować właściwości, takie jak `Rectangle.Diagonal` i `Circle.Diameter`, które są unikatowe dla kształtu, który reprezentuje.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

W poniższym przykładzie użyto obiektów pochodzących od `Shape`. Metoda tworzy tablicę obiektów pochodzących od `Shape` i wywołania metod statycznych `Shape` klasy, która opakowuje zwrotu `Shape` wartości właściwości. Należy pamiętać, że środowisko wykonawcze pobiera wartości z zastąpione właściwości z typów pochodnych. Przykład również rzutowań w każdym `Shape` obiektu w tablicy, tak aby jego pochodny typ i, jeśli rzutowanie zakończy się powodzeniem, pobiera właściwości tego konkretnego podklasą klasy `Shape`. 

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Zobacz także

[Klasy i obiekty](../tour-of-csharp/classes-and-objects.md)   
[Dziedziczenie (C# przewodnik programowania w języku)](../programming-guide/classes-and-structs/inheritance.md)
