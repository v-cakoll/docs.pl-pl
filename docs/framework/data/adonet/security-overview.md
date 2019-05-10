---
title: Overview2 zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: 4960959dfe6f485a96d29a5da43c2b8c6c98fe3a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649601"
---
# <a name="security-overview"></a>Przegląd zabezpieczeń
Zabezpieczanie aplikacji jest procesem stałym. Nigdy nie będzie punktu, w której deweloper może zagwarantować, czy aplikacja jest bezpieczne przed atakami wszystkich, ponieważ nie jest możliwe do przewidzenia, jakie rodzaje nowe technologie atakom w przyszłości nastąpi. Z drugiej strony po prostu, ponieważ nikt nie ma luki w zabezpieczeniach jeszcze odnalezionych (lub opublikowany) w systemie nie oznacza brak istnieje, lub może istnieć. Należy Planowanie zabezpieczeń w fazie projektowania projektu, a także zaplanować, jak zabezpieczenia zostaną zachowane w okresie istnienia aplikacji.  
  
## <a name="design-for-security"></a>Projektowanie pod kątem zabezpieczeń  
 Jedną z największych problemów w projektowania bezpiecznych aplikacji jest zabezpieczeń często wymaga tylko chwili namysłu, coś do zaimplementowania po ukończenia kodu projektu. Nie tworzenia zabezpieczeń do aplikacji na początku prowadzi do niezabezpieczonej aplikacji, ponieważ nieco myślenia dostarczono co sprawia, że aplikacja bezpieczne.  
  
 Implementacja zabezpieczeń ostatniej minuty prowadzi do liczby błędów, jak oprogramowanie przerwy w obszarze nowe ograniczenia lub ma zostać przepisane, aby pomieścić funkcje nieprzewidziane. Każdy wiersz poprawiony kod zawiera możliwość wprowadzenia nowych usterek. Z tego powodu należy rozważyć bezpieczeństwo wcześnie w procesie tworzenia aplikacji, dzięki czemu będzie możliwe jej wraz z rozwojem nowych funkcji.  
  
### <a name="threat-modeling"></a>Modelowanie zagrożeń  
 Nie można chronić system przed atakiem, chyba że rozumiesz, które jest narażony na wypadek potencjalnych ataków. Proces oceny zagrożeń bezpieczeństwa, nazywany *modelowanie zagrożeń*, konieczne jest określenie prawdopodobieństwo i konsekwencje naruszenia zabezpieczeń w aplikacji ADO.NET.  
  
 Modelowanie zagrożeń składa się z trzech kroków wysokiego poziomu: opis widoku osoby atakującej, charakteryzujące zabezpieczeń systemu i określanie zagrożenia.  
  
 Modelowanie zagrożeń to iteracyjne podejście do oceny luk w zabezpieczeniach w aplikacji, aby znaleźć te, które są najbardziej niebezpieczne, ponieważ eksponowanie najbardziej poufnych danych. Po zidentyfikowaniu luk w zabezpieczeniach, ustaw ich pozycję w kolejności ważności i utworzyć priorytetami zestaw środków zaradczych licznik zagrożenia.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Modelowania zagrożeń](https://go.microsoft.com/fwlink/?LinkId=98353) w witrynie Centrum deweloperów zabezpieczeń w witrynie MSDN|Zasoby na tej stronie pomoże Ci zrozumieć zagrożeń procesu modelowania i twórz modele zagrożeń, które można użyć, aby zabezpieczyć swoje własne aplikacje|  
  
## <a name="the-principle-of-least-privilege"></a>Zasadę najmniejszych uprawnień  
 Przy projektowaniu, tworzeniu i wdrażania aplikacji należy zakładać, że aplikacja będzie ataku. Często te ataki jest opracowywane przez złośliwy kod, który jest wykonywany przy użyciu uprawnień użytkownika, uruchamiając kod. Inne mogą pochodzić z intencjami kodem, który ma zostać wykorzystana przez osobę atakującą. Podczas planowania zabezpieczeń należy zawsze przyjęto założenie, że nastąpi scenariuszu najgorszego przypadku.  
  
 Jeden środki zaradcze, które można stosować jest próba ustawienie tyle ściany w całym kodzie jak to możliwe, uruchamiając za pomocą najniższych uprawnień. Zasadę najmniejszych uprawnień mówi, że dany uprawnienia, może być przyznany elementowi najmniejszą ilością kodu, które są niezbędne do najkrótszy czas wymagany do swoją pracę.  
  
 Najlepsze rozwiązanie w przypadku tworzenia bezpiecznych aplikacji ma rozpoczynać się w ogóle nie ma uprawnień, a następnie dodać najwęższego uprawnienia do danego zadania wykonywane. Z drugiej strony począwszy od wszystkich uprawnień, a następnie odmawianie pojedyncze pliki prowadzi do niezabezpieczone aplikacje, które są trudne do testowania i obsługi, ponieważ luk w zabezpieczeniach może istnieć przypadkowo udzielanie więcej uprawnień niż jest to wymagane.  
  
 Aby uzyskać więcej informacji na temat zabezpieczenia aplikacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczanie aplikacji](/visualstudio/ide/securing-applications)|Zawiera łącza do tematów ogólnych zabezpieczeń. Zawiera także łącza do tematów dotyczące zabezpieczania aplikacji rozproszonych, aplikacji sieci Web, aplikacji mobilnych i klasycznych.|  
  
## <a name="code-access-security-cas"></a>Zabezpieczenia dostępu kodu (CAS)  
 Zabezpieczenia dostępu kodu (CAS) to mechanizm, który pomaga ograniczać dostęp do tego kodu do chronionych zasobów i operacji. W .NET Framework urzędy certyfikacji pełni następujące funkcje:  
  
- Definiuje uprawnienia i zestawów uprawnień, które reprezentuje prawo dostępu do różnych zasobów systemowych.  
  
- Umożliwia administratorom konfigurowanie zasad zabezpieczeń, kojarząc zestawy uprawnień przy użyciu grup kodu (grup kodu).  
  
- Umożliwia kodu zażądać uprawnień wymaga, aby można było uruchomić, a także uprawnienia, które będą mieć i określa kod nigdy nie musi mieć uprawnienia.  
  
- Przyznaje uprawnienia do każdego zestawu, który jest ładowany, na podstawie uprawnień żądany przez kod, a operacje dozwolone przez zasady zabezpieczeń.  
  
- Umożliwia kodu zapotrzebowania, że elementy go wywołujące pod ma określone uprawnienia.  
  
- Umożliwia kodu zapotrzebowania, że elementy go wywołujące pod posiadają podpis cyfrowy, dzięki czemu tylko obiekty wywołujące z konkretnej organizacji lub witryny do wywołania chronionego kodu.  
  
- Wymusza ograniczenia dotyczące kodu w czasie wykonywania, porównując udzielone uprawnienia co obiekt wywołujący na stosie wywołań do uprawnień, które musi zawierać obiekty wywołujące.  
  
 Aby zminimalizować ilość uszkodzeń, które mogą wystąpić, jeśli udany atak, wybierz kontekst zabezpieczeń dla tego kodu, która udziela dostępu tylko do zasobów, serwer musi pobrać swoją pracę, gotowe i nie ma więcej.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczenia dostępu kodu i ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)|W tym artykule opisano interakcje między zabezpieczenia dostępu kodu, zabezpieczenia oparte na rolach i środowisk częściowo zaufanym z perspektywy aplikacji ADO.NET.|  
|[Zabezpieczenia dostępu kodu](../../../../docs/framework/misc/code-access-security.md)|Zawiera łącza do dodatkowych tematów opisujących urzędów certyfikacji w programie .NET Framework.|  
  
## <a name="database-security"></a>Zabezpieczenia bazy danych  
 Zasadę najmniejszych uprawnień ma zastosowanie także do źródła danych. Ogólne wskazówki dotyczące zabezpieczeń bazy danych obejmują:  
  
- Tworzenie kont przy najniższe możliwe uprawnienia.  
  
- Nie zezwalaj użytkownikom dostęp do konta z uprawnieniami administracyjnymi tak, aby rozpocząć pracę z kodem.  
  
- Nie zwracają komunikatów o błędach po stronie serwera dla aplikacji klienckich.  
  
- Sprawdź wszystkie dane wejściowe zarówno klient, jak i serwera.  
  
- Za pomocą sparametryzowanych poleceń i uniknąć dynamicznych instrukcji SQL.  
  
- Włącz zabezpieczenia inspekcji i rejestrowania dla bazy danych używane w tak, że alerty są wyzwalane na wszelkie naruszenia zabezpieczeń.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)|Omówienie zabezpieczeń programu SQL Server przy użyciu scenariuszy aplikacji, które zawierają wskazówki dotyczące tworzenia bezpiecznych aplikacji ADO.NET, których obiektem docelowym programu SQL Server.|  
|[Zalecenia dotyczące strategii dostępu do danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Zawiera zalecenia dotyczące uzyskiwania dostępu do danych i wykonywania operacji w bazie danych.|  
  
## <a name="security-policy-and-administration"></a>Zasady zabezpieczeń i administracji  
 Nieprawidłowo administrowania zasady zabezpieczenia dostępu kodu może utworzyć luk zabezpieczeń. Po wdrożeniu aplikacji powinny być używane techniki monitorowanie zabezpieczeń i wyłaniać ryzyko oceniane jako nowe zagrożenia.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zarządzanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))|Zawiera informacje na temat tworzenia i administrowanie zasadami zabezpieczeń.|  
|[Najlepsze rozwiązania dotyczące zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))|Zawiera łącza, dotyczące administrowania zasadami zabezpieczeń.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Zabezpieczenia w .NET](../../../standard/security/index.md)
- [Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
