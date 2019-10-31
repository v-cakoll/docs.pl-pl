---
title: Dziedziczenie wC#
description: Dowiedz się, jak C# używać dziedziczenia w bibliotekach i aplikacjach.
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: b69da841c7c7a2e518191ad34f2ff5b368899728
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120134"
---
# <a name="inheritance-in-c-and-net"></a>Dziedziczenie w języku C# i .NET

Ten samouczek przedstawia sposób dziedziczenia w C#programie. Dziedziczenie to funkcja języków programowania zorientowanego obiektowo, która umożliwia zdefiniowanie klasy bazowej, która zapewnia konkretne funkcje (dane i zachowanie) i definiuje klasy pochodne, które dziedziczą lub przesłaniają te funkcje.

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

C#i .NET obsługuje tylko *pojedyncze dziedziczenie* . Oznacza to, że Klasa może dziedziczyć tylko z pojedynczej klasy. Dziedziczenie jest jednak przechodnie, co pozwala na zdefiniowanie hierarchii dziedziczenia dla zestawu typów. Innymi słowy, typ `D` może dziedziczyć po typie `C`, który dziedziczy z typu `B`, który dziedziczy z typu klasy bazowej `A`. Ponieważ dziedziczenie jest przechodnie, elementy członkowskie typu `A` są dostępne dla typu `D`.

Nie wszystkie składowe klasy bazowej są dziedziczone przez klasy pochodne. Następujące elementy członkowskie nie są dziedziczone:

- [Konstruktory statyczne](../programming-guide/classes-and-structs/static-constructors.md), które inicjują statyczne dane klasy.

- [Konstruktory wystąpień](../programming-guide/classes-and-structs/constructors.md), które są wywoływane w celu utworzenia nowego wystąpienia klasy. Każda klasa musi definiować własne konstruktory.

- [Finalizatory](../programming-guide/classes-and-structs/destructors.md), które są wywoływane przez moduł wyrzucania elementów bezużytecznych środowiska uruchomieniowego, aby zniszczyć wystąpienia klasy.

Wszystkie inne elementy członkowskie klasy bazowej są dziedziczone przez klasy pochodne, niezależnie od tego, czy są one widoczne, czy nie są zależne od ich dostępności. Dostępność elementu członkowskiego ma wpływ na widoczność klas pochodnych w następujący sposób:

- [Prywatne](../language-reference/keywords/private.md) składowe są widoczne tylko w klasach pochodnych, które są zagnieżdżone w klasie podstawowej. W przeciwnym razie nie są one widoczne w klasach pochodnych. W poniższym przykładzie `A.B` jest klasą zagnieżdżoną, która pochodzi od `A`, a `C` pochodzi z `A`. Pole `A.value` prywatny jest widoczne w A.B. Jeśli jednak usuniesz Komentarze z metody `C.GetValue` i spróbujemy skompilować przykład, generuje błąd kompilatora CS0122: "A. Value" jest niedostępny z powodu swojego poziomu ochrony ".

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chronione](../language-reference/keywords/protected.md) elementy członkowskie są widoczne tylko w klasach pochodnych.

- [Wewnętrzne](../language-reference/keywords/internal.md) elementy członkowskie są widoczne tylko w klasach pochodnych, które znajdują się w tym samym zestawie, co Klasa bazowa. Nie są one widoczne w klasach pochodnych znajdujących się w innym zestawie z klasy podstawowej.

- [Publiczne](../language-reference/keywords/public.md) składowe są widoczne w klasach pochodnych i są częścią interfejsu publicznego klasy pochodnej. Publiczne dziedziczone elementy członkowskie mogą być wywoływane tak, jakby są zdefiniowane w klasie pochodnej. W poniższym przykładzie Klasa `A` definiuje metodę o nazwie `Method1`, a Klasa `B` dziedziczy z `A`klasy. Przykład następnie wywołuje `Method1` tak, jakby była metodą wystąpienia na `B`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Klasy pochodne mogą również *przesłaniać* dziedziczone elementy członkowskie, dostarczając alternatywną implementację. Aby możliwe było przesłonięcie elementu członkowskiego, element członkowski w klasie bazowej musi być oznaczony za pomocą słowa kluczowego [Virtual](../language-reference/keywords/virtual.md) . Domyślnie elementy członkowskie klasy bazowej nie są oznaczone jako `virtual` i nie można ich zastąpić. Próba zastąpienia niewirtualnego elementu członkowskiego, jak pokazano w poniższym przykładzie, generuje błąd kompilatora CS0506: "\<składowej > nie może przesłonić dziedziczonej składowej \<>, ponieważ nie jest oznaczona jako wirtualna, abstrakcyjna lub przesłonięcie.

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

W niektórych przypadkach Klasa pochodna *musi* przesłonić implementację klasy bazowej. Elementy członkowskie klasy bazowej oznaczone za pomocą słowa kluczowego [abstract](../language-reference/keywords/abstract.md) wymagają, aby klasy pochodne zostały przez nie zastąpione. Próba skompilowania poniższego przykładu powoduje wygenerowanie błędu kompilatora CS0534, "&lt;klasy&gt; nie implementuje dziedziczonej abstrakcyjnej składowej &lt;elementu członkowskiego&gt;", ponieważ Klasa `B` nie zapewnia implementacji dla `A.Method1`.

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

Oprócz typów, z których mogą dziedziczyć za pośrednictwem pojedynczego dziedziczenia, wszystkie typy w systemie typu .NET niejawnie dziedziczą z <xref:System.Object> lub typu pochodnego. Typowe funkcje <xref:System.Object> są dostępne dla dowolnego typu.

Aby zobaczyć, co oznacza niejawne dziedziczenie, zdefiniujmy nową klasę `SimpleClass`, która jest po prostu pustą definicją klasy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Następnie można użyć odbicia, które umożliwia sprawdzenie metadanych typu w celu uzyskania informacji na temat tego typu, aby uzyskać listę elementów członkowskich należących do typu `SimpleClass`. Chociaż nie zdefiniowano żadnych elementów członkowskich w klasie `SimpleClass`, dane wyjściowe z przykładu wskazują, że faktycznie ma dziewięć członków. Jeden z tych elementów członkowskich jest konstruktorem bez parametrów (lub domyślnym), który jest dostarczany automatycznie dla typu `SimpleClass` przez C# kompilator. Pozostałe osiem są członkami <xref:System.Object>, typu, z którego wszystkie klasy i interfejsy w systemie typu .NET ostatecznie dziedziczą.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Niejawne dziedziczenie z klasy <xref:System.Object> sprawia, że te metody są dostępne dla klasy `SimpleClass`:

- Publiczna Metoda `ToString`, która konwertuje obiekt `SimpleClass` na jego reprezentację ciągu, zwraca w pełni kwalifikowaną nazwę typu. W tym przypadku Metoda `ToString` zwraca ciąg "SimpleClass".

- Trzy metody, które testują pod kątem równości dwóch obiektów: publiczne wystąpienie `Equals(Object)` metodzie, publiczną metodę `Equals(Object, Object)`d static i publiczną metodę `ReferenceEquals(Object, Object)`d static. Domyślnie te metody testują równość odniesienia; oznacza to, że jest równe, dwie zmienne obiektów muszą odwoływać się do tego samego obiektu.

- Publiczna Metoda `GetHashCode`, która oblicza wartość, która pozwala na wystąpienie typu, który ma być używany w kolekcjach skrótów.

- Publiczna Metoda `GetType`, która zwraca obiekt <xref:System.Type>, który reprezentuje typ `SimpleClass`.

- <xref:System.Object.Finalize%2A> chronionej metody, która została zaprojektowana w celu zwolnienia zasobów niezarządzanych przed odjęciem pamięci obiektu przez moduł wyrzucania elementów bezużytecznych.

- Metoda chroniona <xref:System.Object.MemberwiseClone%2A>, która tworzy płytki klonowania bieżącego obiektu.

Ze względu na niejawne dziedziczenie można wywołać dowolny Dziedziczony element członkowski z obiektu `SimpleClass`, tak jakby był to element członkowski zdefiniowany w klasie `SimpleClass`. Na przykład poniższy przykład wywołuje metodę `SimpleClass.ToString`, która `SimpleClass` dziedziczy po <xref:System.Object>.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

W poniższej tabeli wymieniono kategorie typów, które można utworzyć w programie C# , oraz typy, z których dziedziczą niejawnie. Każdy typ podstawowy udostępnia inny zestaw elementów członkowskich za pomocą dziedziczenia do niejawnie pochodnych typów.

| Kategoria typu | Niejawnie dziedziczone z                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| class         | <xref:System.Object>                                                          |
| struktura        | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| delegate      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dziedziczenie i relacja "is"

Zwykle dziedziczenie jest stosowane do wyrażenia "is" relacji między klasą bazową i co najmniej jedną klasą pochodną, gdzie klasy pochodne są wyspecjalizowanymi wersjami klasy bazowej; Klasa pochodna jest typem klasy bazowej. Na przykład Klasa `Publication` reprezentuje publikację dowolnego rodzaju, a klasy `Book` i `Magazine` reprezentują określone typy publikacji.

> [!NOTE]
> Klasa lub struktura może zaimplementować jeden lub więcej interfejsów. Podczas gdy implementacja interfejsu jest często prezentowana jako obejście dla pojedynczego dziedziczenia lub jako sposób używania dziedziczenia z strukturami, należy przedstawić inną relację (relację "może") między interfejsem a jego typem implementującym niż strukturze. Interfejs definiuje podzestaw funkcji (takich jak możliwość testowania równości, porównywania lub sortowania obiektów lub do obsługi analizy zależnej od kultury i formatowania), które Interfejs udostępnia dla jego typów implementujących.

Należy zauważyć, że "is" także wskazuje relację między typem i określonym wystąpieniem tego typu. W poniższym przykładzie `Automobile` jest klasą, która ma trzy unikatowe właściwości tylko do odczytu: `Make`, producent urządzenia przenośnego; `Model`, Rodzaj samochodu: i `Year`, rok produkcji. Klasa `Automobile` ma także konstruktora, którego argumenty są przypisane do wartości właściwości, i zastępuje metodę <xref:System.Object.ToString%2A?displayProperty=nameWithType>, aby utworzyć ciąg, który jednoznacznie identyfikuje wystąpienie `Automobile`, a nie klasę `Automobile`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

W takim przypadku nie należy polegać na dziedziczeniu do reprezentowania określonych samochodów i modeli. Na przykład nie trzeba definiować typu `Packard`, aby reprezentować samochody, które są wytwarzane przez firmę Packard Motor samochodowa. Zamiast tego można je przedstawić przez utworzenie obiektu `Automobile` z odpowiednimi wartościami przekazaną do jego konstruktora klasy, jak pokazano w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Jest to relacja oparta na dziedziczeniu najlepiej zastosowana do klasy bazowej i do klas pochodnych, które dodają do klasy podstawowej dodatkowe elementy członkowskie lub które wymagają dodatkowych funkcji nieobecnych w klasie podstawowej.

## <a name="designing-the-base-class-and-derived-classes"></a>Projektowanie klasy bazowej i klas pochodnych

Przyjrzyjmy się procesowi projektowania klasy bazowej i jej klas pochodnych. W tej sekcji zdefiniujesz klasę bazową `Publication`, która reprezentuje publikację dowolnego rodzaju, na przykład książkę, czasopismo, gazetę, arkusz, artykuł itd. Zdefiniujesz również klasę `Book`, która pochodzi z `Publication`. Możesz łatwo zwiększyć przykład, aby zdefiniować inne klasy pochodne, takie jak `Magazine`, `Journal`, `Newspaper`i `Article`.

### <a name="the-base-publication-class"></a>Klasa publikacji podstawowej

Podczas projektowania klasy `Publication` należy podjąć pewne decyzje dotyczące projektowania:

- Elementy członkowskie do uwzględnienia w klasie bazowej `Publication` i czy `Publication` składowe udostępniają implementacje metod, czy `Publication` jest abstrakcyjną klasą bazową, która służy jako szablon klas pochodnych.

  W takim przypadku Klasa `Publication` udostępnia implementacje metod. [Projektowanie abstrakcyjnych klas podstawowych i ich klas pochodnych](#abstract) zawiera przykład, który używa abstrakcyjnej klasy bazowej do definiowania metod, które muszą zostać przesłonięte przez klasy pochodne. Klasy pochodne są bezpłatne, aby zapewnić implementację, która jest odpowiednia dla typu pochodnego.

  Możliwość ponownego użycia kodu (oznacza to, że wiele klas pochodnych korzysta z deklaracji i implementacji metod klasy bazowej i nie trzeba ich przesłonić) jest zaletą nieabstrakcyjnych klas podstawowych. W związku z tym należy dodać elementy członkowskie do `Publication`, jeśli ich kod może być współużytkowany przez niektóre lub większość wyspecjalizowanych typów `Publication`. Jeśli nie podasz wydajnych implementacji klas podstawowych, będziesz mieć możliwość zapewnienia większości identycznych implementacji elementów członkowskich w klasach pochodnych, a nie pojedynczej implementacji w klasie bazowej. Konieczność utrzymania duplikatu kodu w wielu lokalizacjach jest potencjalnym źródłem błędów.

  Aby zmaksymalizować użycie kodu i utworzyć logiczną i intuicyjną hierarchię dziedziczenia, należy się upewnić, że należy uwzględnić w klasie `Publication` tylko te dane i funkcje, które są wspólne dla wszystkich lub do większości publikacji. Klasy pochodne następnie implementują elementy członkowskie, które są unikatowe dla określonych rodzajów publikacji, które reprezentują.

- Jak daleko, aby zwiększyć hierarchię klas. Czy chcesz opracować hierarchię trzech lub więcej klas, a nie po prostu klasy bazowej i co najmniej jednej klasy pochodnej? Na przykład `Publication` może być klasą bazową `Periodical`, która z kolei jest klasą bazową `Magazine`, `Journal` i `Newspaper`.

  Przykładowo będziesz używać małej hierarchii klasy `Publication` i pojedynczej klasy pochodnej, `Book`. Można łatwo zwiększyć przykład, aby utworzyć szereg dodatkowych klas, które pochodzą od `Publication`, takie jak `Magazine` i `Article`.

- Określa, czy warto utworzyć wystąpienie klasy bazowej. Jeśli tak nie jest, należy zastosować [abstrakcyjne](../language-reference/keywords/abstract.md) słowo kluczowe do klasy. W przeciwnym razie Klasa `Publication` można utworzyć wystąpienie przez wywołanie jego konstruktora klasy. Jeśli zostanie podjęta próba utworzenia wystąpienia klasy oznaczonej za pomocą słowa kluczowego `abstract` przez bezpośrednie wywołanie konstruktora klasy, C# kompilator GENERUJE błąd CS0144, "nie można utworzyć wystąpienia klasy abstrakcyjnej lub interfejsu". Jeśli zostanie podjęta próba utworzenia wystąpienia klasy przy użyciu odbicia, Metoda odbicia zgłasza <xref:System.MemberAccessException>.

  Domyślnie można utworzyć wystąpienie klasy bazowej, wywołując jej Konstruktor klas. Nie musisz jawnie definiować konstruktora klasy. Jeśli nie występuje w kodzie źródłowym klasy podstawowej, C# kompilator automatycznie udostępnia domyślny Konstruktor (bez parametrów).

  Przykładowo należy oznaczyć klasę `Publication` jako [abstract](../language-reference/keywords/abstract.md) , aby nie można było utworzyć wystąpienia.  Klasa `abstract` bez żadnych metod `abstract` wskazuje, że ta klasa reprezentuje abstrakcyjną koncepcję, która jest współużytkowana przez kilka klas konkretnych (takich jak `Book`, `Journal`).

- Bez względu na to, czy klasy pochodne muszą dziedziczyć implementację klasy bazowej określonych elementów członkowskich, czy mają opcję przesłaniania implementacji klasy bazowej, czy też muszą dostarczyć implementację. Aby wymusić implementację klas pochodnych, należy użyć słowa kluczowego [abstract](../language-reference/keywords/abstract.md) . Możesz użyć słowa kluczowego [Virtual](../language-reference/keywords/virtual.md) , aby umożliwić klasom pochodnym przesłonięcie metody klasy bazowej. Domyślnie metody zdefiniowane w klasie bazowej *nie* są możliwe do zastąpienia.

 Klasa `Publication` nie ma żadnych metod `abstract`, ale sama klasa jest `abstract`.

- Czy Klasa pochodna reprezentuje ostateczną klasę w hierarchii dziedziczenia i nie może być używana jako klasa bazowa dla dodatkowych klas pochodnych. Domyślnie każda klasa może być klasą bazową. Można zastosować [zapieczętowane](../language-reference/keywords/sealed.md) słowo kluczowe, aby wskazać, że Klasa nie może być klasą bazową dla jakichkolwiek dodatkowych klas. Próba wygenerowania z CS0509 błędu kompilatora wygenerowanego przez klasę "nie może pochodzić od typu zapieczętowanego \<typeName >".

  Na przykład należy oznaczyć klasę pochodną jako `sealed`.

Poniższy przykład pokazuje kod źródłowy dla klasy `Publication`, a także Wyliczenie `PublicationType`, które jest zwracane przez właściwość `Publication.PublicationType`. Oprócz elementów członkowskich, które dziedziczy po <xref:System.Object>, Klasa `Publication` definiuje następujące unikatowe elementy członkowskie i przesłonięcia składowych:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Ponieważ Klasa `Publication` jest `abstract`, nie można jej utworzyć bezpośrednio w kodzie, podobnie jak w poniższym przykładzie:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Jednak jego Konstruktor wystąpień można wywołać bezpośrednio z konstruktorów klas pochodnych, ponieważ kod źródłowy klasy `Book`.

- Dwie właściwości powiązane z publikacją

  `Title` jest właściwością <xref:System.String> tylko do odczytu, której wartość jest dostarczana przez wywołanie konstruktora `Publication`.

  `Pages` jest właściwością <xref:System.Int32> do odczytu i zapisu, która wskazuje, ile razem stron publikacji ma. Wartość jest przechowywana w prywatnym polu o nazwie `totalPages`. Musi być liczbą dodatnią lub zostanie zgłoszony <xref:System.ArgumentOutOfRangeException>.

- Elementy członkowskie powiązane z wydawcą

  Dwie właściwości tylko do odczytu, `Publisher` i `Type`. Wartości są początkowo dostarczane przez wywołanie konstruktora klasy `Publication`.

- Elementy członkowskie powiązane z publikowaniem

  Dwie metody, `Publish` i `GetPublicationDate`, ustawiają i zwracają datę publikacji. Metoda `Publish` ustawia flagę Private `published` do `true`, gdy jest wywoływana, i przypisuje datę przekazaną do niej jako argument do pola `datePublished` prywatnego. Metoda `GetPublicationDate` zwraca ciąg "NYP", jeśli flaga `published` jest `false`, a wartość pola `datePublished`, jeśli jest `true`.

- Elementy członkowskie powiązane z prawami autorskimi

  Metoda `Copyright` przyjmuje nazwę posiadacza praw autorskich i rok praw autorskich jako argumenty i przypisuje je do właściwości `CopyrightName` i `CopyrightDate`.

- Przesłonięcie metody `ToString`

  Jeśli typ nie przesłania metody <xref:System.Object.ToString%2A?displayProperty=nameWithType>, zwraca w pełni kwalifikowaną nazwę typu, który jest niewielkim użyciem w rozróżnieniu jednego wystąpienia od drugiego. Klasa `Publication` przesłania <xref:System.Object.ToString%2A?displayProperty=nameWithType>, aby zwrócić wartość właściwości `Title`.

Na poniższej ilustracji przedstawiono relacje między klasą podstawową `Publication` i jej niejawnie dziedziczoną klasą <xref:System.Object>.

![Klasy obiektów i publikacji](media/publication-class.jpg)

### <a name="the-book-class"></a>Klasa `Book`

Klasa `Book` reprezentuje książkę jako wyspecjalizowany typ publikacji. Poniższy przykład pokazuje kod źródłowy dla klasy `Book`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Oprócz elementów członkowskich, które dziedziczy po `Publication`, Klasa `Book` definiuje następujące unikatowe elementy członkowskie i przesłonięcia składowych:

- Dwa konstruktory

  Dwa konstruktory `Book` korzystają z trzech wspólnych parametrów. Dwa, *tytuły* i *Wydawca*odpowiadają parametrom konstruktora `Publication`. Trzeci jest *autorem*, który jest przechowywany na publicznej niezmiennej `Author` właściwości. Jeden Konstruktor zawiera parametr *ISBN* , który jest przechowywany w `ISBN` właściwości autoproperty.

  Pierwszy Konstruktor używa słowa kluczowego [this](../language-reference/keywords/this.md) do wywołania innego konstruktora. Tworzenie łańcucha konstruktorów jest typowym wzorcem definiującym konstruktory. Konstruktory z mniejszą liczbą parametrów zapewniają wartości domyślne podczas wywoływania konstruktora przy użyciu największej liczby parametrów.

  Drugi Konstruktor używa słowa kluczowego [Base](../language-reference/keywords/base.md) do przekazania tytułu i nazwy wydawcy do konstruktora klasy bazowej. Jeśli nie utworzysz jawnie wywołania konstruktora klasy bazowej w kodzie źródłowym, C# kompilator automatycznie poda wywołanie do konstruktora klasy podstawowej "Default lub bez parametrów.

- Właściwość `ISBN` tylko do odczytu, która zwraca międzynarodowy numer standardowej książki `Book` obiektu, unikatowy numer 10 lub 13-cyfrowy. ISBN jest dostarczany jako argument do jednego z konstruktorów `Book`. ISBN jest przechowywany w prywatnym polu zapasowym, które jest automatycznie generowane przez kompilator.

- Właściwość `Author` tylko do odczytu. Nazwa autora jest podawana jako argument do obu konstruktorów `Book` i jest przechowywana we właściwości.

- Dwie właściwości dotyczące cen tylko do odczytu, `Price` i `Currency`. Ich wartości są podane jako argumenty w wywołaniu metody `SetPrice`. Właściwość `Currency` jest symbolem waluty ISO o trzech cyfrach (na przykład USD dla dolara USA). Symbole waluty ISO można pobrać z właściwości <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A>. Obie te właściwości są zewnętrznie tylko do odczytu, ale obie można ustawić przez kod w klasie `Book`.

- Metoda `SetPrice`, która ustawia wartości właściwości `Price` i `Currency`. Te wartości są zwracane przez te same właściwości.

- Zastępuje metodę `ToString` (Odziedziczone po `Publication`) i metody <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> i <xref:System.Object.GetHashCode%2A> (dziedziczone z <xref:System.Object>).

  O ile nie zostanie on zastąpiony, Metoda <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> sprawdza równość odwołań. Oznacza to, że dwie zmienne obiektu są uważane za równe, jeśli odwołują się do tego samego obiektu. W klasie `Book`, z drugiej strony, dwa obiekty `Book` powinny być równe, jeśli mają ten sam ISBN.

  Podczas przesłonięcia metody <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> należy również zastąpić metodę <xref:System.Object.GetHashCode%2A>, która zwraca wartość używaną przez środowisko uruchomieniowe do przechowywania elementów w kolekcjach skrótów w celu wydajnego pobierania. Kod skrótu powinien zwracać wartość zgodną z testem dla równości. Ponieważ przesłonięto <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> do zwrócenia `true`, jeśli właściwości ISBN dwóch obiektów `Book` są równe, zwracany jest kod skrótu obliczany przez wywołanie metody <xref:System.String.GetHashCode%2A> ciągu zwracanego przez właściwość `ISBN`.

Na poniższej ilustracji przedstawiono relacje między klasą `Book` i `Publication`, jej klasą bazową.

![Klasy publikacji i książek](media/book-class.jpg)

Teraz można utworzyć wystąpienie obiektu `Book`, wywoływać zarówno jego unikatowy, jak i dziedziczonych elementów członkowskich, i przekazać go jako argument do metody, która oczekuje parametru typu `Publication` lub `Book`, jak pokazano w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Projektowanie abstrakcyjnych klas podstawowych i ich klas pochodnych
<a name="abstract"></a>

W poprzednim przykładzie zdefiniowano klasę bazową, która udostępnia implementację wielu metod, aby umożliwić pochodnym klasom współużytkowanie kodu. W wielu przypadkach jednak Klasa bazowa nie powinna dostarczyć implementacji. Zamiast tego Klasa bazowa jest *klasą abstrakcyjną* , która deklaruje *metody abstrakcyjne*; służy jako szablon definiujący składowe, które muszą zostać zaimplementowane przez każdą klasę pochodną. Zwykle w abstrakcyjnej klasie podstawowej implementacja każdego typu pochodnego jest unikatowa dla tego typu. Klasa jest oznaczona za pomocą abstrakcyjnego słowa kluczowego, ponieważ nie ma sensu, aby utworzyć wystąpienie `Publication` obiektu, chociaż Klasa zapewniała implementacje wspólnych funkcji dla publikacji.

Na przykład każdy zamknięty dwuwymiarowy kształt geometryczny zawiera dwie właściwości: obszar, wewnętrzny zakres kształtu; i obwód oraz odległość wzdłuż krawędzi kształtu. Jednak sposób, w jaki te właściwości są obliczane, zależy całkowicie od określonego kształtu. Formuła służąca do obliczania obwodu (lub obwodu) koła, na przykład, różni się od tego trójkąta. Klasa `Shape` jest klasą `abstract` z metodami `abstract`. Wskazuje, że klasy pochodne mają takie same funkcje, ale te klasy pochodne implementują te funkcje w różny sposób.

W poniższym przykładzie zdefiniowano abstrakcyjną klasę bazową o nazwie `Shape`, która definiuje dwie właściwości: `Area` i `Perimeter`. Oprócz oznaczania klasy [abstrakcyjnym](../language-reference/keywords/abstract.md) słowem kluczowym każdy element członkowski wystąpienia jest również oznaczony za pomocą słowa kluczowego [abstract](../language-reference/keywords/abstract.md) . W tym przypadku `Shape` również przesłania metodę <xref:System.Object.ToString%2A?displayProperty=nameWithType>, aby zwracała nazwę typu, a nie w pełni kwalifikowaną nazwę. Definiuje dwa statyczne elementy członkowskie, `GetArea` i `GetPerimeter`, dzięki czemu wywołujący mogą łatwo pobrać obszar i obwód wystąpienia dowolnej klasy pochodnej. Gdy przekazujesz wystąpienie klasy pochodnej do jednej z tych metod, środowisko uruchomieniowe wywołuje metodę przesłaniania klasy pochodnej.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Następnie można utworzyć klasy z `Shape`, które reprezentują określone kształty. W poniższym przykładzie zdefiniowano trzy klasy, `Triangle`, `Rectangle`i `Circle`. Każda z nich używa formuły unikatowej dla danego kształtu do obliczenia obszaru i obwodu. Niektóre klasy pochodne definiują również właściwości, takie jak `Rectangle.Diagonal` i `Circle.Diameter`, które są unikatowe dla kształtu, który reprezentuje.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

W poniższym przykładzie zastosowano obiekty pochodzące z `Shape`. Tworzy wystąpienie obiektu Array obiektów pochodzących od `Shape` i wywołuje metody statyczne klasy `Shape`, co spowoduje Zawijanie zwracanych wartości właściwości `Shape`. Środowisko uruchomieniowe pobiera wartości z przesłoniętych właściwości typów pochodnych. Przykład rzutuje również każdy obiekt `Shape` w tablicy na jego typ pochodny i, jeśli rzutowanie powiedzie się, pobiera właściwości tej konkretnej podklasy `Shape`. 

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Zobacz także

- [Klasy i obiekty](../tour-of-csharp/classes-and-objects.md)
- [DziedziczenieC# (Przewodnik programowania)](../programming-guide/classes-and-structs/inheritance.md)
