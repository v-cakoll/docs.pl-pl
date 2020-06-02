---
title: Projekt parametrów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: 46c1b8f03d054a63ea837a73fd30eeed163ab0a4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290100"
---
# <a name="parameter-design"></a>Projekt parametrów

Ta sekcja zawiera szczegółowe wskazówki dotyczące projektowania parametrów, w tym sekcje z instrukcjami dotyczącymi sprawdzania argumentów. Ponadto należy zapoznać się z wytycznymi opisanymi w temacie [Parametry nazewnictwa](naming-parameters.md).

 ✔️ należy użyć najmniej pochodnego typu parametru, który zapewnia funkcje wymagane przez element członkowski.

 Załóżmy na przykład, że chcesz zaprojektować metodę, która wylicza kolekcję i drukuje każdy element do konsoli. Taka metoda powinna przyjmować <xref:System.Collections.IEnumerable> jako parametr, nie <xref:System.Collections.ArrayList> lub <xref:System.Collections.IList> , na przykład.

 ❌NIE należy używać zarezerwowanych parametrów.

 Jeśli w przyszłych wersjach jest wymaganych więcej danych wejściowych, można dodać nowe Przeciążenie.

 ❌NIE mają publicznie uwidocznionych metod, które pobierają wskaźniki, tablice wskaźników lub tablice wielowymiarowe jako parametry.

 Wskaźniki i tablice wielowymiarowe są stosunkowo trudne do użycia. W prawie wszystkich przypadkach interfejsy API można przeprojektować, aby uniknąć wykonywania tych typów jako parametrów.

 ✔️ NALEŻY umieścić wszystkie `out` Parametry po wszystkich parametrach przez wartość i `ref` Parametry (z wyjątkiem tablic parametrów), nawet jeśli powoduje niespójność w kolejności parametrów między przeciążeniami (zobacz [przeciążanie elementów członkowskich](member-overloading.md)).

 `out`Parametry mogą być widoczne jako dodatkowe zwracane wartości, a grupowanie ich razem sprawia, że podpis metody jest łatwiejszy do zrozumienia.

 ✔️ są spójne w parametrach nazw podczas zastępowania elementów członkowskich lub implementowania elementów członkowskich interfejsu.

 To lepiej komunikuje się relacją między metodami.

### <a name="choose-between-enum-and-boolean-parameters"></a>Wybór między parametrami enum i Boolean
 ✔️ Użyj typów wyliczeniowych, jeśli element członkowski mógłby w inny sposób mieć co najmniej dwa parametry logiczne.

 ❌NIE używaj wartości logicznych, chyba że masz absolutną pewność, że nie będzie potrzebna więcej niż dwie wartości.

 Wyliczenia dają miejsce na przyszłe Dodawanie wartości, ale należy zwrócić uwagę na wszystkie implikacje dodawania wartości do typów wyliczeniowych, które są opisane w [projekcie wyliczenia](enum.md).

 ✔️ ROZWAŻYĆ użycie wartości logicznych dla parametrów konstruktora, które są w prawdziwie wartościami dwustanowymi i są po prostu używane do inicjowania właściwości logicznych.

### <a name="validate-arguments"></a>Weryfikuj argumenty
 ✔️ weryfikują argumenty przekazane do publicznych, chronionych lub jawnie zaimplementowanych elementów członkowskich. Throw <xref:System.ArgumentException?displayProperty=nameWithType> lub jednej z jej podklas, jeśli sprawdzanie poprawności zakończy się niepowodzeniem.

 Należy zauważyć, że rzeczywista weryfikacja nie musi występować w publicznej lub chronionej składowej. Może się to zdarzyć na niższym poziomie w pewnej prywatnej lub wewnętrznej procedurze. Głównym punktem jest to, że cały obszar powierzchni, który jest widoczny dla użytkowników końcowych, sprawdza argumenty.

 ✔️ zgłosić, <xref:System.ArgumentNullException> czy argument o wartości null zostanie przeszedł, a element członkowski nie obsługuje argumentów o wartości null.

 ✔️ sprawdzać poprawność parametrów wyliczeniowych.

 Nie należy przyjmować argumentów wyliczenia w zakresie zdefiniowanym przez wyliczenie. Środowisko CLR umożliwia rzutowanie dowolnej wartości całkowitej na wartość enum, nawet jeśli wartość nie jest zdefiniowana w wyliczeniu.

 ❌NIE należy używać <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> do sprawdzania zakresu wyliczenia.

 ✔️ należy pamiętać, że argumenty modyfikowalne mogą ulec zmianie po sprawdzeniu poprawności.

 Jeśli składowa jest wrażliwa na zabezpieczenia, zachęca się do tworzenia kopii, a następnie weryfikacji i przetwarzania argumentu.

### <a name="pass-parameters"></a>Przekazywanie parametrów
 Z perspektywy projektanta struktury istnieją trzy główne grupy parametrów: według wartości parametrów, `ref` parametrów i `out` parametrów.

 Gdy argument jest przenoszona przez parametr przez wartość, element członkowski otrzymuje kopię rzeczywistego argumentu przekazywane. Jeśli argument jest typem wartości, kopia argumentu jest umieszczana na stosie. Jeśli argument jest typem referencyjnym, kopia odwołania jest umieszczana na stosie. Najpopularniejsze języki CLR, takie jak C#, Visual Basic i C++, domyślnie przechodzą parametry według wartości.

 Gdy argument jest przenoszona przez `ref` parametr, element członkowski otrzymuje odwołanie do rzeczywistego argumentu przekazywane. Jeśli argument jest typem wartości, odwołanie do argumentu jest umieszczane na stosie. Jeśli argument jest typem referencyjnym, odwołanie do odwołania jest umieszczane na stosie. `Ref`parametrów można użyć, aby zezwolić elementowi członkowskiemu na modyfikowanie argumentów przekazane przez wywołującego.

 `Out`parametry są podobne do `ref` parametrów, z niewielkimi różnicami. Parametr jest początkowo uznawany za nieprzypisany i nie może zostać odczytany w treści elementu członkowskiego przed przypisaniem pewnej wartości. Ponadto parametr musi mieć przypisaną pewną wartość przed zwróceniem elementu członkowskiego.

 ❌Należy unikać używania `out` lub `ref` parametrów.

 Użycie `out` lub `ref` Parametry wymaga środowiska ze wskaźnikami, zrozumienie, jak typy wartości i typy referencyjne różnią się i obsługują metody z wieloma zwracanymi wartościami. Ponadto różnice między `out` i `ref` parametrów nie są szeroko zrozumiałe. Architektzy architektury projektowani dla ogólnych odbiorców nie powinni oczekiwać od użytkowników, aby współpracowały z tymi `out` `ref` parametrami.

 ❌NIE przekazuj typów odwołań przez odwołanie.

 Istnieją pewne ograniczone wyjątki dla reguły, takie jak metoda, która może służyć do wymiany odwołań.

### <a name="members-with-variable-number-of-parameters"></a>Elementy członkowskie ze zmienną liczbą parametrów
 Elementy członkowskie, które mogą przyjmować zmienną liczbę argumentów, są wyrażane przez podanie parametru array. Na przykład <xref:System.String> zapewnia następującą metodę:

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 Użytkownik może następnie wywołać metodę w <xref:System.String.Format%2A?displayProperty=nameWithType> następujący sposób:

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 Dodanie słowa kluczowego params języka C# do parametru array powoduje zmianę parametru na parametr Array "so-called params" i udostępnia skrót do tworzenia tablicy tymczasowej.

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 Dzięki temu użytkownik może wywołać metodę przez przekazanie elementów tablicy bezpośrednio na liście argumentów.

 `String.Format("File {0} not found in {1}",filename,directory);`

 Należy zauważyć, że słowo kluczowe params można dodać tylko do ostatniego parametru na liście parametrów.

 ✔️ Rozważ dodanie słowa kluczowego params do parametrów tablicowych, jeśli oczekujesz, że użytkownicy końcowi przechodzą tablice o niemniejszej liczbie elementów. Jeśli spodziewasz się, że wiele elementów zostanie przekazanych w typowych scenariuszach, użytkownicy prawdopodobnie nie przekazują tych elementów wewnętrznie, a więc słowo kluczowe params nie jest konieczne.

 ❌Należy unikać używania tablic parametrów, jeśli obiekt wywołujący będzie niemal zawsze miał dane wejściowe już w tablicy.

 Na przykład elementy członkowskie z parametrami tablicy bajtów niemal nigdy nie będą wywoływane przez przekazanie pojedynczych bajtów. Z tego powodu parametry tablicy bajtowej w .NET Framework nie używają słowa kluczowego params.

 ❌NIE używaj tablic parametrów, jeśli tablica jest modyfikowana przez element członkowski przyjmujący parametr tablicy parametrów.

 Ze względu na fakt, że wiele kompilatorów przeniesie argumenty do elementu członkowskiego do tablicy tymczasowej w miejscu wywołania, tablica może być obiektem tymczasowym i w związku z tym wszelkie modyfikacje tablicy zostaną utracone.

 ✔️ ROZWAŻYĆ użycie słowa kluczowego params w prostym przeciążeniu, nawet jeśli bardziej złożone Przeciążenie nie mogło go użyć.

 Zwróć się do siebie, jeśli użytkownicy będą mieli wartość tablica parametrów w jednym przeciążeniu, nawet jeśli nie była we wszystkich przeciążeń.

 ✔️ Spróbuj zamówić parametry, aby można było użyć słowa kluczowego params.

 ✔️ ROZWAŻYĆ dostarczenie specjalnych przeciążeń i ścieżek kodu dla wywołań z niewielką liczbą argumentów w skrajnie wrażliwych na wydajność interfejsach API.

 Dzięki temu można uniknąć tworzenia obiektów tablicowych, gdy interfejs API jest wywoływany z niewielką liczbą argumentów. Nazwy parametrów należy tworzyć za pomocą pojedynczej formy parametru array i dodawania sufiksu liczbowego.

 Tę czynność należy wykonać tylko wtedy, gdy w przypadku przechodzenia do specjalnego przypadku należy utworzyć tablicę i wywołać bardziej ogólną metodę.

 ✔️ należy pamiętać, że wartość null może zostać przeniesiona jako argument tablicy parametrów.

 Przed przetworzeniem należy sprawdzić, czy tablica nie ma wartości null.

 ❌NIE należy używać `varargs` metod, w zależności od wielokropka.

 Niektóre języki CLR, takie jak C++, obsługują alternatywną Konwencję do przekazywania list parametrów zmiennych nazywanych `varargs` metodami. Konwencji nie należy używać w strukturach, ponieważ nie jest ona zgodna ze specyfikacją CLS.

### <a name="pointer-parameters"></a>Parametry wskaźnika
 Ogólnie rzecz biorąc wskaźniki nie powinny znajdować się w obszarze publicznej powierzchni dobrze zaprojektowanej struktury kodu zarządzanego. W większości przypadków wskaźniki powinny być hermetyzowane. Jednak w niektórych przypadkach wskaźniki są wymagane ze względu na współdziałanie, a w takich przypadkach są odpowiednie wskaźniki.

 ✔️ zapewnić alternatywę dla każdego elementu członkowskiego, który przyjmuje argument wskaźnika, ponieważ wskaźniki nie są zgodne ze specyfikacją CLS.

 ❌Unikaj jednoczesnego sprawdzania argumentów wskaźnika.

 ✔️ Wykonaj typowe konwencje powiązane ze wskaźnikami podczas projektowania członków ze wskaźnikami.

 Na przykład nie ma potrzeby przekazywania indeksu początkowego, ponieważ można użyć prostej arytmetycznej wskaźnika, aby osiągnąć ten sam wynik.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania elementów członkowskich](member.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
