---
title: 'Dziedziczenie w języku C #'
description: Dowiedz się, jak używać dziedziczenia w bibliotekach i aplikacjach C#.
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 8e24ad3e93dcd11f39ae979a3acda4c4ada13dc5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007731"
---
# <a name="inheritance-in-c-and-net"></a>Dziedziczenie w języku C# i .NET

Ten samouczek przedstawia sposób dziedziczenia w języku C#. Dziedziczenie to funkcja języków programowania zorientowanego obiektowo, która umożliwia zdefiniowanie klasy bazowej, która zapewnia konkretne funkcje (dane i zachowanie) i definiuje klasy pochodne, które dziedziczą lub przesłaniają te funkcje.

## <a name="prerequisites"></a>Wymagania wstępne

W tym samouczku założono, że zainstalowano zestaw .NET Core SDK. Odwiedź stronę [pobierania programu .NET Core](https://dotnet.microsoft.com/download) , aby ją pobrać. Potrzebny jest również Edytor kodu. W tym samouczku użyto [Visual Studio Code](https://code.visualstudio.com), chociaż można użyć dowolnego dowolnego edytora kodu.

## <a name="running-the-examples"></a>Uruchamianie przykładów

Aby utworzyć i uruchomić przykłady w tym samouczku, użyj narzędzia [dotnet](../../core/tools/dotnet.md) z wiersza polecenia. Wykonaj następujące czynności na każdym z przykładów:

1. Utwórz katalog do przechowywania przykładu.
1. Wprowadź [nową konsolę programu dotnet](../../core/tools/dotnet-new.md) w wierszu polecenia, aby utworzyć nowy projekt .NET Core.
1. Skopiuj i wklej kod z przykładu do edytora kodu.
1. Wprowadź [dotnet Restore](../../core/tools/dotnet-restore.md) polecenie w wierszu polecenia, aby załadować lub przywrócić zależności projektu.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Wprowadź polecenie [Uruchom jako dotnet](../../core/tools/dotnet-run.md) , aby skompilować i uruchomić przykład.

## <a name="background-what-is-inheritance"></a>Tło: co to jest dziedziczenie?

*Dziedziczenie* jest jednym z podstawowych atrybutów programowania zorientowanego obiektowo. Umożliwia zdefiniowanie klasy podrzędnej, która ponownie używa (dziedziczy), rozszerza lub modyfikuje zachowanie klasy nadrzędnej. Klasa, której członkowie są dziedziczone jest nazywana *klasą bazową*. Klasa, która dziedziczy elementy członkowskie klasy bazowej, nosi nazwę *klasy pochodnej*.

Języki C# i .NET obsługują tylko *pojedyncze dziedziczenie* . Oznacza to, że Klasa może dziedziczyć tylko z pojedynczej klasy. Dziedziczenie jest jednak przechodnie, co pozwala na zdefiniowanie hierarchii dziedziczenia dla zestawu typów. Innymi słowy, typ `D` może dziedziczyć po typie `C` , który dziedziczy z typu `B` , który dziedziczy z typu klasy bazowej `A` . Ponieważ dziedziczenie jest przechodnie, elementy członkowskie typu `A` są dostępne do typu `D` .

Nie wszystkie składowe klasy bazowej są dziedziczone przez klasy pochodne. Następujące elementy członkowskie nie są dziedziczone:

- [Konstruktory statyczne](../programming-guide/classes-and-structs/static-constructors.md), które inicjują statyczne dane klasy.

- [Konstruktory wystąpień](../programming-guide/classes-and-structs/constructors.md), które są wywoływane w celu utworzenia nowego wystąpienia klasy. Każda klasa musi definiować własne konstruktory.

- [Finalizatory](../programming-guide/classes-and-structs/destructors.md), które są wywoływane przez moduł wyrzucania elementów bezużytecznych środowiska uruchomieniowego, aby zniszczyć wystąpienia klasy.

Wszystkie inne elementy członkowskie klasy bazowej są dziedziczone przez klasy pochodne, niezależnie od tego, czy są one widoczne, czy nie są zależne od ich dostępności. Dostępność elementu członkowskiego ma wpływ na widoczność klas pochodnych w następujący sposób:

- [Prywatne](../language-reference/keywords/private.md) składowe są widoczne tylko w klasach pochodnych, które są zagnieżdżone w klasie podstawowej. W przeciwnym razie nie są one widoczne w klasach pochodnych. W poniższym przykładzie `A.B` jest klasą zagnieżdżoną, która pochodzi od `A` , i `C` pochodzi od `A` . Pole prywatne `A.value` jest widoczne w A.B. Jeśli jednak usuniesz Komentarze z `C.GetValue` metody i spróbujemy skompilować przykład, generuje błąd kompilatora CS0122: "A. Value" jest niedostępny z powodu swojego poziomu ochrony ".

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chronione](../language-reference/keywords/protected.md) elementy członkowskie są widoczne tylko w klasach pochodnych.

- [Wewnętrzne](../language-reference/keywords/internal.md) elementy członkowskie są widoczne tylko w klasach pochodnych, które znajdują się w tym samym zestawie, co Klasa bazowa. Nie są one widoczne w klasach pochodnych znajdujących się w innym zestawie z klasy podstawowej.

- [Publiczne](../language-reference/keywords/public.md) składowe są widoczne w klasach pochodnych i są częścią interfejsu publicznego klasy pochodnej. Publiczne dziedziczone elementy członkowskie mogą być wywoływane tak, jakby są zdefiniowane w klasie pochodnej. W poniższym przykładzie Klasa `A` definiuje metodę o nazwie `Method1` , a Klasa `B` dziedziczy z klasy `A` . Przykład następnie wywołuje `Method1` , jakby była metodą wystąpienia `B` .

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Klasy pochodne mogą również *przesłaniać* dziedziczone elementy członkowskie, dostarczając alternatywną implementację. Aby możliwe było przesłonięcie elementu członkowskiego, element członkowski w klasie bazowej musi być oznaczony za pomocą słowa kluczowego [Virtual](../language-reference/keywords/virtual.md) . Domyślnie elementy członkowskie klasy bazowej nie są oznaczone jako `virtual` i nie można ich zastąpić. Próba zastąpienia niewirtualnego elementu członkowskiego, jak pokazano w poniższym przykładzie, generuje błąd kompilatora CS0506: " \<member> nie można przesłonić dziedziczonej składowej, \<member> ponieważ nie jest oznaczona jako wirtualna, abstrakcyjna lub przesłonięcie.

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

W niektórych przypadkach Klasa pochodna *musi* przesłonić implementację klasy bazowej. Elementy członkowskie klasy bazowej oznaczone za pomocą słowa kluczowego [abstract](../language-reference/keywords/abstract.md) wymagają, aby klasy pochodne zostały przez nie zastąpione. Próba skompilowania poniższego przykładu generuje błąd kompilatora CS0534, " &lt; Klasa nie &gt; implementuje dziedziczonej abstrakcyjnej &lt; składowej składowej &gt; ", ponieważ Klasa nie `B` zapewnia implementacji dla `A.Method1` .

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

Dziedziczenie ma zastosowanie tylko do klas i interfejsów. Inne kategorie typów (struktury, Delegaty i wyliczenia) nie obsługują dziedziczenia. Ze względu na te reguły Próba skompilowania kodu, takiego jak Poniższy przykład, powoduje wystąpienie błędu kompilatora CS0527: "typ" ValueType "na liście interfejsów nie jest interfejsem". Komunikat o błędzie wskazuje, że chociaż można zdefiniować interfejsy, które implementuje struktura, dziedziczenie nie jest obsługiwane.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Dziedziczenie niejawne

Oprócz typów, które mogą dziedziczyć za pośrednictwem pojedynczego dziedziczenia, wszystkie typy w systemie typu .NET niejawnie dziedziczą z <xref:System.Object> lub typu pochodnego. Typowe funkcje programu <xref:System.Object> są dostępne dla dowolnego typu.

Aby zobaczyć, co oznacza niejawne dziedziczenie, zdefiniujmy nową klasę, `SimpleClass` która jest po prostu pustą definicją klasy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Następnie można użyć odbicia, które umożliwia sprawdzenie metadanych typu w celu uzyskania informacji na temat tego typu, aby uzyskać listę elementów członkowskich należących do `SimpleClass` typu. Chociaż nie zdefiniowano żadnych elementów członkowskich w `SimpleClass` klasie, dane wyjściowe z przykładu wskazują, że faktycznie ma dziewięć członków. Jeden z tych elementów członkowskich jest konstruktorem bez parametrów (lub domyślnym), który jest automatycznie dostarczany dla `SimpleClass` typu przez kompilator języka C#. Pozostałe osiem są członkami <xref:System.Object> , typu, z którego wszystkie klasy i interfejsy w systemie typu .NET ostatecznie dziedziczą.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Niejawne dziedziczenie z <xref:System.Object> klasy sprawia, że te metody są dostępne dla `SimpleClass` klasy:

- Metoda publiczna `ToString` , która konwertuje `SimpleClass` obiekt na jego reprezentację w postaci ciągu, zwraca w pełni kwalifikowaną nazwę typu. W tym przypadku `ToString` Metoda zwraca ciąg "SimpleClass".

- Trzy metody, które testują pod kątem równości dwóch obiektów: publiczna `Equals(Object)` metoda wystąpienia, publiczna metoda statyczna `Equals(Object, Object)` i publiczna metoda statyczna `ReferenceEquals(Object, Object)` . Domyślnie te metody testują równość odniesienia; oznacza to, że jest równe, dwie zmienne obiektów muszą odwoływać się do tego samego obiektu.

- Metoda publiczna `GetHashCode` , która oblicza wartość umożliwiającą wystąpienie typu, który ma być używany w kolekcjach skrótów.

- Metoda publiczna `GetType` , która zwraca <xref:System.Type> obiekt, który reprezentuje `SimpleClass` Typ.

- Metoda chroniona <xref:System.Object.Finalize%2A> , która została zaprojektowana w celu zwolnienia zasobów niezarządzanych przed odjęciem pamięci obiektu przez moduł wyrzucania elementów bezużytecznych.

- Metoda chroniona <xref:System.Object.MemberwiseClone%2A> , która tworzy płytki klonowania bieżącego obiektu.

Ze względu na niejawne dziedziczenie można wywołać dowolny Dziedziczony element członkowski z `SimpleClass` obiektu, tak jakby był to element członkowski zdefiniowany w `SimpleClass` klasie. Na przykład poniższy przykład wywołuje `SimpleClass.ToString` metodę, która `SimpleClass` dziedziczy z <xref:System.Object> .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

W poniższej tabeli wymieniono kategorie typów, które można utworzyć w języku C#, oraz typy, z których dziedziczą niejawnie. Każdy typ podstawowy udostępnia inny zestaw elementów członkowskich za pomocą dziedziczenia do niejawnie pochodnych typów.

| Kategoria typu | Niejawnie dziedziczone z                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| class         | <xref:System.Object>                                                          |
| struktura        | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| delegate      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dziedziczenie i relacja "is"

Zwykle dziedziczenie jest stosowane do wyrażenia "is" relacji między klasą bazową i co najmniej jedną klasą pochodną, gdzie klasy pochodne są wyspecjalizowanymi wersjami klasy bazowej; Klasa pochodna jest typem klasy bazowej. Na przykład `Publication` Klasa reprezentuje publikację dowolnego rodzaju, a `Book` `Magazine` klasy i reprezentują określone typy publikacji.

> [!NOTE]
> Klasa lub struktura może zaimplementować jeden lub więcej interfejsów. Podczas gdy implementacja interfejsu jest często prezentowana jako obejście dla pojedynczego dziedziczenia lub jako sposób używania dziedziczenia z strukturami, należy przedstawić inną relację (relację "może") między interfejsem i jego typem implementującym niż dziedziczenie. Interfejs definiuje podzestaw funkcji (takich jak możliwość testowania równości, porównywania lub sortowania obiektów lub do obsługi analizy zależnej od kultury i formatowania), które Interfejs udostępnia dla jego typów implementujących.

Należy zauważyć, że "is" także wskazuje relację między typem i określonym wystąpieniem tego typu. W poniższym przykładzie `Automobile` jest klasą, która ma trzy unikatowe właściwości tylko do odczytu: `Make` , producent urządzenia przenośnego `Model` , rodzaj samochodów, a `Year` rok produkcji. `Automobile`Klasa ma także konstruktora, którego argumenty są przypisane do wartości właściwości, i zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, aby utworzyć ciąg, który jednoznacznie identyfikuje `Automobile` wystąpienie, a nie `Automobile` klasę.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

W takim przypadku nie należy polegać na dziedziczeniu do reprezentowania określonych samochodów i modeli. Nie trzeba na przykład definiować `Packard` typu do reprezentowania samochodów, które są wytwarzane przez firmę Packard Motor samochodowa. Zamiast tego można je przedstawić, tworząc `Automobile` obiekt z odpowiednimi wartościami przekazaną do jego konstruktora klasy, jak pokazano w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Jest to relacja oparta na dziedziczeniu najlepiej zastosowana do klasy bazowej i do klas pochodnych, które dodają do klasy podstawowej dodatkowe elementy członkowskie lub które wymagają dodatkowych funkcji nieobecnych w klasie podstawowej.

## <a name="designing-the-base-class-and-derived-classes"></a>Projektowanie klasy bazowej i klas pochodnych

Przyjrzyjmy się procesowi projektowania klasy bazowej i jej klas pochodnych. W tej sekcji zdefiniujesz klasę bazową, `Publication` która reprezentuje publikację dowolnego rodzaju, na przykład książkę, czasopismo, gazetę, arkusz, artykuł itd. Zdefiniujesz również `Book` klasę, która pochodzi od `Publication` . Można łatwo zwiększyć przykład, aby zdefiniować inne klasy pochodne, takie jak `Magazine` ,, `Journal` `Newspaper` , i `Article` .

### <a name="the-base-publication-class"></a>Klasa publikacji podstawowej

Podczas projektowania `Publication` klasy należy podjąć pewne decyzje dotyczące projektowania:

- Elementy członkowskie, które mają zostać uwzględnione w `Publication` klasie bazowej, oraz informacje o tym, czy `Publication` składowe udostępniają implementacje metod, czy też `Publication` jest abstrakcyjną klasą bazową, która służy jako szablon klas pochodnych.

  W takim przypadku Klasa zapewni `Publication` implementacje metod. [Projektowanie abstrakcyjnych klas podstawowych i ich klas pochodnych](#abstract) zawiera przykład, który używa abstrakcyjnej klasy bazowej do definiowania metod, które muszą zostać przesłonięte przez klasy pochodne. Klasy pochodne są bezpłatne, aby zapewnić implementację, która jest odpowiednia dla typu pochodnego.

  Możliwość ponownego użycia kodu (oznacza to, że wiele klas pochodnych korzysta z deklaracji i implementacji metod klasy bazowej i nie trzeba ich przesłonić) jest zaletą nieabstrakcyjnych klas podstawowych. W związku z tym należy dodać członków do, `Publication` jeśli ich kod może być współużytkowany przez niektóre lub większość wyspecjalizowanych `Publication` typów. Jeśli nie podasz wydajnych implementacji klas podstawowych, będziesz mieć możliwość zapewnienia większości identycznych implementacji elementów członkowskich w klasach pochodnych, a nie pojedynczej implementacji w klasie bazowej. Konieczność utrzymania duplikatu kodu w wielu lokalizacjach jest potencjalnym źródłem błędów.

  Aby zmaksymalizować użycie kodu i utworzyć logiczną i intuicyjną hierarchię dziedziczenia, należy się upewnić, że należy uwzględnić w `Publication` klasie tylko dane i funkcje wspólne dla wszystkich lub większości publikacji. Klasy pochodne następnie implementują elementy członkowskie, które są unikatowe dla określonych rodzajów publikacji, które reprezentują.

- Jak daleko, aby zwiększyć hierarchię klas. Czy chcesz opracować hierarchię trzech lub więcej klas, a nie po prostu klasy bazowej i co najmniej jednej klasy pochodnej? Na przykład `Publication` może być klasą bazową `Periodical` , która z kolei jest klasą bazową `Magazine` , `Journal` i `Newspaper` .

  Przykładowo będziesz używać małej hierarchii `Publication` klasy i pojedynczej klasy pochodnej `Book` . Można łatwo zwiększyć przykład, aby utworzyć szereg dodatkowych klas, które pochodzą z `Publication` , takich jak `Magazine` i `Article` .

- Określa, czy warto utworzyć wystąpienie klasy bazowej. Jeśli tak nie jest, należy zastosować [abstrakcyjne](../language-reference/keywords/abstract.md) słowo kluczowe do klasy. W przeciwnym razie `Publication` można utworzyć wystąpienie klasy, wywołując jej Konstruktor klas. Jeśli zostanie podjęta próba utworzenia wystąpienia klasy oznaczonej za pomocą `abstract` słowa kluczowego przez bezpośrednie wywołanie konstruktora klasy, kompilator języka C# generuje błąd CS0144, "nie można utworzyć wystąpienia klasy abstrakcyjnej lub interfejsu". Jeśli zostanie podjęta próba utworzenia wystąpienia klasy przy użyciu odbicia, Metoda odbicia zgłasza <xref:System.MemberAccessException> .

  Domyślnie można utworzyć wystąpienie klasy bazowej, wywołując jej Konstruktor klas. Nie musisz jawnie definiować konstruktora klasy. Jeśli nie występuje w kodzie źródłowym klasy podstawowej, kompilator języka C# automatycznie udostępnia domyślny Konstruktor (bez parametrów).

  Przykładowo oznaczmy `Publication` klasę jako [abstrakcyjną](../language-reference/keywords/abstract.md) , aby nie można było utworzyć wystąpienia.  `abstract`Klasa bez żadnych `abstract` metod wskazuje, że ta klasa reprezentuje abstrakcyjną koncepcję, która jest współużytkowana przez kilka klas konkretnych (takich jak `Book` , `Journal` ).

- Bez względu na to, czy klasy pochodne muszą dziedziczyć implementację klasy bazowej określonych elementów członkowskich, czy mają opcję przesłaniania implementacji klasy bazowej, czy też muszą dostarczyć implementację. Aby wymusić implementację klas pochodnych, należy użyć słowa kluczowego [abstract](../language-reference/keywords/abstract.md) . Możesz użyć słowa kluczowego [Virtual](../language-reference/keywords/virtual.md) , aby umożliwić klasom pochodnym przesłonięcie metody klasy bazowej. Domyślnie metody zdefiniowane w klasie bazowej *nie* są możliwe do zastąpienia.

  `Publication`Klasa nie ma żadnych `abstract` metod, ale sama klasa to `abstract` .

- Czy Klasa pochodna reprezentuje ostateczną klasę w hierarchii dziedziczenia i nie może być używana jako klasa bazowa dla dodatkowych klas pochodnych. Domyślnie każda klasa może być klasą bazową. Można zastosować [zapieczętowane](../language-reference/keywords/sealed.md) słowo kluczowe, aby wskazać, że Klasa nie może być klasą bazową dla jakichkolwiek dodatkowych klas. Podjęto próbę wygenerowania z wygenerowanej klasy błędu kompilatora CS0509 "nie może pochodzić od typu zapieczętowanego \<typeName> ".

  Na przykład należy oznaczyć klasę pochodną jako `sealed` .

Poniższy przykład pokazuje kod źródłowy dla `Publication` klasy, a także `PublicationType` Wyliczenie, które jest zwracane przez `Publication.PublicationType` Właściwość. Oprócz elementów członkowskich, z których dziedziczy <xref:System.Object> , `Publication` Klasa definiuje następujące unikatowe elementy członkowskie i przesłonięcia elementu członkowskiego:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Ponieważ `Publication` Klasa jest `abstract` , nie można utworzyć wystąpienia bezpośrednio w kodzie, podobnie jak w poniższym przykładzie:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Jednak jego Konstruktor wystąpień można wywołać bezpośrednio z konstruktorów klas pochodnych, ponieważ kod źródłowy `Book` klasy pokazuje.

- Dwie właściwości powiązane z publikacją

  `Title`jest właściwością tylko do odczytu <xref:System.String> , której wartość jest dostarczana przez wywołanie `Publication` konstruktora.

  `Pages`jest właściwością do odczytu i zapisu <xref:System.Int32> , która wskazuje, ile razem stron publikacji ma. Wartość jest przechowywana w prywatnym polu o nazwie `totalPages` . Musi być liczbą dodatnią lub <xref:System.ArgumentOutOfRangeException> jest generowany.

- Elementy członkowskie powiązane z wydawcą

  Dwie właściwości tylko do odczytu `Publisher` i `Type` . Wartości są początkowo dostarczane przez wywołanie `Publication` konstruktora klasy.

- Elementy członkowskie powiązane z publikowaniem

  Dwie metody, `Publish` i `GetPublicationDate` , ustawiają i zwracają datę publikacji. `Publish`Metoda ustawia `published` flagę prywatną na `true` kiedy jest wywoływana i przypisuje datę przekazaną do niej jako argument do pola prywatnego `datePublished` . `GetPublicationDate`Metoda zwraca ciąg "NYP" `published` , jeśli flaga jest `false` i wartość `datePublished` pola, jeśli jest `true` .

- Elementy członkowskie powiązane z prawami autorskimi

  `Copyright`Metoda przyjmuje nazwę posiadacza praw autorskich i rok praw autorskich jako argumenty i przypisuje je do `CopyrightName` `CopyrightDate` właściwości i.

- Przesłonięcie `ToString` metody

  Jeśli typ nie przesłania <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, zwraca w pełni kwalifikowaną nazwę typu, który jest niewielkim użyciem w rozróżnieniu jednego wystąpienia od drugiego. `Publication`Klasa przesłania <xref:System.Object.ToString%2A?displayProperty=nameWithType> wartość `Title` właściwości.

Na poniższej ilustracji przedstawiono relacje między `Publication` klasą bazową i jej niejawnie dziedziczoną <xref:System.Object> klasą.

![Klasy obiektów i publikacji](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book`Klasa

`Book`Klasa reprezentuje książkę jako wyspecjalizowany typ publikacji. Poniższy przykład pokazuje kod źródłowy dla `Book` klasy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Oprócz elementów członkowskich, z których dziedziczy `Publication` , `Book` Klasa definiuje następujące unikatowe elementy członkowskie i przesłonięcia elementu członkowskiego:

- Dwa konstruktory

  Dwa `Book` konstruktory korzystają z trzech wspólnych parametrów. Dwa, *tytuły* i *Wydawca*odpowiadają parametrom `Publication` konstruktora. Trzecia jest *autorem*, który jest przechowywany w publicznej niezmiennej `Author` właściwości. Jeden Konstruktor zawiera parametr *ISBN* , który jest przechowywany we `ISBN` Właściwości autoproperty.

  Pierwszy Konstruktor używa słowa kluczowego [this](../language-reference/keywords/this.md) do wywołania innego konstruktora. Tworzenie łańcucha konstruktorów jest typowym wzorcem definiującym konstruktory. Konstruktory z mniejszą liczbą parametrów zapewniają wartości domyślne podczas wywoływania konstruktora przy użyciu największej liczby parametrów.

  Drugi Konstruktor używa słowa kluczowego [Base](../language-reference/keywords/base.md) do przekazania tytułu i nazwy wydawcy do konstruktora klasy bazowej. Jeśli nie utworzysz jawnie wywołania konstruktora klasy bazowej w kodzie źródłowym, kompilator języka C# automatycznie poda wywołanie do konstruktora klasy podstawowej "Default lub bez parametrów.

- Właściwość tylko do odczytu `ISBN` , która zwraca `Book` międzynarodowy numer standardowej księgi obiektu, unikatowy numer 10 lub 13 cyfr. ISBN jest dostarczany jako argument do jednego z `Book` konstruktorów. ISBN jest przechowywany w prywatnym polu zapasowym, które jest automatycznie generowane przez kompilator.

- Właściwość tylko do odczytu `Author` . Nazwa autora jest dostarczana jako argument do obu `Book` konstruktorów i jest przechowywana we właściwości.

- Dwie właściwości dotyczące cen tylko do odczytu `Price` i `Currency` . Ich wartości są podawane jako argumenty w `SetPrice` wywołaniu metody. `Currency`Właściwość jest symbolem waluty ISO o trzech cyfrach (na przykład USD dla dolara USA). Symbole waluty ISO można pobrać z <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> właściwości. Obie te właściwości są zewnętrznie tylko do odczytu, ale obie można ustawić przez kod w `Book` klasie.

- `SetPrice`Metoda, która ustawia wartości `Price` `Currency` właściwości i. Te wartości są zwracane przez te same właściwości.

- Przesłania do `ToString` metody (dziedziczone z `Publication` ) i <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> <xref:System.Object.GetHashCode%2A> metody i (dziedziczone z <xref:System.Object> ).

  O ile nie zostanie on zastąpiony, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> Metoda sprawdza równość odwołań. Oznacza to, że dwie zmienne obiektu są uważane za równe, jeśli odwołują się do tego samego obiektu. W `Book` klasie, z drugiej strony, dwa `Book` obiekty powinny być równe, jeśli mają ten sam ISBN.

  Podczas przesłonięcia <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody należy również zastąpić <xref:System.Object.GetHashCode%2A> metodę, która zwraca wartość używaną przez środowisko uruchomieniowe do przechowywania elementów w kolekcjach skrótów w celu wydajnego pobierania. Kod skrótu powinien zwracać wartość zgodną z testem dla równości. Ponieważ zastąpienie <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> `true` Właściwości ISBN dwóch `Book` obiektów jest równe, zwracany jest kod skrótu obliczony przez wywołanie <xref:System.String.GetHashCode%2A> metody ciągu zwracanego przez `ISBN` Właściwość.

Na poniższej ilustracji przedstawiono relacje między `Book` klasą a `Publication` klasą bazową.

![Klasy publikacji i książek](media/book-class.jpg)

Teraz można utworzyć wystąpienie `Book` obiektu, wywołać zarówno unikatowy, jak i dziedziczonych elementów członkowskich, i przekazać go jako argument do metody, która oczekuje parametru typu `Publication` lub typu `Book` , jak pokazano w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Projektowanie abstrakcyjnych klas podstawowych i ich klas pochodnych
<a name="abstract"></a>

W poprzednim przykładzie zdefiniowano klasę bazową, która udostępnia implementację wielu metod, aby umożliwić pochodnym klasom współużytkowanie kodu. W wielu przypadkach jednak Klasa bazowa nie powinna dostarczyć implementacji. Zamiast tego Klasa bazowa jest *klasą abstrakcyjną* , która deklaruje *metody abstrakcyjne*; służy jako szablon definiujący składowe, które muszą zostać zaimplementowane przez każdą klasę pochodną. Zwykle w abstrakcyjnej klasie podstawowej implementacja każdego typu pochodnego jest unikatowa dla tego typu. Klasa jest oznaczona za pomocą abstrakcyjnego słowa kluczowego, ponieważ nie ma sensu tworzenia wystąpienia `Publication` obiektu, chociaż Klasa zapewniała implementacje wspólnych funkcji dla publikacji.

Na przykład każdy zamknięty dwuwymiarowy kształt geometryczny zawiera dwie właściwości: obszar, wewnętrzny zakres kształtu; i obwód oraz odległość wzdłuż krawędzi kształtu. Jednak sposób, w jaki te właściwości są obliczane, zależy całkowicie od określonego kształtu. Formuła służąca do obliczania obwodu (lub obwodu) koła, na przykład, różni się od tego trójkąta. `Shape`Klasa jest `abstract` klasą z `abstract` metodami. Wskazuje, że klasy pochodne mają takie same funkcje, ale te klasy pochodne implementują te funkcje w różny sposób.

W poniższym przykładzie zdefiniowano abstrakcyjną klasę bazową o nazwie `Shape` , która definiuje dwie właściwości: `Area` i `Perimeter` . Oprócz oznaczania klasy [abstrakcyjnym](../language-reference/keywords/abstract.md) słowem kluczowym każdy element członkowski wystąpienia jest również oznaczony za pomocą słowa kluczowego [abstract](../language-reference/keywords/abstract.md) . W takim przypadku `Shape` przesłania również <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę zwracającą nazwę typu, a nie jego w pełni kwalifikowaną nazwę. Definiuje dwa statyczne elementy członkowskie `GetArea` i `GetPerimeter` , które umożliwiają wywołującym łatwe pobieranie obszaru i obwodu wystąpienia dowolnej klasy pochodnej. Gdy przekazujesz wystąpienie klasy pochodnej do jednej z tych metod, środowisko uruchomieniowe wywołuje metodę przesłaniania klasy pochodnej.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Następnie można utworzyć klasy z `Shape` tego, które reprezentują określone kształty. W poniższym przykładzie zdefiniowano trzy klasy, `Triangle` , `Rectangle` , i `Circle` . Każda z nich używa formuły unikatowej dla danego kształtu do obliczenia obszaru i obwodu. Niektóre klasy pochodne definiują również właściwości, takie jak `Rectangle.Diagonal` i `Circle.Diameter` , które są unikatowe dla kształtu, który reprezentuje.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

W poniższym przykładzie zastosowano obiekty pochodne od `Shape` . Tworzy wystąpienie obiektu Array obiektów pochodzących od `Shape` i wywołuje metody statyczne `Shape` klasy, co spowoduje Zawijanie zwracanych `Shape` wartości właściwości. Środowisko uruchomieniowe pobiera wartości z przesłoniętych właściwości typów pochodnych. Przykład rzutuje również każdy `Shape` obiekt w tablicy na jego typ pochodny i, jeśli rzutowanie powiedzie się, pobiera właściwości tej konkretnej podklasy `Shape` .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Zobacz też

- [Klasy i obiekty](../tour-of-csharp/classes-and-objects.md)
- [Dziedziczenie (Przewodnik programowania w języku C#)](../programming-guide/classes-and-structs/inheritance.md)
