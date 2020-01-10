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
ms.openlocfilehash: e3725cd11e170c64b6cbf7d77a7a6526603dfd95
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709117"
---
# <a name="parameter-design"></a>Projekt parametru

Ta sekcja zawiera szczegółowe wskazówki dotyczące projektowania parametrów, w tym sekcje z instrukcjami dotyczącymi sprawdzania argumentów. Ponadto należy zapoznać się z wytycznymi opisanymi w temacie [Parametry nazewnictwa](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ DO** używany najmniej pochodnej typ parametru, który udostępnia funkcje wymagane przez element członkowski.  
  
 Załóżmy na przykład, że chcesz zaprojektować metodę, która wylicza kolekcję i drukuje każdy element do konsoli. Taka metoda powinna przyjmować <xref:System.Collections.IEnumerable> jako parametr, a nie <xref:System.Collections.ArrayList> lub <xref:System.Collections.IList>.  
  
 **X DO NOT** parametry zastrzeżone.  
  
 Jeśli w przyszłych wersjach jest wymaganych więcej danych wejściowych, można dodać nowe Przeciążenie.  
  
 **X DO NOT** zostały publicznie udostępnione metod, które przyjmują wskaźników, tablic wskaźników lub wielowymiarowych tablic jako parametrów.  
  
 Wskaźniki i tablice wielowymiarowe są stosunkowo trudne do użycia. W prawie wszystkich przypadkach interfejsy API można przeprojektować, aby uniknąć wykonywania tych typów jako parametrów.  
  
 **✓ DO** Umieść wszystkie `out` po całej przez wartości parametrów i `ref` parametrów (z wyłączeniem tablice parametrów), nawet jeśli powoduje niespójność w parametrze kolejności między przeciążenia (zobacz [elementu członkowskiego Przeciążanie](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 Parametry `out` mogą być widoczne jako dodatkowe zwracane wartości, a grupowanie ich razem sprawia, że podpis metody jest łatwiejszy do zrozumienia.  
  
 **✓ DO** zachować spójność nazw parametrów, gdy zastępowanie elementów członkowskich lub wykonania członków interfejsu.  
  
 To lepiej komunikuje się relacją między metodami.  
  
### <a name="choose-between-enum-and-boolean-parameters"></a>Wybór między parametrami enum i Boolean  
 **✓ DO** Użyj wyliczenia, jeśli element członkowski w przeciwnym razie byłyby dwóch lub więcej parametrów Boolean.  
  
 **X DO NOT** Użyj wartości logiczne, jeśli nie masz pewności absolutnie nigdy nie będą potrzeba więcej niż dwóch wartości.  
  
 Wyliczenia dają miejsce na przyszłe Dodawanie wartości, ale należy zwrócić uwagę na wszystkie implikacje dodawania wartości do typów wyliczeniowych, które są opisane w [projekcie wyliczenia](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ CONSIDER** przy użyciu wartości logiczne są naprawdę dwustanowy wartości, które są używane do zainicjowania właściwości logicznych parametrów konstruktora.  
  
### <a name="validate-arguments"></a>Weryfikuj argumenty  
 **✓ DO** Waliduj Argumenty przekazane do publicznych, chronionych lub jawnie implementowane elementy członkowskie. Zgłoś <xref:System.ArgumentException?displayProperty=nameWithType>lub jedną z jej podklas, jeśli sprawdzanie poprawności zakończy się niepowodzeniem.  
  
 Należy zauważyć, że rzeczywista weryfikacja nie musi występować w publicznej lub chronionej składowej. Może się to zdarzyć na niższym poziomie w pewnej prywatnej lub wewnętrznej procedurze. Głównym punktem jest to, że cały obszar powierzchni, który jest widoczny dla użytkowników końcowych, sprawdza argumenty.  
  
 **✓ DO** throw <xref:System.ArgumentNullException> Jeśli argument o wartości null została przekazana i element członkowski nie obsługuje wartości null argumentów.  
  
 **✓ DO** sprawdza poprawność parametrów wyliczenia.  
  
 Nie należy przyjmować argumentów wyliczenia w zakresie zdefiniowanym przez wyliczenie. Środowisko CLR umożliwia rzutowanie dowolnej wartości całkowitej na wartość enum, nawet jeśli wartość nie jest zdefiniowana w wyliczeniu.  
  
 **X DO NOT** użyj <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> dla wyliczenia zakresu kontroli.  
  
 **✓ DO** należy pamiętać, że argumenty modyfikowalną mogła ulec zmianie po ich została sprawdzona.  
  
 Jeśli składowa jest wrażliwa na zabezpieczenia, zachęca się do tworzenia kopii, a następnie weryfikacji i przetwarzania argumentu.  
  
### <a name="pass-parameters"></a>Przekazywanie parametrów  
 Z perspektywy projektanta struktury istnieją trzy główne grupy parametrów: według wartości parametrów, parametrów `ref` i parametrów `out`.  
  
 Gdy argument jest przenoszona przez parametr przez wartość, element członkowski otrzymuje kopię rzeczywistego argumentu przekazywane. Jeśli argument jest typem wartości, kopia argumentu jest umieszczana na stosie. Jeśli argument jest typem referencyjnym, kopia odwołania jest umieszczana na stosie. Najpopularniejsze języki CLR, takie jak C#, Visual Basic i C++, domyślnie przekazywać parametry według wartości.  
  
 Gdy argument jest przekazywane za pomocą parametru `ref`, element członkowski otrzymuje odwołanie do rzeczywistego argumentu przekazywane. Jeśli argument jest typem wartości, odwołanie do argumentu jest umieszczane na stosie. Jeśli argument jest typem referencyjnym, odwołanie do odwołania jest umieszczane na stosie. parametrów `Ref` można użyć, aby zezwolić elementowi członkowskiemu na modyfikowanie argumentów przekazane przez wywołującego.  
  
 `Out` parametry są podobne do `ref` parametrów, z niewielkimi różnicami. Parametr jest początkowo uznawany za nieprzypisany i nie może zostać odczytany w treści elementu członkowskiego przed przypisaniem pewnej wartości. Ponadto parametr musi mieć przypisaną pewną wartość przed zwróceniem elementu członkowskiego.  
  
 **X AVOID** przy użyciu `out` lub `ref` parametrów.  
  
 Użycie parametrów `out` lub `ref` wymaga środowiska ze wskaźnikami, zrozumienie, jak typy wartości i typy odwołań różnią się i obsługują metody z wieloma zwracanymi wartościami. Ponadto różnice między `out` i `ref` parametrów nie są szeroko zrozumiałe. Architekty architektury przeznaczone dla ogólnych odbiorców nie powinny oczekiwać, aby użytkownicy korzystali z parametrów `out` lub `ref`.  
  
 **X DO NOT** przekazuj typów referencyjnych przez odwołanie.  
  
 Istnieją pewne ograniczone wyjątki dla reguły, takie jak metoda, która może służyć do wymiany odwołań.  
  
### <a name="members-with-variable-number-of-parameters"></a>Elementy członkowskie ze zmienną liczbą parametrów  
 Elementy członkowskie, które mogą przyjmować zmienną liczbę argumentów, są wyrażane przez podanie parametru array. Na przykład <xref:System.String> zapewnia następującą metodę:  
  
```csharp  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Użytkownik może następnie wywołać metodę <xref:System.String.Format%2A?displayProperty=nameWithType> w następujący sposób:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Dodanie słowa C# kluczowego params do parametru array powoduje zmianę parametru na parametr Array "so-calld" i udostępnia skrót do tworzenia tablicy tymczasowej.  
  
```csharp  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Dzięki temu użytkownik może wywołać metodę przez przekazanie elementów tablicy bezpośrednio na liście argumentów.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Należy zauważyć, że słowo kluczowe params można dodać tylko do ostatniego parametru na liście parametrów.  
  
 **✓ CONSIDER** Dodawanie params — słowo kluczowe do tablicy parametrów, Jeśli przypuszczasz, użytkownikom końcowym przekazać tablice o niewielkiej liczby elementów. Jeśli spodziewasz się, że wiele elementów zostanie przekazanych w typowych scenariuszach, użytkownicy prawdopodobnie nie przekazują tych elementów wewnętrznie, a więc słowo kluczowe params nie jest konieczne.  
  
 **X AVOID** przy użyciu tablic parametrów, jeśli element wywołujący prawie zawsze musi danych wejściowych już w tablicy.  
  
 Na przykład elementy członkowskie z parametrami tablicy bajtów niemal nigdy nie będą wywoływane przez przekazanie pojedynczych bajtów. Z tego powodu parametry tablicy bajtowej w .NET Framework nie używają słowa kluczowego params.  
  
 **X DO NOT** Użycie tablic parametrów, jeśli tablica jest modyfikowany przez element członkowski, biorąc parametru params tablicy.  
  
 Ze względu na fakt, że wiele kompilatorów przeniesie argumenty do elementu członkowskiego do tablicy tymczasowej w miejscu wywołania, tablica może być obiektem tymczasowym i w związku z tym wszelkie modyfikacje tablicy zostaną utracone.  
  
 **✓ CONSIDER** przy użyciu słowa kluczowego params w prosty przeciążenia, nawet w przypadku bardziej złożonych przeciążenia nie można użyć.  
  
 Zwróć się do siebie, jeśli użytkownicy będą mieli wartość tablica parametrów w jednym przeciążeniu, nawet jeśli nie była we wszystkich przeciążeń.  
  
 **✓ DO** próby kolejność parametrów umożliwiają użyj słowa kluczowego params.  
  
 **✓ CONSIDER** zapewnienie przeciążeń szczególne i ścieżki kodu dla wywołania z niewielką liczbę argumentów w bardzo ważnych wydajności interfejsów API.  
  
 Dzięki temu można uniknąć tworzenia obiektów tablicowych, gdy interfejs API jest wywoływany z niewielką liczbą argumentów. Nazwy parametrów należy tworzyć za pomocą pojedynczej formy parametru array i dodawania sufiksu liczbowego.  
  
 Tę czynność należy wykonać tylko wtedy, gdy w przypadku przechodzenia do specjalnego przypadku należy utworzyć tablicę i wywołać bardziej ogólną metodę.  
  
 **✓ DO** należy pamiętać, że null można przekazany jako argument tablicy parametrów.  
  
 Przed przetworzeniem należy sprawdzić, czy tablica nie ma wartości null.  
  
 **X DO NOT** użyj `varargs` metod, znanej także jako wielokropka.  
  
 Niektóre języki CLR, takie jak C++, obsługują alternatywną Konwencję do przekazywania list parametrów zmiennych o nazwie `varargs` metody. Konwencji nie należy używać w strukturach, ponieważ nie jest ona zgodna ze specyfikacją CLS.  
  
### <a name="pointer-parameters"></a>Parametry wskaźnika  
 Ogólnie rzecz biorąc wskaźniki nie powinny znajdować się w obszarze publicznej powierzchni dobrze zaprojektowanej struktury kodu zarządzanego. W większości przypadków wskaźniki powinny być hermetyzowane. Jednak w niektórych przypadkach wskaźniki są wymagane ze względu na współdziałanie, a w takich przypadkach są odpowiednie wskaźniki.  
  
 **✓ DO** alternatywą dla żadnego członka, który przyjmuje argument wskaźnika, ponieważ wskaźniki nie są zgodne ze specyfikacją CLS.  
  
 **X AVOID** ten argument kosztowne sprawdzanie argumentów wskaźnika.  
  
 **✓ DO** zgodne z konwencjami typowe powiązane wskaźnika podczas projektowania elementy członkowskie ze wskaźnikiem.  
  
 Na przykład nie ma potrzeby przekazywania indeksu początkowego, ponieważ można użyć prostej arytmetycznej wskaźnika, aby osiągnąć ten sam wynik.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
