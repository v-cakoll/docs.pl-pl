---
title: Parametr projektu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f95301bab57e8bdb6b22c54140a4c02ed208b8d3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="parameter-design"></a>Parametr projektu
Ta sekcja zawiera ogólnych wytycznych w projekcie parametru, w tym sekcje z wytycznymi dotyczącymi sprawdzanie argumentów. Ponadto należy zapoznać się z wytycznymi opisanego w [nazw parametrów](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **CZY ✓** używany najmniej pochodnej typ parametru, który udostępnia funkcje wymagane przez element członkowski.  
  
 Na przykład załóżmy, że chcesz projektowania metodę, która wylicza kolekcji i drukuje każdego elementu w konsoli. Taka metoda powinno zająć <xref:System.Collections.IEnumerable> jako parametr, nie <xref:System.Collections.ArrayList> lub <xref:System.Collections.IList>, np.  
  
 **X nie** parametry zastrzeżone.  
  
 Jeśli wymagane jest więcej danych wejściowych do elementu członkowskiego w niektórych przyszłych wersji, można dodać nowego przeciążenia.  
  
 **X nie** zostały publicznie udostępnione metod, które przyjmują wskaźników, tablic wskaźników lub wielowymiarowych tablic jako parametrów.  
  
 Wskaźników oraz tablic wielowymiarowych są stosunkowo trudny do wykorzystania poprawnie. W większości przypadków interfejsy API można przeprojektowany tak, aby uniknąć wykonywania tych typów jako parametry.  
  
 **CZY ✓** Umieść wszystkie `out` po całej przez wartości parametrów i `ref` parametrów (z wyłączeniem tablice parametrów), nawet jeśli powoduje niespójność w parametrze kolejności między przeciążenia (zobacz [elementu członkowskiego Przeciążanie](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 `out` Parametry są widoczne jako wartości zwracane bardzo i zgrupowanie ułatwia zrozumienie podpis metody.  
  
 **CZY ✓** zachować spójność nazw parametrów, gdy zastępowanie elementów członkowskich lub wykonania członków interfejsu.  
  
 To lepiej komunikuje się relacji między metodami.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Wybór między logiczna parametry i wyliczenia  
 **CZY ✓** Użyj wyliczenia, jeśli element członkowski w przeciwnym razie byłyby dwóch lub więcej parametrów Boolean.  
  
 **X nie** Użyj wartości logiczne, jeśli nie masz pewności absolutnie nigdy nie będą potrzeba więcej niż dwóch wartości.  
  
 Typy wyliczeniowe zapewniają niektóre miejsca dla przyszłych dodanie wartości, ale należy zwrócić uwagę wszystkie efekty dodawania wartości do wyliczenia, które zostały opisane w [projektu wyliczenia](../../../docs/standard/design-guidelines/enum.md).  
  
 **ROZWAŻ ✓** przy użyciu wartości logiczne są naprawdę dwustanowy wartości, które są używane do zainicjowania właściwości logicznych parametrów konstruktora.  
  
### <a name="validating-arguments"></a>Sprawdzanie poprawności argumentów  
 **CZY ✓** Waliduj Argumenty przekazane do publicznych, chronionych lub jawnie implementowane elementy członkowskie. Throw <xref:System.ArgumentException?displayProperty=nameWithType>, lub jeden z jego podklas, w przypadku niepowodzenia weryfikacji.  
  
 Należy pamiętać, że rzeczywista weryfikacja nie musi być w public lub protected członkowski. Może się zdarzyć na niższym poziomie w niektórych procedury prywatny lub wewnętrzny. Główny punkt znajduje się sprawdza, czy cały powierzchni, która jest widoczna dla użytkowników końcowych argumentów.  
  
 **CZY ✓** throw <xref:System.ArgumentNullException> Jeśli argument o wartości null została przekazana i element członkowski nie obsługuje wartości null argumentów.  
  
 **CZY ✓** sprawdza poprawność parametrów wyliczenia.  
  
 Nie przyjęto założenie, że będzie argumenty wyliczenia w zakresie zdefiniowanych przez wyliczenie. Środowisko CLR umożliwia rzutowania dowolną liczbą całkowitą w wartości wyliczenia, nawet jeśli wartość nie jest zdefiniowany w elemencie enum.  
  
 **X nie** użyj <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> dla wyliczenia zakresu kontroli.  
  
 **CZY ✓** należy pamiętać, że argumenty modyfikowalną mogła ulec zmianie po ich została sprawdzona.  
  
 Jeśli element członkowski jest bezpieczeństwa poufnych, zachęca się do skopiowania, a następnie sprawdź poprawność i przetwarzać argumentu.  
  
### <a name="parameter-passing"></a>Przekazywanie parametru  
 Z punktu widzenia projektanta framework, istnieją trzy główne grupy parametrów: parametry, przez wartość `ref` parametry, i `out` parametrów.  
  
 Gdy argument jest przekazywany za pomocą parametru-wartość, element członkowski wysyłana kopia rzeczywisty argument przekazany. Jeśli argument ma typ wartości, kopię argumentu jest umieszczany na stosie. Jeśli argument ma typ referencyjny, kopię odwołanie jest umieszczany na stosie. Najbardziej popularnych języków CLR, takich jak C#, VB.NET i C++, domyślnie przekazywanie parametrów przez wartość.  
  
 Gdy argument jest przekazywany za pośrednictwem `ref` parametru odbiera element członkowski odwołania do rzeczywistego przekazany argument. Jeśli argument ma typ wartości, odwołanie do argumentu jest umieszczany na stosie. Jeśli argument ma typ referencyjny, odwołanie do odwołania jest umieszczany na stosie. `Ref`Aby umożliwić elementu członkowskiego do argumenty przekazany przez wywołującego można użyć parametrów.  
  
 `Out`Parametry są podobne do `ref` parametrów, z niektórych niewielkie różnice. Parametr uważa się początkowo nieprzypisane i nie można odczytać treści elementu członkowskiego, przed przypisaniem niektóre wartości. Ponadto parametr musi zostać przypisany niektóre wartości, zanim zwraca element członkowski.  
  
 **X należy UNIKAĆ** przy użyciu `out` lub `ref` parametrów.  
  
 Przy użyciu `out` lub `ref` środowisko z wskaźników, zrozumienie, jak są różne typy wartości i typy referencyjne i obsługi metod zawierających wiele wartości zwrotnych wymaga parametrów. Ponadto to różnica między `out` i `ref` parametry powszechnie jest niezrozumiały. Architektów Framework projektowania dla wszystkich użytkowników nie oczekiwać użytkownikom pracy wzorca z `out` lub `ref` parametrów.  
  
 **X nie** przekazuj typów referencyjnych przez odwołanie.  
  
 Brak niektórych ograniczone wyjątki w regule, na przykład metodę, która może służyć do wymiany odwołań.  
  
### <a name="members-with-variable-number-of-parameters"></a>Elementy członkowskie o zmiennej liczbie parametrów  
 Elementy członkowskie, które można wykonać zmienna liczba argumentów są wyrażane podając parametr tablicy. Na przykład <xref:System.String> udostępnia następujące metody:  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Użytkownik może wywoływać <xref:System.String.Format%2A?displayProperty=nameWithType> metody, w następujący sposób:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Dodawanie słowa kluczowego params C# do parametru tablicy zmiany parametru parametru params tak zwane tablicy i zapewnia skrót do utworzenia tablicy tymczasowej.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 W ten sposób umożliwia użytkownikowi Wywołaj metodę przez przekazanie elementów tablicy bezpośrednio na liście argumentów.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Należy pamiętać, że słowa kluczowego params można dodać tylko do ostatniego parametru na liście parametrów.  
  
 **ROZWAŻ ✓** Dodawanie params — słowo kluczowe do tablicy parametrów, Jeśli przypuszczasz, użytkownikom końcowym przekazać tablice o niewielkiej liczby elementów. Jeśli oczekuje się, że wiele elementów zostaną przekazane wspólnych scenariuszy, użytkownicy mimo to prawdopodobnie nie przejdą wbudowanego tych elementów, a więc params — słowo kluczowe nie jest konieczne.  
  
 **X należy UNIKAĆ** przy użyciu tablic parametrów, jeśli element wywołujący prawie zawsze musi danych wejściowych już w tablicy.  
  
 Na przykład elementy członkowskie z parametrami tablicy bajtów prawie nigdy nie będzie można wywołać przez przekazanie poszczególnych bajtów. Z tego powodu parametrów tablicy bajtów w programie .NET Framework nie należy używać słowa kluczowego params.  
  
 **X nie** Użycie tablic parametrów, jeśli tablica jest modyfikowany przez element członkowski, biorąc parametru params tablicy.  
  
 Ze względu na fakt, że wiele kompilatorów Włącz argumenty do elementu członkowskiego do tablicy w witrynie wywołanie tablicy może być obiektem tymczasowym, a zatem wszelkie modyfikacje tablicy zostaną utracone.  
  
 **ROZWAŻ ✓** przy użyciu słowa kluczowego params w prosty przeciążenia, nawet w przypadku bardziej złożonych przeciążenia nie można użyć.  
  
 Zadaj sobie, jeśli użytkownicy będą wartości o tablicy parametrów w przeciążeniami, nawet jeśli nie był w wszystkie przeciążenia.  
  
 **CZY ✓** próby kolejność parametrów umożliwiają użyj słowa kluczowego params.  
  
 **ROZWAŻ ✓** zapewnienie przeciążeń szczególne i ścieżki kodu dla wywołania z niewielką liczbę argumentów w bardzo ważnych wydajności interfejsów API.  
  
 Dzięki temu można uniknąć tworzenia tablicy obiektów po wywołaniu interfejsu API z mniejszą liczbą argumentów. Formularz nazwy parametrów przez pobranie pojedynczej formę parametr tablicy i dodanie sufiksu liczbowego.  
  
 Tylko należy to zrobić, jeśli ma specjalne przypadku ścieżkę całego kodu, nie wystarczy utworzyć tablicy i wywołaj metodę bardziej ogólne.  
  
 **CZY ✓** należy pamiętać, że null można przekazany jako argument tablicy parametrów.  
  
 Należy sprawdzić, czy tablica nie jest pusta, przed rozpoczęciem przetwarzania.  
  
 **X nie** użyj `varargs` metod, znanej także jako wielokropka.  
  
 Niektórych języków CLR, takich jak C++, obsługa alternatywnych Konwencji przekazywanie listy parametrów zmiennej o nazwie `varargs` metody. Konwencji nie stosuje się w struktur, ponieważ nie jest zgodne ze specyfikacją CLS.  
  
### <a name="pointer-parameters"></a>Parametry wskaźnika  
 Ogólnie rzecz biorąc wskaźniki nie mogą występować w publicznej powierzchni framework dobrze zaprojektowanego kodu zarządzanego. W większości przypadków należy hermetyzowany wskaźników. Jednak w niektórych przypadkach wskaźniki są wymagane współdziałanie ze względu na i przy użyciu wskaźniki w takich przypadkach jest.  
  
 **CZY ✓** alternatywą dla żadnego członka, który przyjmuje argument wskaźnika, ponieważ wskaźniki nie są zgodne ze specyfikacją CLS.  
  
 **X należy UNIKAĆ** ten argument kosztowne sprawdzanie argumentów wskaźnika.  
  
 **CZY ✓** zgodne z konwencjami typowe powiązane wskaźnika podczas projektowania elementy członkowskie ze wskaźnikiem.  
  
 Ponieważ arytmetyka wskaźnika prostego mogą zostać użyte do wykonania takiego samego wyniku istnieje na przykład, nie trzeba przekazać indeks początkowy.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
