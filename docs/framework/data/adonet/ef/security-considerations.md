---
title: Security Considerations (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: 14d07fcb1d97a4e71747d6517f63fbc4108493da
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641184"
---
# <a name="security-considerations-entity-framework"></a>Security Considerations (Entity Framework)
W tym temacie opisano zagadnienia dotyczące zabezpieczeń, które są specyficzne dla opracowywanie, wdrażanie i uruchamianie [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji. Należy również przestrzegać zaleceń dotyczących tworzenia bezpiecznych [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [Przegląd zabezpieczeń](../../../../../docs/framework/data/adonet/security-overview.md).  
  
## <a name="general-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Następujące zagadnienia dotyczące zabezpieczeń, Zastosuj do wszystkich aplikacji, które używają [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
#### <a name="use-only-trusted-data-source-providers"></a>Użyj tylko zaufanego dostawcy źródła danych.  
 Aby komunikować się ze źródłem danych, dostawca, wykonaj następujące czynności:  
  
- Odbieranie parametrów połączenia z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
- Wykonuje translację elementu drzewo poleceń do źródła danych zapytania natywnego języka.  
  
- Możesz korzystać i zwrócić zestaw wyników.  
  
 Podczas operacji logowania informacje, które opiera się na hasło użytkownika jest przekazywany do serwera przy użyciu bibliotek sieciowych bazowego źródła danych. Złośliwe dostawcy można kradzież poświadczeń użytkownika, generowanie złośliwych zapytań i manipulować w zestawie wyników.  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>Szyfruj połączenie w celu ochrony poufnych danych.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nie obsługuje bezpośrednio szyfrowania danych. Jeśli użytkownikom dostęp do danych przez sieć publiczną, aplikacja powinna nawiązywania zaszyfrowanego połączenia ze źródłem danych, aby zwiększyć poziom zabezpieczeń. Aby uzyskać więcej informacji zobacz dokumentację związanych z zabezpieczeniami dla źródła danych. Dla źródła danych programu SQL Server, zobacz [szyfrowanie połączeń z programem SQL Server](https://go.microsoft.com/fwlink/?LinkId=119544).  
  
#### <a name="secure-the-connection-string"></a>Bezpieczne połączenia.  
 Ochrona dostępu do źródła danych jest jednym z najważniejszych celów podczas zabezpieczania aplikacji. Parametry połączenia przedstawia informacje o potencjalnych luk w zabezpieczeniach, jeśli nie jest zabezpieczony, lub jest nieprawidłowo skonstruowany. Przechowują informacje o połączeniu w postaci zwykłego tekstu lub utrwalić ją w pamięci, istnieje ryzyko obniżania całego systemu. Poniżej przedstawiono zalecane metody zabezpieczania parametry połączenia:  
  
- Uwierzytelnianie Windows ze źródłem danych programu SQL Server.  
  
     Gdy połączenie ze źródłem danych programu SQL Server przy użyciu uwierzytelniania Windows, ciąg połączenia nie zawiera informacji logowania i hasło.  
  
- Szyfrowanie przy użyciu konfiguracji chronionych sekcji pliku konfiguracji.  
  
     Program ASP.NET zapewnia funkcję o nazwie chronionych konfigurację, która umożliwia szyfrowanie poufnych informacji w pliku konfiguracji. Mimo że przeznaczony głównie dla platformy ASP.NET, umożliwia także konfiguracji chronionej do szyfrowania sekcjami plików konfiguracji w aplikacji Windows. Aby uzyskać szczegółowy opis nowych funkcji konfiguracji chronionej, zobacz [szyfrowania informacji przy użyciu chronione Konfiguracja](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
- Store parametry połączenia w plikach konfiguracyjnych zabezpieczone.  
  
     Nigdy nie należy osadzić parametry połączenia w kodzie źródłowym. Parametry połączenia można przechowywać w plikach konfiguracji, więc nie trzeba ich osadzać w kodzie twojej aplikacji. Domyślnie Kreator modelu Entity Data Model przechowuje ciągi połączeń w pliku konfiguracyjnym aplikacji. Należy zabezpieczyć ten plik, aby zapobiegać nieautoryzowanemu dostępowi.  
  
- Użyj Konstruktorzy parametrów połączeń podczas dynamicznego tworzenia połączeń.  
  
     Jeśli musisz utworzyć parametry połączenia w czasie wykonywania, użyj <xref:System.Data.EntityClient.EntityConnectionStringBuilder> klasy. Ta klasa konstruktora ciągu zapobiega atakami polegającymi na iniekcji ciągu połączenia, sprawdzanie poprawności i anulowania zapewnianego element nieprawidłowe dane wejściowe. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie ciągu połączenia EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md). Również korzystanie z klasy Konstruktor odpowiedni ciąg do konstruowania parametry połączenia źródła danych, który jest częścią [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] parametry połączenia. Aby uzyskać informacji na temat Konstruktorzy parametrów połączenia dla dostawcy ADO.NET, zobacz [Konstruktorzy parametrów połączeń](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>Nie ujawniaj EntityConnection niezaufanym użytkownikom.  
 <xref:System.Data.EntityClient.EntityConnection> Obiekt udostępnia połączenie podstawowe parametry połączenia. Użytkownik z uprawnieniami do <xref:System.Data.EntityClient.EntityConnection> obiektu można również zmienić <xref:System.Data.ConnectionState> połączenia podstawowego. <xref:System.Data.EntityClient.EntityConnection> Klasa nie jest bezpieczny dla wątków.  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>Nie przekazuj połączeń poza kontekstem zabezpieczeń.  
 Po nawiązaniu połączenia, nie należy go przekazać poza kontekstem zabezpieczeń. Na przykład jeden wątek z uprawnieniami do otwierania połączenia nie należy przechowywać połączenia w globalnej lokalizacji. Jeśli połączenie jest dostępny w globalnej lokalizacji, inny wątek złośliwego można użyć otwartego połączenia bez tego uprawnienia, które jawnie przyznane uprawnienia do niego.  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>Należy pamiętać, że informacje logowania i hasła mogą być widoczne w zrzut pamięci.  
 Podczas logowania i hasło informacje o źródle danych jest podana w parametrach połączenia, te informacje są utrzymywane w pamięci, aż do wyrzucania elementów bezużytecznych odzyskuje zasobów. Dzięki temu możliwe ustalenie, gdy ciąg hasła nie jest już w pamięci. Jeśli aplikacja ulegnie awarii, plik zrzutu pamięci może zawierać informacje poufne zabezpieczeń, a użytkownik uruchamiający aplikację i każdy użytkownik z dostępem administracyjnym do komputera, można wyświetlić w pliku zrzutu pamięci. Uwierzytelnianie Windows dla połączeń z programu Microsoft SQL Server.  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>Przyznaj użytkownikom tylko niezbędnych uprawnień w źródle danych.  
 Administrator źródła danych należy udzielać użytkownikom tylko niezbędnych uprawnień. Mimo że [!INCLUDE[esql](../../../../../includes/esql-md.md)] jest nie DML oświadczenia dotyczące pomocy technicznej, które modyfikują dane, takie jak INSERT, UPDATE lub DELETE, użytkownicy mogą nadal uzyskiwać dostęp do połączenia ze źródłem danych. Złośliwy użytkownik może używać tego połączenia, można wykonać instrukcji DML w macierzystym języku źródła danych.  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>Uruchamianie aplikacji na minimalny poziom uprawnień.  
 Jeśli zezwolisz na zarządzanej aplikacji do uruchamiania przy użyciu uprawnień pełnego zaufania [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] nie ogranicza dostęp aplikacji do Twojego komputera. Może to umożliwić luki w zabezpieczeniach w aplikacji, aby naruszyć bezpieczeństwo całego systemu. Zabezpieczenia dostępu kodu i inne mechanizmy zabezpieczeń w [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], należy uruchomić aplikacje przy użyciu uprawnień częściowego zaufania i minimalny zestaw uprawnień, które są wymagane do włączenia aplikacji funkcji. Następujące uprawnienia dostępu kodu są minimalne uprawnienia użytkownika [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji potrzebom:  
  
- <xref:System.Security.Permissions.FileIOPermission>: <xref:System.Security.Permissions.FileIOPermissionAccess.Write> do otwierania plików określonych metadanych lub <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> do wyszukiwania plików metadanych katalogu.  
  
- <xref:System.Security.Permissions.ReflectionPermission>: <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> do obsługi zapytań LINQ do zapytań jednostki.  
  
- <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState.Unrestricted> można zarejestrować w <xref:System.Transactions> <xref:System.Transactions.Transaction>.  
  
- <xref:System.Security.Permissions.SecurityPermission>: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> serializować wyjątków za pomocą <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
- Uprawnienia do otwierania połączenia z bazą danych i wykonywania poleceń dla bazy danych, takich jak <xref:System.Data.SqlClient.SqlClientPermission> dla bazy danych programu SQL Server.  
  
 Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
#### <a name="do-not-install-untrusted-applications"></a>Nie należy instalować niezaufane aplikacje.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nie wymusza żadnych uprawnień zabezpieczeń i wywoła dowolnego kodu obiektu dane dostarczone przez użytkownika w procesie, niezależnie od tego, czy jest zaufany lub nie. Upewnij się, że uwierzytelniania i autoryzacji klienta jest wykonywane przez Magazyn danych i aplikacji.  
  
#### <a name="restrict-access-to-all-configuration-files"></a>Ograniczanie dostępu do wszystkich plików konfiguracji.  
 Administrator należy ograniczyć dostęp do zapisu do wszystkich plików, które określają konfigurację dla aplikacji, w tym celu enterprisesec.config —, Security.config — machine.conf, i pliku konfiguracji aplikacji \< *aplikacji* >. exe.config.  
  
 Nazwa niezmienna dostawcy jest można modyfikować w pliku app.config. Aplikacja kliencka musi ponosi odpowiedzialność za dostęp do źródłowego dostawcy za pośrednictwem standardowego dostawcy fabryki modelu za pomocą silnej nazwy.  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>Uprawnienia do modelu i mapowania plików.  
 Administrator należy ograniczyć dostęp do zapisu do modelu i mapowania plików (edmx, .csdl, ssdl i MSL albo identyfikatorem) tylko do użytkowników modyfikujących modelu i mapowania. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Wymaga tylko do odczytu tych plików w czasie wykonywania. Administrator powinien również ograniczyć dostęp do warstwy obiektu i widoku wstępnie skompilowanych plików kodu źródłowego, które są generowane przez [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] narzędzia.  
  
## <a name="security-considerations-for-queries"></a>Zagadnienia dotyczące zabezpieczeń dla zapytań  
 Podczas wykonywania zapytań dotyczących modelu koncepcyjnego, mają zastosowanie następujące zagadnienia dotyczące zabezpieczeń. Te zagadnienia dotyczą [!INCLUDE[esql](../../../../../includes/esql-md.md)] wysyła kwerendę za pomocą EntityClient i obiekt zapytania za pomocą LINQ, [!INCLUDE[esql](../../../../../includes/esql-md.md)]oraz metody konstruktora zapytań.  
  
#### <a name="prevent-sql-injection-attacks"></a>Uniemożliwić ataki przez wstrzyknięcie kodu SQL.  
 Aplikacje często akceptują dane wejściowe w zewnętrznych (z lub innego zewnętrznego agenta użytkownika) i wykonywać akcje w oparciu o te dane wejściowe. Wszystkie dane wejściowe, który bezpośrednio lub pośrednio pochodzi od użytkownika lub zewnętrznego agenta może mieć zawartości, która używa składni języka docelowego w celu wykonywania akcji nieautoryzowanego. Gdy język docelowy jest języka SQL (Structured Query), takich jak [!INCLUDE[tsql](../../../../../includes/tsql-md.md)], manipulowania ten jest znany jako ataku polegającego na iniekcji SQL. Złośliwy użytkownik może wstrzyknąć poleceń bezpośrednio do zapytania i upuść tabeli bazy danych, i spowodować odmowę usługi lub w przeciwnym razie Zmień rodzaj wykonywanej operacji.  
  
- [!INCLUDE[esql](../../../../../includes/esql-md.md)] ataki przez iniekcję kodu:  
  
     Ataki przez iniekcję SQL mogą być wykonywane w [!INCLUDE[esql](../../../../../includes/esql-md.md)] poprzez dostarczenie złośliwych danych do wartości, które są używane w predykacie zapytania i w nazwach parametrów. Aby uniknąć ryzyka wstrzyknięcie kodu SQL, nigdy nie należy łączyć dane wejściowe użytkownika z [!INCLUDE[esql](../../../../../includes/esql-md.md)] tekst polecenia.  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytania akceptować wszędzie, gdzie parametry, że literały są akceptowane. Należy użyć sparametryzowanych zapytań zamiast iniekcji literały z zewnętrznego agenta bezpośrednio do zapytania. Należy również rozważyć użycie [metody konstruktora zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896238(v=vs.100)) bezpiecznie skonstruowanie jednostki SQL.  
  
- [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] ataki przez iniekcję kodu:  
  
     Mimo że w kompozycją zapytań [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)], odbywa się za pośrednictwem interfejsu API modelu obiektu. W odróżnieniu od [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytań, [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] zapytania nie składają się przy użyciu manipulowanie ciągami lub łączenia i nie są one podatne na tradycyjnych ataki przez wstrzyknięcie kodu SQL.  
  
#### <a name="prevent-very-large-result-sets"></a>Zapobiegaj bardzo dużych zestawów wyników.  
 Zestaw wyników bardzo dużych może spowodować systemów klienckich, aby zamknąć, jeżeli klient wykonuje operacje, które zużywają zasoby proporcjonalny do rozmiaru zestawu wyników. Nieoczekiwanie dużych zestawów danych może wystąpić w następujących warunkach:  
  
- W zapytaniach dotyczących dużej bazy danych, które nie zawierają warunków odpowiedni filtr.  
  
- W zapytaniach, tworzyć sprzężenia Kartezjańskiego na serwerze.  
  
- W zagnieżdżonej [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytania.  
  
 Akceptując danych wejściowych użytkownika, należy się upewnić, że dane wejściowe nie może powodować zestawy wyników do wydają się większe niż co system może obsłużyć danych. Można również użyć <xref:System.Linq.Queryable.Take%2A> method in Class metoda [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] lub [LIMIT](../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) operatora w [!INCLUDE[esql](../../../../../includes/esql-md.md)] konieczność ograniczenia rozmiaru zestawu wyników.  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>Należy unikać zwracania wyników IQueryable, gdy Uwidaczniającą metody potencjalnie niezaufanych wywołujących.  
 Należy unikać cofania się <xref:System.Linq.IQueryable%601> typów z metod, które są dostępne do potencjalnie niezaufanych wywołujących z następujących powodów:  
  
- Konsument kwerendę, która udostępnia <xref:System.Linq.IQueryable%601> typu można wywoływać metody na wynik, który ujawnić zabezpieczonych danych lub zwiększyć rozmiar zestawu wyników. Na przykład rozważmy następujący podpis metody:  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     Konsument to zapytanie może wywołać `.Include("Orders")` na zwracanego `IQueryable<Customer>` do pobierania danych zapytania nie chcesz ujawniać. To można uniknąć, zmieniając typ zwracany metody <xref:System.Collections.Generic.IEnumerable%601> i wywołanie metody (takie jak `.ToList()`) który materializuje wyniki.  
  
- Ponieważ <xref:System.Linq.IQueryable%601> zapytania są wykonywane, gdy wyników jest iterowana, odbiorcy kwerendę, która udostępnia <xref:System.Linq.IQueryable%601> typu może przechwytywać wyjątki, które są zgłaszane. Wyjątki mogą zawierać informacje, które nie są przeznaczone dla konsumentów.  
  
## <a name="security-considerations-for-entities"></a>Uwagi dotyczące podmiotów zabezpieczeń  
 Podczas generowania i pracą z nimi przy użyciu typów jednostek, mają zastosowanie następujące zagadnienia dotyczące zabezpieczeń.  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>Nie należy udostępniać obiektu ObjectContext w różnych domenach aplikacji.  
 Udostępnianie <xref:System.Data.Objects.ObjectContext> z więcej niż jednej aplikacji domeny może spowodować ujawnienie informacji w parametrach połączenia. Zamiast tego należy przeniesienie obiektów zserializowanych lub wykresów obiektów do innej domeny aplikacji i następnie dołączyć te obiekty do <xref:System.Data.Objects.ObjectContext> w tej domenie aplikacji. Aby uzyskać więcej informacji, zobacz [serializacji obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
#### <a name="prevent-type-safety-violations"></a>Zapobiegaj naruszenia bezpieczeństwa typu.  
 W przypadku naruszenia bezpieczeństwa typu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nie może zagwarantować integralności danych w obiektach. Naruszenia bezpieczeństwa typu może wystąpić, jeśli zezwolisz na niezaufane aplikacje do uruchamiania przy użyciu zabezpieczeń dostępu kodu pełnego zaufania.  
  
#### <a name="handle-exceptions"></a>Obsługa wyjątków.  
 Dostęp do metod i właściwości <xref:System.Data.Objects.ObjectContext> w bloku try-catch. Przechwytywanie wyjątków zapobiega nieobsługiwanych wyjątków z udostępnianie wpisów w <xref:System.Data.Objects.ObjectStateManager> lub informacji o modelu (np. nazwy tabel) do użytkowników aplikacji.  
  
## <a name="security-considerations-for-aspnet-applications"></a>Zagadnienia dotyczące zabezpieczeń dla aplikacji ASP.NET  
 Należy rozważyć następujące podczas pracy ze ścieżkami w [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] aplikacji.  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>Sprawdź, czy hosta sprawdza ścieżkę.  
 Gdy `|DataDirectory|` (ujęty w symbole potoku) jest używany ciąg podstawienia, [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] sprawdza, czy rozpoznana ścieżka jest obsługiwana. Na przykład ".." nie jest dozwolona za `DataDirectory`. Tym samym sprawdzanie rozpoznawania operatora główny aplikacji sieci Web (`~`) odbywa się przez proces hostingu [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]. Usługi IIS wykonuje to sprawdzenie; hosty innej niż IIS mogą nie weryfikują jednak czy rozpoznana ścieżka jest obsługiwana. Należy znać zachowanie hosta, na którym jest wdrażany [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>Nie należy wprowadzać założeń dotyczących nazw rozpoznana ścieżka.  
 Mimo że wartości, do którego operator głównego (`~`) i `DataDirectory` resolve ciąg podstawienia powinien pozostaje niezmienna, podczas wykonywania aplikacji [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nie ogranicza hosta modyfikowanie tych wartości.  
  
#### <a name="verify-the-path-length-before-deployment"></a>Sprawdź długość ścieżki, przed przystąpieniem do wdrożenia.  
 Przed wdrożeniem [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji, należy upewnić się, że wartości operator głównym (~) i `DataDirectory` ciąg podstawienia nie przekraczają limitów długość ścieżki w systemie operacyjnym. [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawcy danych nie upewnij się, że długość ścieżki w granicach prawidłowe.  
  
## <a name="security-considerations-for-adonet-metadata"></a>Zagadnienia dotyczące zabezpieczeń dla metadanych programu ADO.NET  
 Podczas generowania i pracą z nimi za pomocą modelu i mapowania plików, mają zastosowanie następujące zagadnienia dotyczące zabezpieczeń.  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>Nie ujawniaj poufnych informacji za pośrednictwem rejestrowania.  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] składniki usługi metadanych nie Rejestruj informacje prywatne. W przypadku wyników, które nie mogą być zwracane z powodu ograniczeń dostępu systemy zarządzania bazami danych i systemy plików powinna zwrócić wyniki, zerowego zamiast zgłaszania wyjątku, który może zawierać informacje poufne.  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>Nie akceptuj obiektów w obiekcie MetadataWorkspace ze źródeł niezaufanych.  
 Aplikacje powinny akceptuje wystąpień <xref:System.Data.Metadata.Edm.MetadataWorkspace> klasy z niezaufanego źródła. Zamiast tego należy jawnie utworzyć i wypełnienia obszaru roboczego z takich źródeł.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Zagadnienia dotyczące migracji](../../../../../docs/framework/data/adonet/ef/migration-considerations.md)
