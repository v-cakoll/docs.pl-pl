---
title: Projekt parametrów
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea5311de8cef266af23b259d943568bfa95eaf72
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615079"
---
# <a name="parameter-design"></a>Projekt parametrów
Ta sekcja zawiera parametr projektu, w tym sekcje z wytycznymi dotyczącymi sprawdzania argumentów ogólnych wytycznych. Ponadto należy zapoznać się z wytycznymi opisany w [parametry nazwy](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ DO** używany najmniej pochodnej typ parametru, który udostępnia funkcje wymagane przez element członkowski.  
  
 Na przykład załóżmy, że chcesz zaprojektować metodę, która wylicza kolekcji i drukuje każdy element do konsoli. Taka metoda powinno zająć <xref:System.Collections.IEnumerable> jako parametr, nie <xref:System.Collections.ArrayList> lub <xref:System.Collections.IList>, na przykład.  
  
 **X DO NOT** parametry zastrzeżone.  
  
 W razie potrzeby więcej danych wejściowych do elementu członkowskiego jest niektóre przyszłej wersji, można dodać też nowym przeciążeniem.  
  
 **X DO NOT** zostały publicznie udostępnione metod, które przyjmują wskaźników, tablic wskaźników lub wielowymiarowych tablic jako parametrów.  
  
 Wskaźniki i tablice wielowymiarowe są stosunkowo trudne prawidłowo. W większości przypadków interfejsów API można przeprojektowane, aby uniknąć tworzenia tych typów jako parametrów.  
  
 **✓ DO** Umieść wszystkie `out` po całej przez wartości parametrów i `ref` parametrów (z wyłączeniem tablice parametrów), nawet jeśli powoduje niespójność w parametrze kolejności między przeciążenia (zobacz [elementu członkowskiego Przeciążanie](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 `out` Parametry są widoczne jako wartości zwracane dodatkowych i grupując je razem sprawia, że podpis metody łatwiejsze do zrozumienia.  
  
 **✓ DO** zachować spójność nazw parametrów, gdy zastępowanie elementów członkowskich lub wykonania członków interfejsu.  
  
 To lepiej komunikuje się relacji między metodami.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Wybieranie między logiczna parametry i wyliczenia  
 **✓ DO** Użyj wyliczenia, jeśli element członkowski w przeciwnym razie byłyby dwóch lub więcej parametrów Boolean.  
  
 **X DO NOT** Użyj wartości logiczne, jeśli nie masz pewności absolutnie nigdy nie będą potrzeba więcej niż dwóch wartości.  
  
 Typy wyliczeniowe umożliwiają trochę miejsca dla przyszłych dodanie wartości, ale należy pamiętać o wszystkie implikacje dodawanie wartości do wyliczenia, które są opisane w [projekt wyliczeń](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ CONSIDER** przy użyciu wartości logiczne są naprawdę dwustanowy wartości, które są używane do zainicjowania właściwości logicznych parametrów konstruktora.  
  
### <a name="validating-arguments"></a>Sprawdzanie poprawności argumentów  
 **✓ DO** Waliduj Argumenty przekazane do publicznych, chronionych lub jawnie implementowane elementy członkowskie. Throw <xref:System.ArgumentException?displayProperty=nameWithType>, lub jednej z podklas, jeśli weryfikacja zakończy się niepowodzeniem.  
  
 Pamiętaj, że rzeczywista weryfikacja nie musi być w publiczny lub chroniony sam element członkowski. Może się zdarzyć na niższym poziomie w procedurze, niektóre prywatne lub wewnętrzne. Główną kwestią jest, że cały obszar powierzchni, która jest widoczna dla użytkowników końcowych sprawdza, czy argumenty.  
  
 **✓ DO** throw <xref:System.ArgumentNullException> Jeśli argument o wartości null została przekazana i element członkowski nie obsługuje wartości null argumentów.  
  
 **✓ DO** sprawdza poprawność parametrów wyliczenia.  
  
 Nie zakłada, że argumenty wyliczenia w zakresie zdefiniowanych przez wyliczenie. Środowisko CLR umożliwia rzutowanie dowolnej wartości liczby całkowitej do wyliczenia wartości, nawet jeśli wartość nie jest zdefiniowany w typie wyliczeniowym.  
  
 **X DO NOT** użyj <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> dla wyliczenia zakresu kontroli.  
  
 **✓ DO** należy pamiętać, że argumenty modyfikowalną mogła ulec zmianie po ich została sprawdzona.  
  
 Jeśli element jest zabezpieczenia poufnych, zachęcamy do skopiowania, a następnie sprawdź poprawność i przetworzyć argumentu.  
  
### <a name="parameter-passing"></a>Przekazywanie parametru  
 Z punktu widzenia projektanta framework istnieją trzy główne grupy parametrów: parametry, przez wartość `ref` parametrów i `out` parametrów.  
  
 Gdy argument jest przekazywane przez wartość parametru, elementu członkowskiego otrzymuje kopię rzeczywisty argument przekazywany w. Jeśli argument jest typem wartości, Kopia argumentu jest umieszczany na stosie. Jeśli argument jest typem referencyjnym, kopię odwołanie zostanie przełączone na stosie. Najbardziej popularnych języków CLR, takich jak C#, VB.NET i C++, domyślne do przekazywania parametrów przez wartość.  
  
 Gdy argument jest przekazywany za pośrednictwem `ref` parametru, elementu członkowskiego otrzymuje odwołanie do rzeczywisty argument przekazywany w. Jeśli argument jest typem wartości, odwołanie do argumentu jest umieszczany na stosie. Jeśli argument jest typem referencyjnym, odwołanie do odwołania jest umieszczany na stosie. `Ref` można użyć parametrów, aby umożliwić elementu członkowskiego zmodyfikować Argumenty przekazane przez obiekt wywołujący.  
  
 `Out` Parametry są podobne do `ref` parametrów, za pomocą niewielkie różnice. Parametr uważa się początkowo nieprzypisane i nie można odczytać treści elementu członkowskiego, przed przypisaniem jakąś wartość. Ponadto parametr musi zostać przypisany jakąś wartość, zanim zwraca element członkowski.  
  
 **X AVOID** przy użyciu `out` lub `ref` parametrów.  
  
 Za pomocą `out` lub `ref` parametrów wymaga doświadczenia w zakresie wskaźników, zrozumienie, jak różnią się typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Ponadto różnica między `out` i `ref` parametrów nie jest powszechnie zrozumiała. Architekci Framework projektowania dla wszystkich użytkowników nie powinni oczekiwać od użytkowników do wzorca pracę z `out` lub `ref` parametrów.  
  
 **X DO NOT** przekazuj typów referencyjnych przez odwołanie.  
  
 Istnieją pewne ograniczony zakres wyjątków reguły, takie jak metody, która może służyć do wymiany odwołania.  
  
### <a name="members-with-variable-number-of-parameters"></a>Elementy członkowskie o zmienną liczbę parametrów  
 Elementy członkowskie, które może potrwać zmienną liczbę argumentów są wyrażane, podając parametr tablicy. Na przykład <xref:System.String> udostępnia następujące metody:  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Użytkownik może wywoływać <xref:System.String.Format%2A?displayProperty=nameWithType> metody w następujący sposób:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Dodawanie słowa kluczowego params C# do parametr tablicowy zmiany parametru parametru params tak zwane tablicy i zapewnia skrót do tworzenia tablicy tymczasowej.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 W ten sposób umożliwia użytkownikowi wywołania metody przez przekazanie elementów tablicy bezpośrednio na liście argumentów.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Należy pamiętać, że słowa kluczowego params można dodać tylko do ostatniego parametru na liście parametrów.  
  
 **✓ CONSIDER** Dodawanie params — słowo kluczowe do tablicy parametrów, Jeśli przypuszczasz, użytkownikom końcowym przekazać tablice o niewielkiej liczby elementów. Jeśli oczekuje się, że wiele elementów zostaną przekazane w typowych scenariuszy, użytkownicy mimo to prawdopodobnie nie przejdzie tych wbudowanych elementów, a więc słowa kluczowego params nie jest konieczne.  
  
 **X AVOID** przy użyciu tablic parametrów, jeśli element wywołujący prawie zawsze musi danych wejściowych już w tablicy.  
  
 Na przykład elementy członkowskie z parametrami tablicy bajtów prawie nigdy nie będzie wywoływana przez przekazanie pojedynczych bajtów. Z tego powodu parametry tablicy bajtów w .NET Framework nie należy używać słowa kluczowego params.  
  
 **X DO NOT** Użycie tablic parametrów, jeśli tablica jest modyfikowany przez element członkowski, biorąc parametru params tablicy.  
  
 Ze względu na fakt, że wiele kompilatorów przekształcając argumenty do elementu członkowskiego tablicy tymczasowej, w witrynie wywołania tablicy może być obiektem tymczasowym, a zatem wszelkie zmiany w tablicy zostaną utracone.  
  
 **✓ CONSIDER** przy użyciu słowa kluczowego params w prosty przeciążenia, nawet w przypadku bardziej złożonych przeciążenia nie można użyć.  
  
 Zadaj sobie, jeśli użytkownicy będą wartość mających tablicą parametrów w jednego przeciążenia, nawet jeśli te informacje nie były w wszystkie przeciążenia.  
  
 **✓ DO** próby kolejność parametrów umożliwiają użyj słowa kluczowego params.  
  
 **✓ CONSIDER** zapewnienie przeciążeń szczególne i ścieżki kodu dla wywołania z niewielką liczbę argumentów w bardzo ważnych wydajności interfejsów API.  
  
 Dzięki temu można uniknąć tworzenia tablicy obiektów po wywołaniu interfejsu API z niewielką liczbę argumentów. Forma nazwy parametrów przez pobranie pojedynczej formie parametr tablicowy i dodanie sufiksu liczbowego.  
  
 Tylko należy to zrobić, jeśli ma szczególny ścieżkę całego kodu, nie tylko utworzyć tablicę i wywołać metodę bardziej ogólnych.  
  
 **✓ DO** należy pamiętać, że null można przekazany jako argument tablicy parametrów.  
  
 Należy sprawdzić, czy tablica nie jest null, przed rozpoczęciem przetwarzania.  
  
 **X DO NOT** użyj `varargs` metod, znanej także jako wielokropka.  
  
 Niektóre języki CLR, takich jak C++, obsługa alternatywnych Konwencji przekazywania list parametrów zmiennych, o nazwie `varargs` metody. Konwencja nie stosuje się w struktur, ponieważ nie jest zgodny ze specyfikacją CLS.  
  
### <a name="pointer-parameters"></a>Parametry wskaźnika  
 Ogólnie rzecz biorąc wskaźniki nie powinny być wyświetlane w obszarze powierzchni publicznych Framework dobrze zaprojektowanego kodu zarządzanego. W większości przypadków, powinien hermetyzowany wskaźników. Jednak w niektórych przypadkach wskaźniki są wymagane do współdziałania powodów i za pomocą wskaźników w takich przypadkach jest odpowiednia.  
  
 **✓ DO** alternatywą dla żadnego członka, który przyjmuje argument wskaźnika, ponieważ wskaźniki nie są zgodne ze specyfikacją CLS.  
  
 **X AVOID** ten argument kosztowne sprawdzanie argumentów wskaźnika.  
  
 **✓ DO** zgodne z konwencjami typowe powiązane wskaźnika podczas projektowania elementy członkowskie ze wskaźnikiem.  
  
 Na przykład nie ma potrzeby do przekazania indeksu początkowego, ponieważ proste arytmetyka wskaźnika można osiągnąć ten sam wynik.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
