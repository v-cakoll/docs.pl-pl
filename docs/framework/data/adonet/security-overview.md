---
title: Overview2 zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: 4aac564e55b24b2499f861938082a32f30247f91
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794341"
---
# <a name="security-overview"></a>Przegląd zabezpieczeń
Zabezpieczanie aplikacji jest procesem ciągłym. Nie będzie to miało miejsca, w którym deweloper może zagwarantować, że aplikacja jest bezpieczna przed atakami, ponieważ nie można przewidzieć, jakie rodzaje przyszłych ataków będą się pojawiać. Z drugiej strony, ponieważ nikt nie został jeszcze odnaleziony (lub opublikowany) wady zabezpieczeń w systemie nie oznacza, że nic nie istnieje lub nie istnieje. Należy zaplanować zabezpieczenia w fazie projektowania projektu, a także zaplanować, w jaki sposób zabezpieczenia będą utrzymywane w okresie istnienia aplikacji.  
  
## <a name="design-for-security"></a>Projektowanie pod kątem zabezpieczeń  
 Jednym z największych problemów związanych z tworzeniem bezpiecznych aplikacji jest to, że bezpieczeństwo jest często zostawiać, co do wdrożenia po zakończeniu projektu. Nietworzenie zabezpieczeń w aplikacji na początku prowadzi do niezabezpieczonych aplikacji, ponieważ niektóre uwagi zostały nadane w celu zabezpieczenia aplikacji.  
  
 Ostatnia minuta implementacja zabezpieczeń prowadzi do większej liczby usterek, ponieważ przerwy w oprogramowaniu w ramach nowych ograniczeń lub należy zapisać w celu uwzględnienia nieoczekiwanych funkcji. Każdy wiersz poprawionego kodu zawiera możliwość wprowadzenia nowego błędu. Z tego powodu należy wziąć pod uwagę wczesne zabezpieczenia w procesie opracowywania, tak aby można było kontynuować opracowywanie nowych funkcji.  
  
### <a name="threat-modeling"></a>Modelowanie zagrożeń  
 Nie można chronić systemu przed atakami, chyba że zrozumiesz wszystkie potencjalne ataki, dla których jest on narażony. Proces oceny zagrożeń bezpieczeństwa zwany *modelem zagrożeń*jest konieczny do określenia prawdopodobieństwa i konsekwencji naruszeń zabezpieczeń w aplikacji ADO.NET.  
  
 Modelowanie zagrożeń składa się z trzech kroków wysokiego poziomu: zrozumienie widoku atakującej, scharakteryzowanie zabezpieczeń systemu i określanie zagrożeń.  
  
 Modelowanie zagrożeń jest iteracyjnym podejściem do oceny luk w zabezpieczeniach aplikacji, aby znaleźć te, które są najbardziej niebezpieczne, ponieważ uwidaczniają one najbardziej poufne dane. Po zidentyfikowaniu luk w zabezpieczeniach należy określić ich rangę w kolejności ważności i utworzyć priorytetowy zestaw środków zaradczych, aby wyeliminować zagrożenia.  
  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|Witryna [modelowania zagrożeń](https://go.microsoft.com/fwlink/?LinkId=98353) w witrynie MSDN Security Developer Center|Zasoby na tej stronie pomogą zrozumieć proces modelowania zagrożeń oraz modele zagrożeń kompilacji, których można użyć do zabezpieczenia własnych aplikacji|  
  
## <a name="the-principle-of-least-privilege"></a>Zasada najniższych uprawnień  
 Podczas projektowania, kompilowania i wdrażania aplikacji należy założyć, że aplikacja zostanie zaatakowana. Często te ataki pochodzą ze złośliwego kodu, który jest wykonywany z uprawnieniami użytkownika, na którym uruchomiono kod. Inne mogą pochodzić z dobrze zamierzonym kodem, który został wykorzystany przez osobę atakującą. W przypadku planowania zabezpieczeń zawsze zakłada się, że wystąpi scenariusz najgorszego przypadku.  
  
 Jedną z miar liczników, których można użyć, jest próba przewinięcia możliwie największej liczby ścian w kodzie przez uruchomienie z najniższymi uprawnieniami. Zasada najniższych uprawnień oznacza, że każde z tych uprawnień powinno być przyznane najmniejszej ilości kodu niezbędnej przez najkrótszy czas wymagany do wykonania zadania.  
  
 Najlepszym rozwiązaniem w przypadku tworzenia bezpiecznych aplikacji jest rozpoczęcie od braku uprawnień, a następnie dodanie najwęższych uprawnień dla danego wykonywanego zadania. Z drugiej strony, począwszy od wszystkich uprawnień, a następnie odmówienia poszczególnym osobom potencjalną ochronę niezabezpieczonych aplikacji, które są trudne do przetestowania i utrzymania, ponieważ luki w zabezpieczeniach mogą być niecelowo przyznawane więcej uprawnień niż jest to wymagane.  
  
 Aby uzyskać więcej informacji na temat zabezpieczania aplikacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczanie aplikacji](/visualstudio/ide/securing-applications)|Zawiera linki do ogólnych tematów zabezpieczeń. Zawiera również linki do tematów zabezpieczania aplikacji rozproszonych, aplikacji sieci Web, aplikacji mobilnych i aplikacji klasycznych.|  
  
## <a name="code-access-security-cas"></a>Zabezpieczenia dostępu kodu (CAS)  
 Zabezpieczenia dostępu kodu (CAS) to mechanizm, który pomaga ograniczyć dostęp do tego kodu do chronionych zasobów i operacji. W .NET Framework urzędy certyfikacji wykonują następujące funkcje:  
  
- Definiuje uprawnienia i zestawy uprawnień, które reprezentują prawo dostępu do różnych zasobów systemu.  
  
- Umożliwia administratorom konfigurowanie zasad zabezpieczeń, kojarząc zestawy uprawnień z grupami kodu (grupy kodu).  
  
- Umożliwia programowi Code żądanie uprawnień wymaganych do uruchomienia programu, a także uprawnienia, które byłyby przydatne, i określa, które uprawnienia kod nigdy nie musi mieć.  
  
- Przyznaje uprawnienia do każdego zestawu, który jest ładowany, na podstawie uprawnień wymaganych przez kod oraz operacji dozwolonych przez zasady zabezpieczeń.  
  
- Włącza kod do żądania, że jego obiekty wywołujące mają określone uprawnienia.  
  
- Umożliwia wykonywanie kodu na potrzeby żądania, że jego obiekty wywołujące mają podpis cyfrowy, co pozwala tylko wywołującym z danej organizacji lub lokacji wywoływanie chronionego kodu.  
  
- Wymusza ograniczenia dotyczące kodu w czasie wykonywania, porównując przyznane uprawnienia każdego obiektu wywołującego na stosie wywołań z uprawnieniami, które są wymagane przez wywoływania.  
  
 Aby zminimalizować ilość szkód, które mogą wystąpić, jeśli atak powiedzie się, wybierz kontekst zabezpieczeń dla kodu, który udziela dostępu tylko do zasobów potrzebnych do wykonania pracy i nie tylko.  
  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczenia dostępu kodu i ADO.NET](code-access-security.md)|Opisuje interakcje między zabezpieczeniami dostępu kodu, zabezpieczeniami opartymi na rolach i częściowo zaufanymi środowiskami z perspektywy aplikacji ADO.NET.|  
|[Zabezpieczenia dostępu kodu](../../misc/code-access-security.md)|Zawiera linki do dodatkowych tematów opisujących urzędy certyfikacji w .NET Framework.|  
  
## <a name="database-security"></a>Zabezpieczenia bazy danych  
 Zasada najniższych uprawnień dotyczy również źródła danych. Poniżej wymieniono ogólne wskazówki dotyczące zabezpieczeń bazy danych:  
  
- Utwórz konta z najniższymi możliwymi uprawnieniami.  
  
- Nie Zezwalaj użytkownikom na dostęp do kont administracyjnych tylko w celu uzyskania działania kodu.  
  
- Nie zwracaj komunikatów o błędach po stronie serwera do aplikacji klienckich.  
  
- Sprawdź poprawność wszystkich danych wejściowych zarówno na kliencie, jak i na serwerze.  
  
- Używaj sparametryzowanych poleceń i unikaj dynamicznych instrukcji SQL.  
  
- Włącz inspekcję zabezpieczeń i rejestrowanie dla używanej bazy danych, aby otrzymywać alerty o naruszeniach zabezpieczeń.  
  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczenia serwera SQL](./sql/sql-server-security.md)|Zawiera omówienie zabezpieczeń SQL Server ze scenariuszami aplikacji, które zapewniają wskazówki dotyczące tworzenia bezpiecznych aplikacji ADO.NET, które są przeznaczone SQL Server.|  
|[Zalecenia dotyczące strategii dostępu do danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Zawiera zalecenia dotyczące uzyskiwania dostępu do danych i wykonywania operacji bazy danych.|  
  
## <a name="security-policy-and-administration"></a>Zasady zabezpieczeń i administracja  
 Nieprawidłowe administrowanie zasadami zabezpieczeń dostępu kodu (CAS) może potencjalnie stworzyć słabe zabezpieczenia. Po wdrożeniu aplikacji należy użyć technik monitorowania zabezpieczeń i ryzyka, które są oceniane jako nowe zagrożenia.  
  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zarządzanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))|Zawiera informacje dotyczące tworzenia i administrowania zasadami zabezpieczeń.|  
|[Najlepsze rozwiązania dotyczące zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))|Zawiera łącza opisujące sposób administrowania zasadami zabezpieczeń.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](securing-ado-net-applications.md)
- [Zabezpieczenia w programie .NET](../../../standard/security/index.md)
- [Zabezpieczenia serwera SQL](./sql/sql-server-security.md)
- [Omówienie ADO.NET](ado-net-overview.md)
