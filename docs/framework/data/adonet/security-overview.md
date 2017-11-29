---
title: "Overview2 zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d7288eeffeb642d1e897e11153802633d71747bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="security-overview"></a>Przegląd zabezpieczeń
Zabezpieczanie aplikacji jest ciągły proces. Nigdy nie będą punktu, w którym deweloper może zagwarantować, czy aplikacja jest bezpieczne przed atakami wszystkich, ponieważ nie jest możliwe do przewidzenia, jakie rodzaje ataków w przyszłości nowych technologii nastąpi. Z drugiej strony tak, ponieważ nikt nie ma luki w zabezpieczeniach jeszcze odnalezionych (lub opublikowany) w systemie nie oznacza brak istnieje, lub mogą istnieć. Musisz planowaniu zabezpieczeń w fazie projektowania projektu, a także zaplanować, jak zabezpieczeń będzie przechowywany w okresie istnienia aplikacji.  
  
## <a name="design-for-security"></a>Projektowanie pod kątem zabezpieczeń  
 Jedną z największych problemów w tworzeniu aplikacji bezpiecznego jest zabezpieczeń często zbagatelizowane, coś do wykonania po wykonać kod projektu. Nie budowania zabezpieczeń do aplikacji na początku prowadzi do niezabezpieczonych aplikacji, ponieważ małego myśl dostarczono co sprawia, że aplikacja bezpieczne.  
  
 Implementacji zabezpieczeń ostatniej minuty prowadzi do usterki więcej jako podziały oprogramowania w obszarze nowe ograniczenia lub ma do ponownego napisania do uwzględnienia nieprzewidziane funkcji. Każdy wiersz kodu poprawione zawiera możliwość wprowadzenia nowych usterek. Z tego powodu należy rozważyć zabezpieczeń wczesnym etapie projektowania, aby móc kontynuować wraz z rozwojem nowych funkcji.  
  
### <a name="threat-modeling"></a>Modelowanie zagrożeń  
 Nie można chronić systemu przed atakiem bez zrozumienia wszystkich potencjalnych ataków, które jest narażony na. Proces oceny zagrożeń bezpieczeństwa, nazywany *modelowanie zagrożeń*, konieczne jest określenie prawdopodobieństwo i konsekwencje naruszeń zabezpieczeń w aplikacji ADO.NET.  
  
 Modelowanie zagrożeń składa się z trzech kroków ogólnych: opis widoku atakujący dokonuje, charakteryzujące zabezpieczeń systemu i określania zagrożeń.  
  
 Modelowanie zagrożeń jest metody iteracyjnej do oceny luk w zabezpieczeniach w aplikacji, aby znaleźć te, które są najbardziej niebezpieczne, ponieważ udostępniają najbardziej poufnych danych. Po zidentyfikowaniu luk w zabezpieczeniach rank je w kolejności ważności i utworzyć zbiór priorytetową środków zaradczych liczników zagrożenia.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Modelowania zagrożeń](http://go.microsoft.com/fwlink/?LinkId=98353) w witrynie MSDN w Centrum deweloperów zabezpieczeń|Zasoby na tej stronie pomoże Ci zrozumieć procesu modelowania zagrożeń i tworzenie modeli zagrożenia, które służy do zabezpieczania własnych aplikacji|  
  
## <a name="the-principle-of-least-privilege"></a>Zasadą najniższych uprawnień  
 Podczas projektowania, tworzenie i wdrażanie aplikacji musi założono, że aplikacja będzie ataku. Często ataki pochodzą z złośliwy kod, który wykonuje z uprawnieniami użytkownika uruchamiającego kod. Inne osoby mogą pochodzących z dobrze tych kod, który ma zostać wykorzystana przez osobę atakującą. Podczas planowania zabezpieczeń należy zawsze przyjęto założenie, że nastąpi najgorszym przypadku.  
  
 Jeden środki zaradcze, które można stosować jest próba ustawienie tyle ściany wokół kodu jak to możliwe, uruchamiając o najniższych uprawnień. Zasadą najniższych uprawnień mówi, że danego uprawnienia, może być przyznany elementowi minimalnej liczbie kodu niezbędne najkrótszy czas trwania czas, jaki trzeba wykonać zadanie.  
  
 Najlepsze rozwiązanie dotyczące tworzenia aplikacji bezpiecznego ma rozpoczynać się w ogóle nie ma uprawnień, a następnie dodaj najwęższym uprawnienia dla określonego zadania wykonywane. Z kolei następnie odrzuciła pojedyncze pliki, począwszy od wszystkie uprawnienia prowadzi do niebezpieczne aplikacje, które są trudne do testowania i obsługi, ponieważ luk w zabezpieczeniach, może istnieć w niezamierzony sposób udzielania więcej uprawnień niż jest to wymagane.  
  
 Aby uzyskać więcej informacji na temat zabezpieczenia aplikacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczanie aplikacji](/visualstudio/ide/securing-applications)|Zawiera linki do tematów dotyczących zabezpieczeń. Zawiera również linki do tematów do zabezpieczania aplikacji rozproszonych, aplikacji sieci Web, aplikacji mobilnych i klasycznych.|  
  
## <a name="code-access-security-cas"></a>Zabezpieczenia dostępu kodu (CAS)  
 Zabezpieczenia dostępu kodu (CAS) jest mechanizm, który pomaga ograniczyć dostępu kodu do chronionych zasobów i operacji. W programie .NET Framework urzędy certyfikacji wykonuje następujące funkcje:  
  
-   Definiuje uprawnienia i zestawów uprawnień, które reprezentują prawa dostępu różnych zasobów systemowych.  
  
-   Umożliwia administratorom konfigurowanie zasad zabezpieczeń z grupami kodu (grup kodów) można skojarzyć zestawów uprawnień.  
  
-   Włącza kod, aby zażądać uprawnień wymaga, aby można było uruchomić, a także uprawnienia, które będą mieć i określa uprawnienia, które nigdy nie są wymagane kod.  
  
-   Przyznaje uprawnienia do każdego zestawu, który jest ładowany, na podstawie uprawnień wymaganych przez kod i na operacje dozwolone przez zasady zabezpieczeń.  
  
-   Umożliwia kodu na żądanie, że elementy wywołujące pod ma określone uprawnienia.  
  
-   Umożliwia kodu na żądanie, aby elementy wywołujące pod posiadał podpisu cyfrowego, dzięki czemu tylko wywołującym z organizacji lub witryny wywoływać kod chronionych.  
  
-   Wymusza ograniczenia dotyczące kodu w czasie wykonywania na podstawie porównania ilości uprawnienia nadanego co wywołujący na stosie wywołań w celu wywoływania musi mieć uprawnienia.  
  
 Aby zminimalizować ilość uszkodzeń, które mogą wystąpić, jeśli atak zakończy się pomyślnie, należy wybrać kontekst zabezpieczeń dla tego kodu, która udziela dostępu tylko do zasobów, serwer musi pobrać jego pracy gotowe i nie więcej.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczenia dostępu kodu i ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)|W tym artykule opisano interakcje między zabezpieczenia dostępu kodu, na podstawie ról zabezpieczeń i środowisk częściowo zaufany z perspektywy aplikacji ADO.NET.|  
|[Zabezpieczenia dostępu kodu](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)|Zawiera łącza do dodatkowych tematów opisujących urzędów certyfikacji w programie .NET Framework.|  
  
## <a name="database-security"></a>Zabezpieczenia bazy danych  
 Zasadą najniższych uprawnień ma również zastosowanie do źródła danych. Zawiera ogólne wskazówki dotyczące zabezpieczeń bazy danych:  
  
-   Utwórz konta z najmniejsze możliwe uprawnienia.  
  
-   Nie zezwalaj użytkownikom dostęp do konta z uprawnieniami administracyjnymi tak, aby działało kodu.  
  
-   Zwraca komunikaty po stronie serwera dla aplikacji klienckich.  
  
-   Zweryfikuj wszystkie dane wejściowe zarówno klient, jak i serwera.  
  
-   Używaj sparametryzowanych poleceń, a dynamicznych instrukcji SQL.  
  
-   Włącz zabezpieczenie inspekcji i rejestrowania dla bazy danych używanej tak, aby alert wszelkie naruszenia zabezpieczeń.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)|Przegląd zabezpieczeń programu SQL Server z scenariuszy aplikacji, które zawierają wskazówki dotyczące tworzenia bezpiecznych aplikacji ADO.NET obiektu docelowego programu SQL Server.|  
|[Zalecenia dotyczące strategii dostępu do danych](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)|Zawiera zalecenia dotyczące uzyskiwania dostępu do danych i wykonywanie operacji bazy danych.|  
  
## <a name="security-policy-and-administration"></a>Zasady zabezpieczeń i administracji  
 Nieprawidłowo administrowania zasadami zabezpieczeń (CAS) dostępu do kodu może utworzyć słabych zabezpieczeń. Po wdrożeniu aplikacji technik w celu monitorowania zabezpieczeń powinien być używany, a wyłonić ryzyka ocenione jako nowych zagrożeń.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[NIB: Zarządzanie zasadami dotyczącymi zabezpieczeń](http://msdn.microsoft.com/en-us/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9)|Zawiera informacje na temat tworzenia i administrowanie zasadami zabezpieczeń.|  
|[NIB: Najlepsze rozwiązania zasad zabezpieczeń](http://msdn.microsoft.com/en-us/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05)|Łącza dotyczące administrowania zasadami zabezpieczeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Pave – zabezpieczeń w trybie macierzystym i kodu platformy .NET Framework](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784)  
 [Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
