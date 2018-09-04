---
title: Dziedziczenie w języku C#
description: Dowiedz się użyć dziedziczenia w C#, bibliotek i aplikacji.
author: rpetrusha
ms.author: ronpet
ms.date: 07/05/2018
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 15e2ddd7e103857054973d6c4ed7401d6f91af0d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502167"
---
# <a name="inheritance-in-c-and-net"></a>Dziedziczenie w języku C# i .NET

W tym samouczku przedstawiono dziedziczenia w C#. Dziedziczenie jest funkcją zorientowane obiektowo języków programowania, która pozwala zdefiniować klasę bazową, który zapewnia funkcje (danych i zachowanie) i definiowanie klas pochodnych, które dziedziczą lub zastąpić tę funkcję.

## <a name="prerequisites"></a>Wymagania wstępne

Ten samouczek zakłada, że po zainstalowaniu platformy .NET Core. Aby uzyskać instrukcje dotyczące instalacji, zobacz [Przewodnik instalacji platformy .NET Core](https://www.microsoft.com/net/core). Należy również edytora kodu. W tym samouczku [programu Visual Studio Code](https://code.visualstudio.com), chociaż można używać dowolnego edytora kodu, wybranych przez użytkownika.

## <a name="running-the-examples"></a>Uruchamianie przykładów

Aby utworzyć i uruchomić przykłady w tym samouczku, należy użyć [dotnet](../../core/tools/dotnet.md) narzędzie z wiersza polecenia. Wykonaj następujące kroki dla każdego przykładu:

1. Utwórz katalog do przechowywania w przykładzie.
1. Wprowadź [dotnet nową konsolę](../../core/tools/dotnet-new.md) polecenie w wierszu polecenia, aby utworzyć nowy projekt .NET Core.
1. Skopiuj i Wklej kod z przykładu do edytora kodu.
1. Wprowadź [dotnet restore](../../core/tools/dotnet-restore.md) polecenia z wiersza polecenia do załadowania lub przywracanie zależności projektu.

  [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Wprowadź [dotnet, uruchom](../../core/tools/dotnet-run.md) polecenie, aby skompilować i wykonać przykładu.

## <a name="background-what-is-inheritance"></a>Tło: Co to jest dziedziczenie?

*Dziedziczenie* jest jednym z podstawowych atrybutów programowanie zorientowane obiektowo. Pozwala na zdefiniowanie klasę podrzędną, która używa (dziedziczy) rozszerza i modyfikuje zachowanie klasy nadrzędnej. Nosi nazwę klasy, której członkowie są dziedziczeni *klasy bazowej*. Nosi nazwę klasy, która dziedziczy członków klasy podstawowej *klasy pochodnej*.

Obsługa języka C# i .NET *pojedyncze dziedziczenie* tylko. Oznacza to, że klasa może dziedziczyć tylko pojedynczą klasę. Jednak dziedziczenia jest przechodnia, co pozwala na zdefiniowanie Hierarchia dziedziczenia dla zestawu typów. Innymi słowy, wpisz `D` może dziedziczyć z typu `C`, który dziedziczy z typu `B`, który dziedziczy z klasy podstawowej typu `A`. Ponieważ dziedziczenia jest przechodnia, elementy członkowskie typu `A` są dostępne dla typów `D`.

Nie wszystkie elementy członkowskie klasy bazowej są dziedziczone przez klasy pochodne. Następujące elementy członkowskie nie są dziedziczone:

- [Konstruktory statyczne](../programming-guide/classes-and-structs/static-constructors.md), który inicjowanie danych statycznych w klasie.

- [Konstruktory wystąpień](../programming-guide/classes-and-structs/constructors.md), które należy wywołać, aby utworzyć nowe wystąpienie klasy. Każda klasa musi definiować własne konstruktorów.

- [Finalizatory](../programming-guide/classes-and-structs/destructors.md), które są wywoływane przez moduł wyrzucania elementów bezużytecznych w środowisku uruchomieniowym do likwidacji wystąpienia klasy.

Podczas wszystkich innych członków klasy podstawowej są dziedziczone przez klasy pochodne, czy są one widoczne czy nie zależy od ich dostępność. Ułatwienia dostępu członków wpływa na jego widoczność klas pochodnych w następujący sposób:

- [Prywatne](../language-reference/keywords/private.md) elementy są widoczne tylko w klasach pochodnych, które są osadzone w swojej klasie bazowej. W przeciwnym razie nie są widoczne w klasach pochodnych. W poniższym przykładzie `A.B` to klasa zagnieżdżona, która pochodzi od klasy `A`, i `C` pochodzi od klasy `A`. Prywatna `A.value` pole jest widoczne w A.B. Jednak jeśli usuniesz komentarze z `C.GetValue` metody i podjęcie próby skompilować przykład generuje błąd kompilatora CS0122: "" A.value"jest niedostępny z powodu swojego poziomu ochrony".

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chronione](../language-reference/keywords/protected.md) elementy są widoczne tylko w klasach pochodnych.

- [Wewnętrzny](../language-reference/keywords/internal.md) elementy są widoczne tylko w klasach pochodnych, które znajdują się w tym samym zestawie jako klasa bazowa. Nie są widoczne w klasach pochodnych znajduje się w innym zestawie z klasy bazowej.

- [Publiczne](../language-reference/keywords/public.md) elementów członkowskich są widoczne w klasach pochodnych i są dostępne w ramach interfejsu publicznego klasy pochodnej. Publiczne dziedziczone elementy Członkowskie mogą być wywoływane tak, jakby zostały zdefiniowane w klasie pochodnej. W poniższym przykładzie klasa `A` definiuje metodę o nazwie `Method1`, a klasa `B` dziedziczy z klasy `A`. Przykład następnie wywołuje `Method1` tak, jakby był metodą instancji na `B`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Klasy pochodne mogą również *zastąpienia* odziedziczone składowe, zapewniając alternatywnej implementacji. Aby można było przesłonić składowej, składowej w klasie podstawowej musi być oznaczony przez [wirtualnego](../language-reference/keywords/virtual.md) — słowo kluczowe. Domyślnie składowych klasy bazowej nie są oznaczane jako `virtual` i nie może zostać zastąpiona. Próba zastąpienia niewirtualną elementu członkowskiego, jak poniższy przykład generuje błąd kompilatora CS0506: "<member> nie można przesłonić odziedziczonej składowej <member> , ponieważ nie jest oznaczony wirtualnego, abstract" ani "override.

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

W niektórych przypadkach klasę pochodną *musi* zastępować implementację klasy bazowej. Składowych klasy oznaczona za pomocą podstawowej [abstrakcyjne](../language-reference/keywords/abstract.md) — słowo kluczowe wymaga, że klasy pochodne je zastąpić. Podjęto próbę skompilować poniższy przykład generuje błąd kompilatora CS0534, "<class> nie implementuje odziedziczonej abstrakcyjnej składowej <member>", ponieważ klasa `B` zapewnia implementacji `A.Method1`.

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

Dziedziczenie ma zastosowanie tylko do klasy i interfejsy. Inne kategorie (struktur, delegaty i wyliczeń) nie obsługują dziedziczenia. Ze względu na te reguły próby kompilacji kodu, jak w poniższym przykładzie generuje błąd kompilatora CS0527: "Typ"ValueType"na liście interfejsów nie jest interfejsem." Komunikat o błędzie wskazuje, że, mimo że można zdefiniować interfejsy, które implementuje struktury, dziedziczenie nie jest obsługiwany.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Niejawne dziedziczenia

Oprócz żadnych typów, które mogą dziedziczyć z przez pojedyncze dziedziczenie, wszystkie typy w systemie typów .NET niejawnie dziedziczą z <xref:System.Object> lub typ pochodzący od niego. Typowe funkcje <xref:System.Object> jest dostępny dla dowolnego typu.

Aby zobaczyć, jakie niejawne dziedziczenia oznacza, że czynnością jest zdefiniowanie nowej klasy `SimpleClass`, to po prostu pustą definicję klasy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Następnie można użyć odbicia, (która pozwala sprawdzić metadanych typu, aby uzyskać informacje dotyczące tego typu) w celu uzyskania listy elementów członkowskich, które należą do `SimpleClass` typu. Mimo że jeszcze nie zdefiniowano żadnych elementów członkowskich w swojej `SimpleClass` klasy, dane wyjściowe z przykładu wskazuje, że faktycznie ma dziewięciu członków. Jedną z tych składowych jest konstruktorem bez parametrów (lub domyślny), automatycznie dostarczany dla `SimpleClass` typu przez kompilator języka C#. Pozostałe ośmiu są elementami członkowskimi <xref:System.Object>, typ, z której wszystkie klasy i interfejsy na platformie .NET system typów ostatecznie niejawnie dziedziczą.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Niejawne dziedziczenie z <xref:System.Object> klasy sprawia, że te metody są dostępne dla `SimpleClass` klasy:

- Publicznie `ToString` metody, która konwertuje `SimpleClass` obiektu na jego reprezentację ciągu zwraca w pełni kwalifikowana nazwa typu. W tym przypadku `ToString` metoda zwraca ciąg "SimpleClass".

- Trzy metody testowania pod kątem równości dwóch obiektów: publiczne wystąpienia `Equals(Object)` metody, publiczne statyczne `Equals(Object, Object)` metoda i publiczne statyczne `ReferenceEquals(Object, Object)` metody. Domyślnie te metody testu równości odwołań; oznacza to aby być taka sama, dwie zmienne obiektu musi odwoływać się do tego samego obiektu.

- Publicznie `GetHashCode` metody, która oblicza wartość, która umożliwia wystąpienia typu, który ma być używany w kolekcjach w formie skrótu.

- Publicznie `GetType` metody, która zwraca <xref:System.Type> obiekt, który reprezentuje `SimpleClass` typu.

- Chronionego <xref:System.Object.Finalize%2A> metody, który został zaprojektowany, aby zwolnić niezarządzane zasoby, zanim pamięci obiektu jest odzyskiwane przez moduł odśmiecania pamięci.

- Chronionego <xref:System.Object.MemberwiseClone%2A> metody, która tworzy pobieżne klonowanie bieżącego obiektu.

Ze względu na niejawne dziedziczenie, można wywołać wszelkie odziedziczonej składowej przed `SimpleClass` obiekt po prostu, tak jakby znajdowała się faktycznie elementu członkowskiego zdefiniowany w `SimpleClass` klasy. Na przykład poniższy przykład wywołuje `SimpleClass.ToString` metody, która `SimpleClass` dziedziczy <xref:System.Object>.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

W poniższej tabeli wymieniono kategorie typów, utworzone w języku C# oraz typy, z których niejawnie dziedziczą. Każdego typu podstawowego sprawia, że inny zbiór elementów członkowskich jest dostępna za pośrednictwem dziedziczenia dla typów pochodnych niejawnie.

| Kategoria typów | Dziedziczy niejawnie z                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| class         | <xref:System.Object>                                                          |
| struktura         | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| delegate      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dziedziczenie i "to" relacji

Zazwyczaj dziedziczenia jest używany do wyrażenia "to" relację między klasą bazową i jeden lub więcej klas pochodnych, w których specjalistyczne wersje klasy bazowej; klasy pochodne Klasa pochodna jest typem klasy bazowej. Na przykład `Publication` klasa reprezentuje publikacji dowolnego rodzaju i `Book` i `Magazine` klasy reprezentują określonych rodzajów publikacji.

> [!NOTE]
> Klasy lub struktury, można zaimplementować jeden większej liczby interfejsów. Podczas implementacji interfejsu często są prezentowane, jako obejście pojedyncze dziedziczenie lub sposób użycia dziedziczenia w strukturach, jest ona przeznaczona do innej relacji (relację "może zrobić") między interfejsem, a jego typ implementujący niż express dziedziczenie. Interfejs definiuje podzbiór funkcji (np. możliwość testowania pod kątem równości do porównywania lub Sortuj obiektów, lub obsługuje wrażliwość na ustawienia kulturowe formatowanie i analizowanie), która udostępnia interfejs do jego typy implementujące.

Należy pamiętać, że "jest" również określa relację między typem i określonego wystąpienia tego typu. W poniższym przykładzie `Automobile` to klasa, która ma trzy unikatowe właściwości tylko do odczytu: `Make`, producent samochodów; `Model`, rodzaj samochodów; i `Year`, rok produkcji. Twoje `Automobile` klasa również ma konstruktora, w której argumenty są przypisywane do wartości właściwości i zastępuje ona <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody do tworzenia ciąg, który unikatowo identyfikuje `Automobile` wystąpienia zamiast `Automobile` klasy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

W tym przypadku nie należy traktować dziedziczenia do reprezentowania określonych samochodu marek i modeli. Na przykład, nie trzeba zdefiniować `Packard` typu do reprezentowania wytwarzane przez firma samochodowa Motor Packard samochodów. Zamiast tego należy je reprezentować, tworząc `Automobile` obiektu odpowiednimi wartościami, które są przekazywane do jej konstruktora klasy, tak jak w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Relacji oparte na dziedziczenie w to a najlepiej jest stosowany do klasy podstawowej i pochodnej klasy, Dodaj dodatkowe elementy członkowskie do klasy bazowej lub które wymagają dodatkowych funkcji, które nie znajduje się w klasie bazowej.

## <a name="designing-the-base-class-and-derived-classes"></a>Projektowanie klasy podstawowej i klasy pochodne

Przyjrzyjmy się proces projektowania klasy podstawowej i jej klasy pochodne. W tej sekcji należy zdefiniować klasę bazową `Publication`, która reprezentuje publikacji jakiegokolwiek rodzaju, takich jak książki, magazynu, gazet, dziennikiem, artykułu itp. Należy także zdefiniować `Book` klasę pochodzącą od `Publication`. Można łatwo rozszerzyć przykładu tak, aby zdefiniować innych klas pochodnych, takich jak `Magazine`, `Journal`, `Newspaper`, i `Article`.

### <a name="the-base-publication-class"></a>Klasa bazowa publikacji

W projektowaniu swoje `Publication` klasy, musisz wprowadzić kilka decyzje dotyczące projektu:

- Jakie elementy członkowskie do uwzględnienia w podstawowym `Publication` klasy oraz tego, czy `Publication` członkowie dostarczać implementacje metod czy `Publication` jest abstrakcyjną klasę bazową, która służy jako szablon do jej klasy pochodne.

  W tym przypadku `Publication` klasa będzie dostarczać implementacje metod. [Projektowania abstrakcyjnych klas bazowych i ich klasy pochodne](#abstract) sekcja zawiera przykład pokazujący abstrakcyjną klasę bazową do definiowania metod, które klasy pochodne muszą przesłaniać. Klasy pochodne mogą wszelkie implementacji, które jest odpowiednie dla typu pochodnego.

  Możliwość ponownego użycia kodu (oznacza to, że wiele klas pochodnych udział deklarację i implementację base metody klasy i nie trzeba je zastąpić) jest zaletą nieabstrakcyjnej klasy podstawowej. W związku z tym, należy dodać członków do `Publication` jeśli ich kod jest może być współużytkowane przez niektóre lub najbardziej wyspecjalizowane `Publication` typów. Jeśli nie wydajnie dostarczać implementacje klasy bazowej, będzie znajdą koniczności podawania implementacji elementu członkowskiego w przeważającej mierze identyczny w klasach pochodnych zamiast pojedynczego wykonania w klasie bazowej. Potrzebę utrzymywania zduplikowany kodem w wielu lokalizacjach jest potencjalnym źródłem błędów.

  Zarówno w celu zmaksymalizowania kodu ponownego użycia oraz do tworzenia hierarchii dziedziczenia logiczne i intuicyjne, chcesz upewnij się, że uwzględniasz w `Publication` klasy tylko dane i funkcje, które są wspólne dla wszystkich lub większości publikacji. Klasy pochodne następnie zaimplementuj elementy członkowskie, które są unikatowe dla szczególnych typów publikacji, które reprezentują one.

- Jak daleko w celu rozszerzenia swojej hierarchii klas. Czy chcesz tworzyć hierarchii co najmniej trzech klas, a nie po prostu klasę bazową i jeden lub więcej klas pochodnych? Na przykład `Publication` może być klasą bazową dla `Periodical`, który z kolei jest klasą bazową dla `Magazine`, `Journal` i `Newspaper`.

  Dla przykładu, użyjesz hierarchii małych `Publication` klasy i jednej klasy pochodnej `Book`. Można łatwo rozszerzyć przykładu tak, aby utworzyć kilka dodatkowych klas, które wynikają z `Publication`, takich jak `Magazine` i `Article`.

- Czy warto utworzyć wystąpienia klasy bazowej. Jeśli nie, należy zastosować [abstrakcyjne](../language-reference/keywords/abstract.md) — słowo kluczowe do klasy. W przeciwnym razie swoje `Publication` klasy mogą być utworzone przez wywołanie metody jej konstruktora klasy. Jeśli do utworzenia wystąpienia klasy oznaczone zostanie podjęta próba `abstract` — słowo kluczowe przez bezpośrednie wywołanie do jej konstruktora klasy, kompilator języka C# generuje błąd CS0144, "Nie można utworzyć wystąpienia abstrakcyjnej klasy lub interfejsu." Jeśli zostanie podjęta próba, aby utworzyć wystąpienie klasy przy użyciu odbicia, metoda zgłasza wyjątek odbicia <xref:System.MemberAccessException>.

  Domyślnie klasę bazową mogą być utworzone przez wywołanie metody jej konstruktora klasy. Nie masz definiuje jawnie konstruktora klasy. Jeżeli nie są dostępne w kodzie źródłowym klasy bazowej, kompilator języka C# automatycznie zapewnia domyślnego (bezparametrowego) konstruktora.

  Dla przykładu, będzie można oznaczyć `Publication` klasy [abstrakcyjne](../language-reference/keywords/abstract.md) tak, aby nie można utworzyć wystąpienia.  `abstract` Klasy bez `abstract` metody oznacza, że ta klasa reprezentuje pojęcie abstrakcyjne, jest współużytkowana przez kilka konkretnych klas (takich jak `Book`, `Journal`).

- Czy pochodne musi dziedziczyć z implementacji klasy podstawowej, określonych elementów członkowskich, czy mają możliwość zastąpienia implementacji klasy podstawowej lub czy musi dostarczyć implementację. Możesz użyć [abstrakcyjne](../language-reference/keywords/abstract.md) słowo kluczowe, aby wymusić na klasach pochodnych, aby zapewniać implementację. Możesz użyć [wirtualnego](../language-reference/keywords/virtual.md) — słowo kluczowe, aby zezwolić na zastąpienie metody klasy podstawowej w klasach pochodnych. Domyślnie są metody zdefiniowane w klasie bazowej *nie* możliwym do zastąpienia.

 `Publication` Klasa nie ma żadnych `abstract` metody, ale sama klasa `abstract`.

- Czy klasę pochodną reprezentuje ostatnią klasę w hierarchii dziedziczenia, a nie sam można użyć jako klasę bazową dla dodatkowych klasach pochodnych. Domyślnie każda klasa może służyć jako klasę bazową. Można zastosować [zapieczętowanego](../language-reference/keywords/sealed.md) — słowo kluczowe, aby wskazać, że klasa nie może służyć jako klasę bazową dla wszelkich dodatkowych zajęć. Podjęto próbę pochodzi od klasy zapieczętowanej generowany błąd kompilatora CS0509, "nie może pochodzić od typu zapieczętowanego <typeName>".

  Dla przykładu, możesz oznaczyć klasy pochodnej jako `sealed`.

Poniższy kod przedstawia kod źródłowy `Publication` klasy, a także `PublicationType` wyliczenie, który jest zwracany przez `Publication.PublicationType` właściwości. Oprócz elementów członkowskich, które dziedziczy <xref:System.Object>, `Publication` klasa definiuje następujące unikatowych elementów członkowskich i element członkowski zastępuje element:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Ponieważ `Publication` klasa jest `abstract`, nie można utworzyć wystąpienia bezpośrednio z kodu, jak w poniższym przykładzie:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Jednak jego konstruktora wystąpienia mogą być wywoływane bezpośrednio z konstruktorami klasy pochodnej, jako kod źródłowy `Book` klasy pokazuje.

- Dwie właściwości związane z publikacji

  `Title` jest tylko do odczytu <xref:System.String> właściwość, której wartość jest dostarczana przez wywołanie `Publication` konstruktora.

  `Pages` jest do odczytu i zapisu <xref:System.Int32> ma właściwość, która wskazuje, ile łącznie strony publikacji. Wartość jest przechowywana w polu prywatnej o nazwie `totalPages`. Musi być liczbą dodatnią lub <xref:System.ArgumentOutOfRangeException> zgłaszany.

- Składowe związane z wydawcy

  Dwie właściwości tylko do odczytu, `Publisher` i `Type`. Wartości pierwotnie są dostarczane przez wywołanie metody `Publication` konstruktora klasy.

- Powiązane publikowania elementów członkowskich

  Dwie metody `Publish` i `GetPublicationDate`, ustawianie i zwracanie dat publikacji. `Publish` Metoda ustawia prywatnej `published` flaga `true` gdy jest wywoływana i przypisuje Data przekazany jako argument do prywatnego `datePublished` pola. `GetPublicationDate` Metoda zwraca ciąg "NYP", jeśli `published` flaga jest `false`i wartość `datePublished` pola, gdy jest `true`.

- Pokrewnych elementów członkowskich

  `Copyright` Metoda przyjmuje jako argumenty nazwę właściciela praw autorskich i rok praw autorskich i przypisuje je do `CopyrightName` i `CopyrightDate` właściwości.

- Zastępowanie `ToString` — metoda

  Jeśli typ nie zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody zwraca w pełni kwalifikowaną nazwę typu, który jest rzadko używane w rozróżnianie jednego wystąpienia z innego. `Publication` Klasy zastąpienia <xref:System.Object.ToString%2A?displayProperty=nameWithType> do zwracania wartości `Title` właściwości.

Na poniższym rysunku przedstawiono relację między podstawowym `Publication` klasy i jego niejawnie dziedziczenia <xref:System.Object> klasy.

![Klasy obiektu i publikacji](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book` Klasy

`Book` Klasa reprezentuje książki jako wyspecjalizowane typ publikacji. Poniższy przykład pokazuje kod źródłowy `Book` klasy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Oprócz elementów członkowskich, które dziedziczy `Publication`, `Book` klasa definiuje następujące unikatowych elementów członkowskich i element członkowski zastępuje element:

- Dwa konstruktory

  Dwa `Book` konstruktory udostępnianie trzech typowych parametrów. Dwa *tytuł* i *wydawcy*, odpowiadać parametrom `Publication` konstruktora. Trzecia będzie *Autor*, który jest przechowywany w prywatnej `authorName` pola. Zawiera jeden konstruktor *isbn* parametr, który jest przechowywany w `ISBN` właściwości automatycznej.

  Pierwszy Konstruktor używa [to](../language-reference/keywords/this.md) — słowo kluczowe do wywoływania innego konstruktora. Tworzenie łańcuchów Konstruktor jest typowym definiować konstruktorów. Konstruktorów z parametrami mniej udostępni wartości domyślne podczas wywoływania konstruktora z największą liczbą parametrów.

  Drugi Konstruktor używa [podstawowy](../language-reference/keywords/base.md) — słowo kluczowe do przekazania nazwy stanowiska i wydawcy do konstruktora klasy bazowej. Jeśli nie dokonasz jawnym wywołaniem konstruktora klasy bazowej, w kodzie źródłowym, kompilator języka C# automatycznie dostarczy wywołanie klasy bazowej domyślnego lub konstruktora bez parametrów.

- Tylko do odczytu `ISBN` właściwość, która zwraca `Book` International Standard książki numer obiektu, unikatowe 10 - lub 13-cyfrowy numer. ISBN jest dostarczany jako argument do jednego z `Book` konstruktorów. ISBN są przechowywane w polem zapasowym prywatnego, który został wygenerowany automatycznie przez kompilator.

- Tylko do odczytu `Author` właściwości. Imię i nazwisko autora jest dostarczany jako argument do obu `Book` konstruktorów i jest przechowywany w prywatnej `authorName` pola.

- Dwie właściwości tylko do odczytu dotyczące cen, `Price` i `Currency`. Ich wartości są przekazywane jako argumenty `SetPrice` wywołania metody. Ceny są przechowywane w pole private `bookPrice`. `Currency` Właściwość jest symbol waluty ISO trzycyfrowy (na przykład USD za dolar amerykański) i jest przechowywany w prywatnej `ISOCurrencySymbol` pola. Symbole waluty ISO można pobrać z <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> właściwości.

- A `SetPrice` metody, która ustawia wartości `bookPrice` i `ISOCurrencySymbol` pola. Te wartości są zwracane przez `Price` i `Currency` właściwości.

- Zastąpienia `ToString` — metoda (odziedziczone `Publication`) i <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> i <xref:System.Object.GetHashCode%2A> metody (odziedziczone <xref:System.Object>).

  O ile nie zostanie on przesłonięty <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody testów dla równości odwołań. Oznacza to, że dwie zmienne do obiektu są traktowane jako równe, jeżeli odnoszą się do tego samego obiektu. W `Book` klasy, z drugiej strony dwa `Book` obiekty powinny być równe, jeśli mają one ten sam ISBN.

  Gdy zastąpisz <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody, konieczne jest również przesłonięcie <xref:System.Object.GetHashCode%2A> metody, która zwraca wartość, która na podstawie środowisko uruchomieniowe do przechowywania elementów w kolekcji skrótu dla efektywne pobieranie. Wartość skrótu powinien zwrócić wartość, która jest zgodna z testem pod kątem równości. Ponieważ została zastąpiona <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> do zwrócenia `true` Jeśli właściwości ISBN dwóch `Book` obiekty są równe, zwraca wartość skrótu obliczane przez wywołanie metody <xref:System.String.GetHashCode%2A> ciąg zwracany przez metodę `ISBN` właściwości.

Na poniższym rysunku przedstawiono relację między `Book` klasy i `Publication`, jej klasy bazowej.

![Klasy publikacji i książki](media/book-class.jpg)

Teraz można utworzyć wystąpienie `Book` obiektu, wywołaj jego unikatowy i dziedziczonych członków i przekazać go jako argument do metody, która oczekuje, że parametr typu `Publication` lub typu `Book`, jak pokazano w poniższym przykładzie.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Projektowanie abstrakcyjnych klas bazowych i ich klasy pochodne
<a name="abstract"></a>

W poprzednim przykładzie zdefiniowano klasę bazową, przewidzianego implementację na wiele sposobów, aby umożliwić udostępnianie kodu w klasach pochodnych. W wielu przypadkach jednak klasa bazowa nie powinien zapewniać implementację. Klasa bazowa jest *abstrakcyjna klasa* oświadcza, że *metody abstrakcyjne*; służy jako szablon, który definiuje składowe każdej klasy pochodnej musi implementować. Zazwyczaj w abstrakcyjna klasa bazowa implementacji każdego typu pochodnego jest unikatowa dla tego typu. Oznaczyć klasę za pomocą abstract — słowo kluczowe, ponieważ ona żadnego znaczenia, aby utworzyć wystąpienie `Publication` obiektu, chociaż klasa dostarczył implementacji funkcji, które są wspólne dla publikacji.

Na przykład każdego zamknięty kształt geometryczny dwuwymiarową zawiera dwie właściwości: obszar, wewnętrzny zakres kształtu; i obwodowej lub odległości wzdłuż krawędzi kształtu. Sposób, w którym te właściwości są obliczane, jednak zależy od całkowicie określonego kształtu. Obliczanie obwodowej (lub obwodu) koło, na przykład różni się od, trójkąt. `Shape` Klasa jest `abstract` klasy `abstract` metody. Wskazująca klasy pochodne udostępnić taką samą funkcjonalność, ale te klasy pochodne zaimplementować tę funkcję inaczej.

W poniższym przykładzie zdefiniowano abstrakcyjna klasa bazowa o nazwie `Shape` definiuje dwie właściwości: `Area` i `Perimeter`. Oprócz oznakowania klasy za pomocą [abstrakcyjne](../language-reference/keywords/abstract.md) — słowo kluczowe, każdy członek wystąpienia również jest oznaczona za pomocą [abstrakcyjne](../language-reference/keywords/abstract.md) — słowo kluczowe. W tym przypadku `Shape` zastępuje również <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, aby zwrócić nazwę typu, a nie jego w pełni kwalifikowana nazwa. Które definiują dwa statyczne elementy członkowskie `GetArea` i `GetPerimeter`, umożliwiające obiektom wywołującym można łatwo pobrać pole i obwód wystąpienie klasy pochodnej. Jeśli wystąpienie klasy pochodnej do jednej z tych metod, środowisko wykonawcze wywołuje metodę zastępującą klasy pochodnej.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Następnie można uzyskać niektóre klasy z `Shape` reprezentujące określonych kształtów. Poniższy przykład definiuje trzy klasy `Triangle`, `Rectangle`, i `Circle`. Każda używa formuły, które są unikatowe dla tego konkretnego kształtu do obliczenia pole i obwód. Niektóre z klas pochodnych również zdefiniować właściwości, takie jak `Rectangle.Diagonal` i `Circle.Diameter`, które są unikatowe dla kształtu, które reprezentują one.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

W poniższym przykładzie użyto obiektów pochodzących od `Shape`. Metoda tworzy tablicę obiektów pochodzących od `Shape` i wywołuje metody statyczne `Shape` klasy, która otacza zwrócenia `Shape` wartości właściwości. Środowisko uruchomieniowe pobiera wartości z właściwości zgodnym z przesłoniętą typów pochodnych. Przykład również każdej rzutuje `Shape` obiektów w tablicy, do jego typ pochodny i, jeśli rzutowanie zakończy się powodzeniem, pobiera właściwości tego konkretnego podklasą `Shape`. 

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Zobacz też

- [Klasy i obiekty](../tour-of-csharp/classes-and-objects.md)   
- [Dziedziczenie (C# Programming Guide)](../programming-guide/classes-and-structs/inheritance.md)
