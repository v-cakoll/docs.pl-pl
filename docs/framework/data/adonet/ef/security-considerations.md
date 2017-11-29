---
title: "Zagadnienia dotyczące zabezpieczeń (Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 107b222d37d62505c021f277a660741b52a9cdbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="security-considerations-entity-framework"></a>Zagadnienia dotyczące zabezpieczeń (Entity Framework)
W tym temacie opisano zagadnienia dotyczące zabezpieczeń, które są specyficzne dla tworzenie, wdrażanie i uruchamianie [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji. Należy również stosować zaleceń dotyczących tworzenia bezpiecznego [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie zabezpieczeń](../../../../../docs/framework/data/adonet/security-overview.md).  
  
## <a name="general-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Następujące zagadnienia dotyczące zabezpieczeń są stosowane do wszystkich aplikacji, które używają [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
#### <a name="use-only-trusted-data-source-providers"></a>Użyj zaufanego tylko dostawcy źródła danych.  
 Aby komunikować się ze źródłem danych, dostawcę, wykonaj następujące czynności:  
  
-   Wyświetlany ciąg połączenia z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Tłumaczenie drzewo poleceń do źródła danych zapytania natywnego języka.  
  
-   Złóż i zwracać zestawów wyników.  
  
 Podczas operacji logowania opartego na hasło użytkownika przekazywania informacji do serwera przy użyciu biblioteki sieciowe o źródle danych. Dostawca złośliwego można ukraść poświadczenia użytkownika, generowanie złośliwych zapytań lub manipulowanie zestawu wyników.  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>Szyfrowane połączenie w celu ochrony poufnych danych.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nie obsługuje bezpośrednio szyfrowania danych. Jeśli użytkownicy uzyskują dostęp do danych przez sieć publiczną, aplikacja powinna nawiązywania zaszyfrowanego połączenia ze źródłem danych, aby zwiększyć bezpieczeństwo. Aby uzyskać więcej informacji zobacz dokumentację związanych z zabezpieczeniami, źródła danych. Dla źródła danych programu SQL Server, zobacz [szyfrowanie połączeń z programem SQL Server](http://go.microsoft.com/fwlink/?LinkId=119544).  
  
#### <a name="secure-the-connection-string"></a>Bezpieczny ciąg połączenia.  
 Ochrona dostępu do źródła danych jest jednym z najważniejszych celów zabezpieczania aplikacji. Ciąg połączenia przedstawia potencjalne luki w zabezpieczeniach, jeśli nie jest zabezpieczony lub jest niepoprawnie zbudowane. Przechowują informacje o połączeniu w formacie zwykłego tekstu lub zachować go w pamięci, istnieje ryzyko naruszenia całego systemu. Zalecane metody zabezpieczania parametry połączenia są następujące:  
  
-   Uwierzytelnianie systemu Windows ze źródłem danych programu SQL Server.  
  
     Podczas połączenia ze źródłem danych programu SQL Server za pomocą uwierzytelniania systemu Windows, ciąg połączenia nie zawiera informacji logowania i hasło.  
  
-   Szyfrowanie za pomocą konfiguracji chronionych sekcji pliku konfiguracji.  
  
     Program ASP.NET udostępnia funkcję chronionych konfigurację, która umożliwia szyfrowanie poufnych informacji w pliku konfiguracji. Mimo że przeznaczony głównie dla platformy ASP.NET, umożliwia także chronionych konfiguracji do szyfrowania plików konfiguracji w aplikacjach systemu Windows. Aby uzyskać szczegółowy opis nowych możliwości konfiguracji chronionych, zobacz [szyfrowania informacji przy użyciu chronione Konfiguracja](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
-   Przechowywanie parametrów połączenia w plikach konfiguracji zabezpieczonych.  
  
     Nigdy nie należy osadzić parametry połączenia w kodzie źródłowym. Parametry połączenia można przechowywać w plikach konfiguracji, która eliminuje potrzebę osadzić je w kodzie aplikacji. Domyślnie Kreator modelu danych jednostki przechowuje parametry połączenia w pliku konfiguracyjnym aplikacji. Należy zabezpieczyć ten plik, aby uniemożliwić nieautoryzowany dostęp.  
  
-   Użyj konstruktorów ciągu połączenia podczas dynamicznego tworzenia połączenia.  
  
     Jeśli musisz utworzyć parametry połączenia w czasie wykonywania, użyj <xref:System.Data.EntityClient.EntityConnectionStringBuilder> klasy. Ten ciąg konstruktora klasy pomaga zapobiegać atakom iniekcji ciąg połączenia, sprawdzanie poprawności i anulowanie nieprawidłowe dane wejściowe. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie ciągu połączenia EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md). Również użyć klasy konstruktora odpowiedni ciąg, aby utworzyć parametry połączenia źródła danych, który jest częścią [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] parametry połączenia. Informacje o Konstruktorzy ciągów połączenia dla dostawcy ADO.NET, zobacz [Konstruktorzy ciągów połączenia](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>Nie ujawniaj EntityConnection niezaufanym użytkownikom.  
 <xref:System.Data.EntityClient.EntityConnection> Obiekt ujawnia parametry połączenia w podstawowym połączeniu. Użytkownik z dostępem do <xref:System.Data.EntityClient.EntityConnection> obiektu można również zmienić <xref:System.Data.ConnectionState> z podstawowym połączeniu. <xref:System.Data.EntityClient.EntityConnection> Klasa nie jest bezpieczne dla wątków.  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>Nie przekazuj połączenia poza kontekstu zabezpieczeń.  
 Po nawiązaniu połączenia, nie musi ona przekazać poza kontekstem zabezpieczeń. Na przykład jeden wątek uprawnień do otwierania połączenia nie należy przechowywać połączenia w globalnej lokalizacji. Jeśli połączenie jest dostępny w globalnej lokalizacji, inny wątek złośliwego można użyć otwartego połączenia bez jawnie udzielone uprawnienie.  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>Należy pamiętać, że informacje logowania i hasła mogą być widoczne w zrzutu pamięci.  
 Podczas logowania i hasło informacje o źródle danych został podany w parametrach połączenia, te informacje są przechowywane w pamięci, do czasu odzyskiwania pamięci zwraca zasobów. Dzięki temu możliwe ustalenie, gdy ciąg hasła nie jest już w pamięci. Jeśli aplikacja ulegnie awarii, plik zrzutu pamięci może zawierać informacje poufne zabezpieczeń, a użytkownik uruchamiający aplikację i każdy użytkownik z dostępem administracyjnym do komputera można przeglądać plik zrzutu pamięci. Uwierzytelnianie systemu Windows dla połączeń z programu Microsoft SQL Server.  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>Zezwolenie użytkownikom tylko niezbędnych uprawnień w źródle danych.  
 Administrator źródła danych należy udzielić tylko wymagane uprawnienia dla użytkowników. Mimo że [!INCLUDE[esql](../../../../../includes/esql-md.md)] jest nie instrukcje DML pomocy technicznej, które modyfikują dane, takie jak INSERT, UPDATE lub DELETE, użytkownicy mogą nadal uzyskiwać dostęp do połączenia ze źródłem danych. Złośliwy użytkownik może używać tego połączenia do wykonywania instrukcji DML w języku macierzystym źródła danych.  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>Uruchamianie aplikacji minimalny poziom uprawnień.  
 Jeśli zezwolisz na zarządzanej aplikacji do uruchamiania z uprawnieniami pełnego zaufania [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] nie powoduje ograniczenia dostępu aplikacji do komputera. Może to umożliwić luki w zabezpieczeniach w aplikacji włamywać się do całego systemu. Aby korzystać z zabezpieczeń dostępu kodu i innych mechanizmów zabezpieczeń w [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], należy uruchomić aplikacje przy użyciu uprawnień częściowego zaufania, a minimalny zestaw uprawnień, które są wymagane do włączenia aplikacji funkcji. Minimalne uprawnienia są następujące uprawnienia dostępu do kodu użytkownika [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] potrzeb aplikacji:  
  
-   <xref:System.Security.Permissions.FileIOPermission>: <xref:System.Security.Permissions.FileIOPermissionAccess.Write> do otwierania plików określonych metadanych lub <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> do wyszukiwania plików metadanych katalogu.  
  
-   <xref:System.Security.Permissions.ReflectionPermission>: <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> do obsługi LINQ do jednostek zapytań.  
  
-   <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState.Unrestricted> można zarejestrować w <xref:System.Transactions> <xref:System.Transactions.Transaction>.  
  
-   <xref:System.Security.Permissions.SecurityPermission>: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> do serializacji wyjątków przy użyciu <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
-   Uprawnienie do otwierania połączenia z bazą danych i wykonywać polecenia w bazie danych, takich jak <xref:System.Data.SqlClient.SqlClientPermission> dla [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] bazy danych.  
  
 Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
#### <a name="do-not-install-untrusted-applications"></a>Nie należy instalować niezaufanych aplikacji.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nie wymusza uprawnień zabezpieczeń i wywoła dowolnego kodu obiektu dane dostarczone przez użytkownika w procesie niezależnie od tego, czy jest zaufany lub nie. Upewnij się, że uwierzytelnianie i autoryzacja klienta jest wykonywane przez Magazyn danych i aplikacji.  
  
#### <a name="restrict-access-to-all-configuration-files"></a>Ograniczanie dostępu do wszystkich plików konfiguracji.  
 Administrator może ograniczyć dostęp do zapisu do wszystkich plików, które będzie określić konfigurację dla aplikacji, w tym enterprisesec.config — Security.config —, machine.conf, i pliku konfiguracji aplikacji \< *aplikacji* >. exe.config.  
  
 Niezmienna Nazwa dostawcy jest można modyfikować w pliku app.config. Aplikacja kliencka musi odpowiada za dostęp do źródłowego dostawcy za pośrednictwem standardowego dostawcy fabryki modelu przy użyciu silnej nazwy.  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>Ogranicz uprawnienia do modelu i mapowania plików.  
 Administrator musi ograniczyć dostęp do zapisu do modelu i mapowania plików (edmx, CSDL, ssdl i .msl) tylko użytkownicy, którzy zmodyfikować mapowania i modelu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Wymaga tylko do odczytu tych plików w czasie wykonywania. Administrator powinien również ograniczanie dostępu do warstwy obiektu i widoku wstępnie skompilowanych plików kodu źródłowego, które są generowane przez [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] narzędzia.  
  
## <a name="security-considerations-for-queries"></a>Zagadnienia dotyczące zabezpieczeń dla zapytań  
 Podczas wykonywania zapytania w modelu koncepcyjnym, mają zastosowanie następujące zagadnienia dotyczące zabezpieczeń. Te kwestie [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytania korzystające z EntityClient i do zapytań obiektu za pomocą LINQ, [!INCLUDE[esql](../../../../../includes/esql-md.md)]oraz metody konstruktora zapytań.  
  
#### <a name="prevent-sql-injection-attacks"></a>Zapobieganie atakom iniekcji kodu SQL.  
 Aplikacje często zająć zewnętrzny (od użytkownika lub innego agenta zewnętrznych) i wykonywania akcji w oparciu o te dane wejściowe. Wszystkie dane wejściowe, który bezpośrednio lub pośrednio pochodzi od użytkownika lub zewnętrznego agenta może mieć zawartość, która używa składni języka docelowego w celu wykonania akcji nieautoryzowanego. Gdy języka docelowego jest języka SQL (Structured Query), takich jak [!INCLUDE[tsql](../../../../../includes/tsql-md.md)], manipulowanie ten nosi nazwę ataku polegającego na iniekcji SQL. Złośliwy użytkownik może wstrzyknąć polecenia bezpośrednio do zapytania i tabeli bazy danych, "odmowa usługi" lub w przeciwnym razie Zmień rodzaj wykonywanej operacji.  
  
-   [!INCLUDE[esql](../../../../../includes/esql-md.md)]ataki na wstrzyknięciu kodu:  
  
     Ataki mogą być wykonywane w [!INCLUDE[esql](../../../../../includes/esql-md.md)] podając złośliwego dane wejściowe do wartości, które są używane w predykacie zapytania i w nazwach parametrów. Aby uniknąć zagrożenia iniekcja kodu SQL, nigdy nie należy łączyć danych wejściowych użytkownika z [!INCLUDE[esql](../../../../../includes/esql-md.md)] tekst polecenia.  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)]zapytania akceptuje wszędzie parametrów, że literały są akceptowane. Zapytania sparametryzowane należy używać zamiast iniekcję literały z zewnętrznego agenta bezpośrednio do zapytania. Należy również rozważyć za pomocą metody konstruktora zapytań do skonstruowania bezpiecznie [SQL jednostki](http://msdn.microsoft.com/en-us/05685434-05e6-41c2-8d5e-8933b88a40b0).  
  
-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]ataki na wstrzyknięciu kodu:  
  
     Mimo że zapytanie jest możliwe w [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)], odbywa się za pośrednictwem interfejsu API modelu obiektu. W odróżnieniu od [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytań, [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] zapytania nie składają się przy użyciu manipulowanie ciągami lub łączenia i nie jest narażony na ataki tradycyjnych.  
  
#### <a name="prevent-very-large-result-sets"></a>Zapobiegaj bardzo dużych zestawów wyników.  
 Zestaw wyników bardzo dużych może spowodować systemów klienckich, aby zamknąć, jeżeli klient wykonuje operacje, których użycie zasobów proporcjonalny do rozmiaru zestawu wyników. Nieoczekiwanie dużych zestawów wyników może wystąpić w następujących warunkach:  
  
-   W zapytaniach duże bazy danych, które nie zawierają warunki odpowiedni filtr.  
  
-   W zapytaniach, które tworzyć sprzężenia kartezjańskimi na serwerze.  
  
-   Zagnieżdżone w [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytania.  
  
 Gdy akceptowanie danych wejściowych użytkownika, to należy się upewnić, czy dane wejściowe nie może spowodować zestawów wyników większy niż co system może obsłużyć. Można również użyć <xref:System.Linq.Queryable.Take%2A> metody w [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] lub [LIMIT](../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) operatora w [!INCLUDE[esql](../../../../../includes/esql-md.md)] do ograniczania rozmiaru zestawu wyników.  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>Unikaj zwracania wyników IQueryable podczas Uwidaczniającą metody potencjalnie niezaufanych wywołań.  
 Należy unikać zwracania <xref:System.Linq.IQueryable%601> typów z metod, które są dostępne do wywoływania potencjalnie niezaufane z następujących powodów:  
  
-   Konsument zapytania, który ujawnia <xref:System.Linq.IQueryable%601> typu można wywoływać metod w wyniku, który ujawnia zabezpieczonych danych lub zwiększyć rozmiar zestawu wyników. Na przykład wziąć pod uwagę następujące podpis metody:  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     Klient korzystający z tej kwerendy może wywołać `.Include("Orders")` w zwróconym `IQueryable<Customer>` do pobierania danych zapytania nie powinna zostać udostępniona. Można tego uniknąć, zmieniając typ zwracany metody <xref:System.Collections.Generic.IEnumerable%601> i wywołanie metody (takie jak `.ToList()`) która zostaje wyniki.  
  
-   Ponieważ <xref:System.Linq.IQueryable%601> zapytania są wykonywane, gdy wyniki są iterowane przez konsumentów zapytania, który ujawnia <xref:System.Linq.IQueryable%601> typu może przechwytywać wyjątki, zwracane. Wyjątki mogą zawierać informacje, które nie są przeznaczone do konsumenta.  
  
## <a name="security-considerations-for-entities"></a>Zagadnienia dotyczące zabezpieczeń dla obiektów  
 Podczas generowania i Praca z typami jednostek, mają zastosowanie następujące zagadnienia dotyczące zabezpieczeń.  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>Nie udostępniaj obiektu ObjectContext między domenami aplikacji.  
 Udostępnianie <xref:System.Data.Objects.ObjectContext> z więcej niż jedną aplikację domeny może ujawnić informacji w parametrach połączenia. Zamiast tego należy przekazywać obiektów serializowanych ani wykresów obiektów domeny aplikacji i następnie dołączyć te obiekty, do <xref:System.Data.Objects.ObjectContext> w tej domenie aplikacji. Aby uzyskać więcej informacji, zobacz [serializacji obiektów](http://msdn.microsoft.com/en-us/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
#### <a name="prevent-type-safety-violations"></a>Zapobiegaj typu naruszenia bezpieczeństwa.  
 W przypadku naruszenia bezpieczeństwa typu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nie może zagwarantować spójność danych w obiektach. Naruszenia bezpieczeństwa typ mógł wystąpić, jeśli zezwolisz niezaufanych aplikacji do uruchamiania z zabezpieczeniami dostępu kodu pełnego zaufania.  
  
#### <a name="handle-exceptions"></a>Obsługa wyjątków.  
 Dostęp do metody i właściwości <xref:System.Data.Objects.ObjectContext> w bloku try-catch. Przechwytywanie wyjątków uniemożliwia osobie nieobsłużonych wyjątków z udostępnianie wpisów w <xref:System.Data.Objects.ObjectStateManager> lub informacji o modelu (takich jak nazwy tabeli) do użytkowników aplikacji.  
  
## <a name="security-considerations-for-aspnet-applications"></a>Zagadnienia dotyczące zabezpieczeń dla aplikacji ASP.NET  
 Należy rozważyć następujące podczas pracy ze ścieżkami w [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] aplikacji.  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>Sprawdź, czy host sprawdza ścieżkę.  
 Gdy `|DataDirectory|` (ujęta w potoku symboli) jest używany ciąg podstawienia, [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] sprawdza, czy rozpoznana ścieżka jest obsługiwana. Na przykład ".." nie jest dozwolona za `DataDirectory`. Sprawdzanie tego samego postępowania operatora główny aplikacji sieci Web (`~`) odbywa się za pośrednictwem procesu hostingu [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]. Program IIS wykonuje sprawdzanie; jednak hostach innych niż IIS mogą nie Sprawdź, czy rozpoznana ścieżka jest obsługiwana. Należy zapoznać się z zachowaniem hosta, na której wdrożono [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>Nie należy wprowadzać założenia dotyczące nazwy rozpoznana ścieżka.  
 Mimo że wartości, do którego operator głównego (`~`) i `DataDirectory` podczas wykonywania aplikacji, Usuń ciąg podstawienia powinna pozostać stała [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nie ogranicza hosta z zmodyfikowanie tych wartości.  
  
#### <a name="verify-the-path-length-before-deployment"></a>Sprawdź długość ścieżki przed przystąpieniem do wdrożenia.  
 Przed wdrożeniem [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji, należy upewnić się, że wartości operatora głównego (~) i `DataDirectory` ciąg podstawienia nie przekraczają limitów długość ścieżki w systemie operacyjnym. [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]dostawcy danych nie upewnij się, że długość ścieżki jest prawidłowy maksymalnej.  
  
## <a name="security-considerations-for-adonet-metadata"></a>Zagadnienia dotyczące zabezpieczeń dla metadanych programu ADO.NET  
 Podczas generowania i Praca z modelu i mapowania plików, mają zastosowanie następujące zagadnienia dotyczące zabezpieczeń.  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>Nie ujawniaj informacji poufnych za pośrednictwem rejestrowania.  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]składniki usługi metadanych nie Rejestruj informacje prywatne. Brak wyników, które nie mogą zostać zwrócone ze względu na ograniczenia dostępu, systemy zarządzania bazami danych i systemy plików powinien zwrócić wyników zamiast wywoływanie wyjątek, który może zawierać informacje poufne.  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>Nie akceptuj obiekty w obiekcie MetadataWorkspace ze źródeł niezaufanych.  
 Aplikacje nie powinien akceptować wystąpienia <xref:System.Data.Metadata.Edm.MetadataWorkspace> klasy ze źródeł niezaufanych. Zamiast tego należy jawnie konstruowania i wypełnienia obszaru roboczego z takich źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Zagadnienia dotyczące migracji](../../../../../docs/framework/data/adonet/ef/migration-considerations.md)
