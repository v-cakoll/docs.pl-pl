---
title: 'Dziedziczenie w C #'
description: Naucz się używać dziedziczenia w bibliotekach i aplikacjach języka C#.
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 78833110db0e4f0382e5c0c6de7c6c8be9a16c8d
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391152"
---
# <a name="inheritance-in-c-and-net"></a>Dziedziczenie w języku C# i .NET

W tym samouczku przedstawiono dziedziczenie w języku C#. Dziedziczenie jest funkcją zorientowanych obiektowo języków programowania, która pozwala zdefiniować klasę podstawową, która zapewnia określone funkcje (dane i zachowanie) i zdefiniować klasy pochodne, które dziedziczą lub zastępują tę funkcjonalność.

## <a name="prerequisites"></a>Wymagania wstępne

W tym samouczku przyjęto założenie, że zainstalowano pakiet SDK .NET Core. Odwiedź stronę [pobierania rdzenia .NET,](https://dotnet.microsoft.com/download) aby ją pobrać. Potrzebny jest również edytor kodu. W tym samouczku użyto [programu Visual Studio Code](https://code.visualstudio.com), chociaż można użyć dowolnego edytora kodu do wyboru.

## <a name="running-the-examples"></a>Uruchamianie przykładów

Aby utworzyć i uruchomić przykłady w tym samouczku, należy użyć narzędzia [dotnet](../../core/tools/dotnet.md) z wiersza polecenia. Wykonaj następujące kroki dla każdego przykładu:

1. Utwórz katalog do przechowywania przykładu.
1. Wprowadź polecenie [dotnet nowej konsoli](../../core/tools/dotnet-new.md) w wierszu polecenia, aby utworzyć nowy projekt .NET Core.
1. Kopiowanie i wklejenie kodu z przykładu do edytora kodu.
1. Wprowadź polecenie [przywracania dotnet](../../core/tools/dotnet-restore.md) z wiersza polecenia, aby załadować lub przywrócić zależności projektu.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Wprowadź polecenie [dotnet run,](../../core/tools/dotnet-run.md) aby skompilować i wykonać przykład.

## <a name="background-what-is-inheritance"></a>Tło: Co to jest dziedziczenie?

*Dziedziczenie* jest jednym z podstawowych atrybutów programowania obiektowego. Umożliwia zdefiniowanie klasy podrzędnej, która ponownie używa (dziedziczy), rozszerza lub modyfikuje zachowanie klasy nadrzędnej. Klasa, której członkowie są dziedziczone, jest nazywana *klasą podstawową*. Klasa, która dziedziczy członków klasy podstawowej, jest *nazywana klasą pochodną*.

C# i .NET obsługują tylko *pojedyncze dziedziczenie.* Oznacza to, że klasa może dziedziczyć tylko z jednej klasy. Jednak dziedziczenie jest przechodnie, co pozwala na zdefiniowanie hierarchii dziedziczenia dla zestawu typów. Innymi słowy, `D` typ może `C`dziedziczyć z `B`typu , który dziedziczy `A`po typie , który dziedziczy z typu klasy podstawowej . Ponieważ dziedziczenie jest przechodnie, `A` elementy członkowskie `D`typu są dostępne do wpisywać .

Nie wszystkie elementy członkowskie klasy podstawowej są dziedziczone przez klasy pochodne. Następujące elementy członkowskie nie są dziedziczone:

- [Konstruktory statyczne](../programming-guide/classes-and-structs/static-constructors.md), które inicjują dane statyczne klasy.

- [Konstruktory instancji](../programming-guide/classes-and-structs/constructors.md), które można wywołać, aby utworzyć nowe wystąpienie klasy. Każda klasa musi zdefiniować własne konstruktory.

- [Finalizatory](../programming-guide/classes-and-structs/destructors.md), które są wywoływane przez moduł zbierający elementy bezużyteczne środowiska wykonawczego, aby zniszczyć wystąpienia klasy.

Podczas gdy wszystkie inne elementy członkowskie klasy podstawowej są dziedziczone przez klasy pochodne, czy są one widoczne, czy nie zależy od ich dostępności. Dostępność elementu członkowskiego wpływa na jego widoczność dla klas pochodnych w następujący sposób:

- [Prywatne](../language-reference/keywords/private.md) elementy członkowskie są widoczne tylko w klasach pochodnych, które są zagnieżdżone w ich klasie podstawowej. W przeciwnym razie nie są one widoczne w klasach pochodnych. W poniższym `A.B` przykładzie jest klasą zagnieżdżoną, która wywodzi się z `A`i `C` wywodzi się z `A`. Pole `A.value` prywatne jest widoczne w trybie A.B. Jednak jeśli usuniesz `C.GetValue` komentarze z metody i spróbujesz skompilować przykład, generuje błąd kompilatora CS0122: "'A.value' jest niedostępny ze względu na jego poziom ochrony."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chronione elementy](../language-reference/keywords/protected.md) członkowskie są widoczne tylko w klasach pochodnych.

- [Elementy wewnętrzne](../language-reference/keywords/internal.md) są widoczne tylko w klasach pochodnych, które znajdują się w tym samym zestawie co klasa podstawowa. Nie są one widoczne w klasach pochodnych znajdujących się w innym zestawie niż klasa podstawowa.

- [Elementy](../language-reference/keywords/public.md) publiczne są widoczne w klasach pochodnych i są częścią interfejsu publicznego klasy pochodnej. Publiczne dziedziczone elementy członkowskie mogą być wywoływane tak, jakby były zdefiniowane w klasie pochodnej. W poniższym przykładzie `A` klasa definiuje `Method1`metodę `B` o nazwie `A`, a klasa dziedziczy z klasy . W przykładzie `Method1` następnie wywołuje tak, `B`jakby była to metoda wystąpienia na .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Klasy *pochodne* mogą również zastąpić odziedziczone elementy członkowskie, zapewniając alternatywną implementację. Aby można było zastąpić element członkowski, element członkowski w klasie podstawowej musi być oznaczony [wirtualnym](../language-reference/keywords/virtual.md) słowem kluczowym. Domyślnie elementy członkowskie klasy podstawowej nie są oznaczone jako `virtual` i nie mogą zostać zastąpione. Próba zastąpienia elementu członkowskiego niebędącego wirtualnym, zgodnie z poniższym przykładem, generuje błąd\<kompilatora CS0506: \<" element członkowski> nie może zastąpić dziedziczonego elementu członkowskiego>, ponieważ nie jest oznaczony jako wirtualny, abstrakcyjny lub zastąpiony.

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

W niektórych przypadkach klasa pochodna *musi* zastąpić implementacji klasy podstawowej. Elementy członkowskie klasy podstawowej oznaczone [abstrakcyjnym](../language-reference/keywords/abstract.md) słowem kluczowym wymagają, aby klasy pochodne je zastępować. Próba skompilowania poniższego przykładu generuje błąd kompilatora&gt; CS0534, &lt;&gt;"&lt;klasa `B` nie implementuje dziedziczonego abstrakcyjnego elementu członkowskiego ", ponieważ klasa nie zapewnia implementacji dla `A.Method1`.

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

Dziedziczenie dotyczy tylko klas i interfejsów. Inne kategorie typów (struktury, delegatów i wyliczenia) nie obsługują dziedziczenia. Z powodu tych reguł próba skompilowania kodu, podobnie jak w poniższym przykładzie, powoduje błąd kompilatora CS0527: "Typ 'ValueType' na liście interfejsów nie jest interfejsem." Komunikat o błędzie wskazuje, że chociaż można zdefiniować interfejsy, które implementuje struktury, dziedziczenie nie jest obsługiwane.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Dziedziczenie niejawne

Oprócz typów, które mogą dziedziczyć za pośrednictwem pojedynczego dziedziczenia, <xref:System.Object> wszystkie typy w systemie typu .NET niejawnie dziedziczą lub typu pochodnego z niego. Wspólna funkcjonalność <xref:System.Object> jest dostępna dla każdego typu.

Aby zobaczyć, co oznacza dziedziczenie niejawne, zdefiniujmy nową klasę, `SimpleClass`czyli po prostu pustą definicję klasy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Następnie można użyć odbicia (co pozwala sprawdzić metadane typu, aby uzyskać informacje o tym typie), aby uzyskać listę elementów członkowskich, które należą do `SimpleClass` typu. Mimo że nie zdefiniowano żadnych `SimpleClass` elementów członkowskich w klasie, dane wyjściowe z przykładu wskazuje, że faktycznie ma dziewięć elementów członkowskich. Jeden z tych elementów członkowskich jest konstruktorem bez parametrów (lub domyślnym), który jest automatycznie dostarczany dla `SimpleClass` typu przez kompilator języka C#. Pozostałe osiem to <xref:System.Object>członkowie , typ, z którego wszystkie klasy i interfejsy w systemie typu .NET ostatecznie niejawnie dziedziczą.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Niejawne <xref:System.Object> dziedziczenie z klasy `SimpleClass` udostępnia te metody do klasy:

- Metoda `ToString` publiczna, która `SimpleClass` konwertuje obiekt na jego reprezentację ciągu, zwraca w pełni kwalifikowaną nazwę typu. W takim przypadku `ToString` metoda zwraca ciąg "SimpleClass".

- Trzy metody, które testują równość `Equals(Object)` dwóch obiektów: metodę `Equals(Object, Object)` wystąpienia publicznego, `ReferenceEquals(Object, Object)` publiczną metodę statyczną i publiczną metodę statyczną. Domyślnie te metody testują równość odniesienia; oznacza to, że aby być równe, dwie zmienne obiektu muszą odwoływać się do tego samego obiektu.

- Metoda `GetHashCode` publiczna, która oblicza wartość, która umożliwia wystąpienie typu, które mają być używane w kolekcjach mieszanych.

- Metoda `GetType` publiczna, która <xref:System.Type> zwraca obiekt, który reprezentuje `SimpleClass` typ.

- Metoda chroniona, <xref:System.Object.Finalize%2A> która jest przeznaczona do zwalniania zasobów niezarządzanych, zanim pamięć obiektu zostanie odzyskana przez moduł zbierający elementy bezużyteczne.

- Metoda chroniona, <xref:System.Object.MemberwiseClone%2A> która tworzy płytki klon bieżącego obiektu.

Z powodu niejawnego dziedziczenia można `SimpleClass` wywołać dowolny odziedziczony element członkowski `SimpleClass` z obiektu tak, jakby był faktycznie członkiem zdefiniowanym w klasie. Na przykład w poniższym `SimpleClass.ToString` przykładzie `SimpleClass` wywołuje <xref:System.Object>metodę, która dziedziczy po .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

W poniższej tabeli wymieniono kategorie typów, które można utworzyć w języku C# i typy, z których niejawnie dziedziczą. Każdy typ podstawowy sprawia, że inny zestaw elementów członkowskich dostępnych za pośrednictwem dziedziczenia do niejawnie pochodnych typów.

| Kategoria typu | Niejawnie dziedziczy po                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| class         | <xref:System.Object>                                                          |
| struktura         | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| delegate      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dziedziczenie i relacja "jest"

Zwykle dziedziczenie jest używane do wyrażania relacji "jest" między klasą podstawową a jedną lub kilkoma klasami pochodnymi, gdzie klasy pochodne są wyspecjalizowanymi wersjami klasy podstawowej; klasa pochodna jest typem klasy podstawowej. Na przykład `Publication` klasa reprezentuje publikację dowolnego rodzaju, a `Book` i `Magazine` klasy reprezentują określone typy publikacji.

> [!NOTE]
> Klasa lub struktura można zaimplementować jeden lub więcej interfejsów. Chociaż implementacja interfejsu jest często przedstawiana jako obejście pojedynczego dziedziczenia lub jako sposób używania dziedziczenia za pomocą struktur, ma na celu wyrażenie innej relacji (relacji "może zrobić") między interfejsem a jego typem implementacmentu niż Dziedziczenia. Interfejs definiuje podzbiór funkcji (takich jak możliwość testowania równości, do porównywania lub sortowania obiektów lub do obsługi analizowania i formatowania zależne od kultury), które interfejs udostępnia do jego typów implementujących.

Należy zauważyć, że "jest" wyraża również relację między typem a określonym wystąpieniem tego typu. W poniższym `Automobile` przykładzie jest klasą, która ma `Make`trzy unikatowe właściwości tylko do odczytu: , producenta samochodu; `Model`, rodzaj samochodu; i `Year`, jego rok produkcji. Klasa `Automobile` ma również konstruktora, którego argumenty są przypisane do <xref:System.Object.ToString%2A?displayProperty=nameWithType> wartości właściwości i zastępuje metodę tworzenia `Automobile` ciągu, `Automobile` który jednoznacznie identyfikuje wystąpienie, a nie klasy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

W takim przypadku nie należy polegać na dziedziczeniu do reprezentowania określonych samochodów sprawia i modeli. Na przykład nie trzeba definiować `Packard` typu reprezentującego samochody produkowane przez Firmę Samochodów Packard. Zamiast tego można je reprezentować, `Automobile` tworząc obiekt z odpowiednimi wartościami przekazanymi do konstruktora klasy, tak jak w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Relacja is-a oparta na dziedziczeniu jest najlepiej stosowana do klasy podstawowej i klas pochodnych, które dodają dodatkowe elementy członkowskie do klasy podstawowej lub które wymagają dodatkowych funkcji, które nie są obecne w klasie podstawowej.

## <a name="designing-the-base-class-and-derived-classes"></a>Projektowanie klasy podstawowej i klas pochodnych

Przyjrzyjmy się procesowi projektowania klasy podstawowej i jej klas pochodnych. W tej sekcji zdefiniujesz klasę `Publication`podstawową, która reprezentuje wszelkiego rodzaju publikację, taką jak książka, czasopismo, gazeta, czasopismo, artykuł itp. Zdefiniujesz również `Book` klasę, która `Publication`wywodzi się z . Przykład można łatwo rozszerzyć, aby zdefiniować inne `Magazine` `Journal`klasy `Newspaper`pochodne, takie jak , , i `Article`.

### <a name="the-base-publication-class"></a>Podstawowa klasa Publikacja

Projektując swoją `Publication` klasę, musisz podjąć kilka decyzji projektowych:

- Jakie elementy członkowskie do `Publication` uwzględnienia w `Publication` klasie podstawowej i `Publication` czy członkowie zapewniają implementacje metody lub czy jest abstrakcyjną klasą podstawową, która służy jako szablon dla klas pochodnych.

  W takim przypadku `Publication` klasa zapewni implementacje metody. [Projektowanie abstrakcyjnych klas podstawowych i ich klas pochodnych](#abstract) sekcja zawiera przykład, który używa abstrakcyjnej klasy podstawowej do definiowania metod, które klasy pochodne muszą zastąpić. Klasy pochodne są wolne do zapewnienia dowolnej implementacji, która jest odpowiednia dla typu pochodnego.

  Możliwość ponownego użycia kodu (oznacza to, że wiele klas pochodnych współużytkuje deklarację i implementację metod klasy podstawowej i nie trzeba ich zastępować) jest zaletą nieabstrakcyjnych klas podstawowych. W związku z tym `Publication` należy dodać członków, jeśli ich kod `Publication` może być współużytkowany przez niektóre lub najbardziej wyspecjalizowane typy. Jeśli nie uda się zapewnić implementacji klasy podstawowej skutecznie, skończysz z koniecznością zapewnienia implementacji w dużej mierze identyczne element członkowski w klasach pochodnych, a pojedyncza implementacja w klasie podstawowej. Konieczność obsługi zduplikowanego kodu w wielu lokalizacjach jest potencjalnym źródłem błędów.

  Zarówno w celu zmaksymalizowania ponownego użycia kodu i utworzenia logicznej i intuicyjnej hierarchii dziedziczenia, należy mieć pewność, że w `Publication` klasie uwzględnisz tylko dane i funkcje, które są wspólne dla wszystkich lub większości publikacji. Klasy pochodne następnie implementują elementy członkowskie, które są unikatowe dla określonych rodzajów publikacji, które reprezentują.

- Jak daleko rozszerzyć hierarchię klas. Czy chcesz opracować hierarchię trzech lub więcej klas, a nie tylko klasę podstawową i jedną lub więcej klas pochodnych? Na przykład `Publication` może być klasą podstawową , która `Periodical`z kolei jest klasą podstawową `Magazine`, `Journal` i `Newspaper`.

  W przykładzie użyjesz małej hierarchii `Publication` klasy i pojedynczej klasy `Book`pochodnej. Można łatwo rozszerzyć przykład, aby utworzyć szereg dodatkowych `Publication`klas, `Magazine` które `Article`wynikają z , takich jak i .

- Czy ma sens tworzenie wystąpienia klasy podstawowej. Jeśli tak nie jest, należy zastosować [abstrakcyjne](../language-reference/keywords/abstract.md) słowo kluczowe do klasy. W przeciwnym `Publication` razie można utworzyć wystąpienia klasy, wywołując jego konstruktora klasy. Jeśli zostanie podjęta próba wystąpienia klasy `abstract` oznaczonej słowem kluczowym przez bezpośrednie wywołanie konstruktora klasy, kompilator języka C# generuje błąd CS0144, "Nie można utworzyć wystąpienia klasy abstrakcyjnej lub interfejsu". Jeśli zostanie podjęta próba wystąpienia klasy przy użyciu odbicia, metoda <xref:System.MemberAccessException>odbicia rzuca .

  Domyślnie można utworzyć wystąpienie klasy podstawowej, wywołując jego konstruktora klas. Nie trzeba jawnie definiować konstruktora klasy. Jeśli jeden nie jest obecny w kodzie źródłowym klasy podstawowej, kompilator Języka C# automatycznie zapewnia domyślny (bez parametrów) konstruktora.

  W przykładzie zaznaczysz `Publication` klasę jako [abstrakcyjną,](../language-reference/keywords/abstract.md) aby nie można było utworzyć wystąpienia.  Klasa `abstract` bez `abstract` żadnych metod wskazuje, że ta klasa reprezentuje abstrakcyjną koncepcję, która jest współużytkowana przez kilka konkretnych klas (takich jak `Book`, `Journal`).

- Czy klasy pochodne muszą dziedziczyć implementacji klasy podstawowej określonych elementów członkowskich, czy mają możliwość zastąpienia implementacji klasy podstawowej lub czy muszą zapewnić implementację. Użycie [abstrakcyjnego](../language-reference/keywords/abstract.md) słowa kluczowego, aby wymusić klasy pochodne, aby zapewnić implementację. Wirtualne [virtual](../language-reference/keywords/virtual.md) słowo kluczowe służy do zezwalania klas pochodnych zastąpić metody klasy podstawowej. Domyślnie metody zdefiniowane w klasie podstawowej *nie* są nadpisywalne.

 Klasa `Publication` nie ma `abstract` żadnych metod, ale `abstract`sama klasa jest .

- Czy klasa pochodna reprezentuje klasę końcową w hierarchii dziedziczenia i nie może sama być używana jako klasa podstawowa dla dodatkowych klas pochodnych. Domyślnie każda klasa może służyć jako klasa podstawowa. [Zapieczętowane](../language-reference/keywords/sealed.md) słowo kluczowe można zastosować, aby wskazać, że klasa nie może służyć jako klasa podstawowa dla żadnych dodatkowych klas. Próba wyprowadzenia z zapieczętowanego błędu kompilatora wygenerowanego \<klasy CS0509 ,,nie może pochodzić z zapieczętowanego typu typeName>".

  W twoim przykładzie oznaczysz klasę `sealed`pochodną jako .

Poniższy przykład przedstawia kod `Publication` źródłowy dla klasy, a także wyliczenie, `PublicationType` które jest zwracane przez `Publication.PublicationType` właściwość. Oprócz elementów członkowskich, które <xref:System.Object>dziedziczy `Publication` z , klasa definiuje następujące unikatowe elementy członkowskie i elementy członkowskie zastępuje:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Ponieważ `Publication` klasa `abstract`jest , nie można utworzyć wystąpienia bezpośrednio z kodu, jak w poniższym przykładzie:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Jednak jego konstruktora wystąpienia można wywołać bezpośrednio z konstruktorów `Book` klas pochodnych, jak pokazuje kod źródłowy dla klasy.

- Dwie właściwości związane z publikacją

  `Title`jest właściwością <xref:System.String> tylko do odczytu, `Publication` której wartość jest dostarczana przez wywołanie konstruktora.

  `Pages`jest właściwością <xref:System.Int32> odczytu i zapisu, która wskazuje, ile wszystkich stron ma publikacja. Wartość jest przechowywana w `totalPages`prywatnym polu o nazwie . Musi to być liczba <xref:System.ArgumentOutOfRangeException> dodatnia lub jest wyrzucana.

- Członkowie związani z wydawcą

  Dwie właściwości tylko do `Publisher` `Type`odczytu i . Wartości są pierwotnie dostarczane przez wywołanie do konstruktora `Publication` klasy.

- Członkowie związani z publikowaniem

  Dwie metody `Publish` `GetPublicationDate`i , ustawić i zwrócić datę publikacji. Metoda `Publish` ustawia prywatną `published` `true` flagę, gdy jest wywoływana i przypisuje datę przekazywaną do niej jako argument do pola prywatnego. `datePublished` Metoda `GetPublicationDate` zwraca ciąg "NYP", `published` jeśli `false`flaga jest , `datePublished` a wartość `true`pola, jeśli jest .

- Członkowie związani z prawami autorskimi

  Metoda `Copyright` przyjmuje nazwę posiadacza praw autorskich i rok praw autorskich jako `CopyrightName` argumenty `CopyrightDate` i przypisuje je do i właściwości.

- Zastąpienie `ToString` metody

  Jeśli typ nie zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, zwraca w pełni kwalifikowaną nazwę typu, który ma niewielkie zastosowanie w odróżnianiu jednego wystąpienia od innego. Klasa `Publication` zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> zwracać wartość `Title` właściwości.

Poniższy rysunek ilustruje `Publication` relację między klasą <xref:System.Object> podstawową a jej niejawnie dziedziczoną klasą.

![Klasa Obiekt i publikacja](media/publication-class.jpg)

### <a name="the-book-class"></a>Klasa `Book`

Klasa `Book` reprezentuje książkę jako wyspecjalizowany typ publikacji. Poniższy przykład pokazuje kod `Book` źródłowy dla klasy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Oprócz elementów członkowskich, które `Publication`dziedziczy `Book` z , klasa definiuje następujące unikatowe elementy członkowskie i elementy członkowskie zastępuje:

- Dwa konstruktory

  Dwa `Book` konstruktory mają trzy wspólne parametry. Dwa, *tytuł* i *wydawca*, `Publication` odpowiadają parametrom konstruktora. Trzeci to *autor*, który jest przechowywany `Author` w publicznej właściwości niezmienne. Jeden konstruktor zawiera parametr *isbn,* `ISBN` który jest przechowywany we właściwości auto.

  Pierwszy konstruktor używa [tego](../language-reference/keywords/this.md) słowa kluczowego, aby wywołać inny konstruktora. Tworzenie łańcucha konstruktora jest typowym wzorcem w definiowaniu konstruktorów. Konstruktory z mniejszą liczbą parametrów zapewniają wartości domyślne podczas wywoływania konstruktora z największą liczbą parametrów.

  Drugi konstruktor używa podstawowego słowa [kluczowego,](../language-reference/keywords/base.md) aby przekazać nazwę tytułu i wydawcy do konstruktora klasy podstawowej. Jeśli nie dokonać jawnego wywołania konstruktora klasy podstawowej w kodzie źródłowym, kompilator Języka C# automatycznie dostarcza wywołanie domyślnego lub bez parametrowego konstruktora klasy podstawowej.

- Właściwość tylko `ISBN` do odczytu, `Book` która zwraca międzynarodowy standardowy numer książki obiektu, unikatowy numer 10- lub 13-cyfrowy. Numer ISBN jest dostarczany jako argument `Book` do jednego z konstruktorów. Numer ISBN jest przechowywany w prywatnym polu zapasowym, które jest generowane automatycznie przez kompilator.

- Właściwość tylko `Author` do odczytu. Nazwa autora jest dostarczana `Book` jako argument do obu konstruktorów i jest przechowywana we właściwości.

- Dwie właściwości związane tylko z `Price` ceną do odczytu i `Currency`. Ich wartości są dostarczane `SetPrice` jako argumenty w wywołaniu metody. Właściwość `Currency` jest trzycyfrowym symbolem waluty ISO (na przykład USD dla dolara amerykańskiego). Symbole waluty ISO można pobrać <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> z właściwości. Obie te właściwości są tylko do odczytu zewnętrznie, ale `Book` oba mogą być ustawione przez kod w klasie.

- Metoda, `SetPrice` która ustawia wartości `Price` i `Currency` właściwości. Te wartości są zwracane przez te same właściwości.

- `ToString` Zastępuje metodę (dziedziczoną z `Publication`) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> oraz <xref:System.Object.GetHashCode%2A> metody i <xref:System.Object>metody (dziedziczone po ).

  Chyba że jest zastępowane, testy <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody równości odwołania. Oznacza to, że dwie zmienne obiektu są uważane za równe, jeśli odnoszą się do tego samego obiektu. W `Book` klasie, z drugiej strony, dwa `Book` obiekty powinny być równe, jeśli mają ten sam numer ISBN.

  Po zastąpieniu <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody, należy również zastąpić <xref:System.Object.GetHashCode%2A> metodę, która zwraca wartość, która używa środowiska wykonawczego do przechowywania elementów w kolekcji mieszania dla skutecznego pobierania. Kod mieszania powinien zwracać wartość, która jest zgodna z testem równości. Ponieważ <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> zostały zastąpione do `true` zwrócenia, jeśli właściwości ISBN dwóch `Book` obiektów są równe, zwracasz kod <xref:System.String.GetHashCode%2A> skrótu obliczony `ISBN` przez wywołanie metody ciągu zwróconego przez właściwość.

Poniższy rysunek ilustruje `Book` relację między klasą i `Publication`, jej klasą podstawową.

![Klasy publikacji i książek](media/book-class.jpg)

Teraz można utworzyć wystąpienie `Book` obiektu, wywołać zarówno jego unikatowe i dziedziczone elementy członkowskie i przekazać `Publication` go jako `Book`argument do metody, która oczekuje parametru typu lub typu, jak pokazano w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Projektowanie abstrakcyjnych klas podstawowych i ich klas pochodnych
<a name="abstract"></a>

W poprzednim przykładzie zdefiniowano klasę podstawową, która dostarczyła implementację dla wielu metod, aby umożliwić klasom pochodnym udostępnianie kodu. W wielu przypadkach jednak klasa podstawowa nie oczekuje się implementacji. Zamiast tego klasa podstawowa jest *klasą abstrakcyjną,* która deklaruje *metody abstrakcyjne;* służy jako szablon, który definiuje elementy członkowskie, które każda klasa pochodna musi zaimplementować. Zazwyczaj w abstrakcyjnej klasie podstawowej implementacja każdego typu pochodnego jest unikatowa dla tego typu. Oznaczone klasy z abstrakcyjne słowa kluczowego, ponieważ nie `Publication` ma sensu do tworzenia wystąpienia obiektu, chociaż klasa nie zapewniają implementacji funkcji wspólnych dla publikacji.

Na przykład każdy zamknięty dwuwymiarowy kształt geometryczny zawiera dwie właściwości: obszar, wewnętrzny zasięg kształtu; i obwodu lub odległości wzdłuż krawędzi kształtu. Sposób obliczania tych właściwości zależy jednak całkowicie od konkretnego kształtu. Wzór do obliczania obwodu (lub obwodu) okręgu, na przykład, różni się od trójkąta. Klasa `Shape` jest `abstract` klasą `abstract` z metodami. Oznacza to, że klasy pochodne współużytkują te same funkcje, ale te klasy pochodne implementują tę funkcjonalność inaczej.

Poniższy przykład definiuje abstrakcyjną `Shape` klasę podstawową o `Area` nazwie, która definiuje dwie właściwości: i `Perimeter`. Oprócz oznaczania klasy słowem kluczowym [abstrakcyjnym,](../language-reference/keywords/abstract.md) każdy element członkowski wystąpienia jest również oznaczony [abstrakcyjnym](../language-reference/keywords/abstract.md) słowem kluczowym. W takim `Shape` przypadku również zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę zwracania nazwy typu, a nie jego w pełni kwalifikowaną nazwę. I definiuje dwa statyczne `GetArea` elementy `GetPerimeter`członkowskie i , które umożliwiają wywołującym łatwo pobrać obszar i obwód wystąpienia dowolnej klasy pochodnej. Po przełknięciu wystąpienia klasy pochodnej do jednej z tych metod środowisko uruchomieniowe wywołuje zastąpienie metody klasy pochodnej.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Następnie można wyprowadzić niektóre `Shape` klasy z tych reprezentują określone kształty. Poniższy przykład definiuje trzy `Triangle` `Rectangle`klasy, `Circle`, i . Każdy używa formuły unikatowej dla tego konkretnego kształtu do obliczenia obszaru i obwodu. Niektóre klasy pochodne również zdefiniować właściwości, takie jak `Rectangle.Diagonal` i `Circle.Diameter`, które są unikatowe dla kształtu, który reprezentują.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

W poniższym przykładzie użyto obiektów pochodzących z `Shape`programu . Wywołuje tablicę obiektów pochodzących z `Shape` i wywołuje metody statyczne `Shape` klasy, która `Shape` zawija zwraca wartości właściwości. Środowisko wykonawcze pobiera wartości z nadpisanych właściwości typów pochodnych. W przykładzie rzutuje również każdy `Shape` obiekt w tablicy na jego typ pochodny i, jeśli `Shape`rzutowania powiedzie się, pobiera właściwości tej konkretnej podklasy .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Zobacz też

- [Klasy i obiekty](../tour-of-csharp/classes-and-objects.md)
- [Dziedziczenie (Przewodnik programowania w języku C#)](../programming-guide/classes-and-structs/inheritance.md)
