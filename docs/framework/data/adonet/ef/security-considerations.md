---
title: Zagadnienia dotyczące zabezpieczeń (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: 1865afb384cfff41ede953c00f01cc96aea9a080
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854249"
---
# <a name="security-considerations-entity-framework"></a>Zagadnienia dotyczące zabezpieczeń (Entity Framework)
W tym temacie opisano zagadnienia dotyczące zabezpieczeń, które są specyficzne dla opracowywania, wdrażania i uruchamiania aplikacji Entity Framework. Należy również postępować zgodnie z zaleceniami dotyczącymi tworzenia bezpiecznych aplikacji .NET Framework. Aby uzyskać więcej informacji, zobacz [Omówienie zabezpieczeń](../security-overview.md).  
  
## <a name="general-security-considerations"></a>Ogólne zagadnienia dotyczące zabezpieczeń  
 Poniższe zagadnienia dotyczące zabezpieczeń dotyczą wszystkich aplikacji, które używają Entity Framework.  
  
#### <a name="use-only-trusted-data-source-providers"></a>Używaj tylko zaufanych dostawców źródeł danych.  
 Aby można było komunikować się ze źródłem danych, dostawca musi wykonać następujące czynności:  
  
- Odbierz parametry połączenia z Entity Framework.  
  
- Przetłumacz drzewo poleceń na natywny język zapytań źródła danych.  
  
- Tworzenie i zwracanie zestawów wyników.  
  
 Podczas operacji logowania informacje oparte na haśle użytkownika są przesyłane do serwera za pośrednictwem bibliotek sieciowych bazowego źródła danych. Złośliwy dostawca może ukraść poświadczenia użytkownika, generować złośliwe zapytania lub naruszać zestaw wyników.  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>Szyfruj połączenie, aby chronić poufne dane.  
 Entity Framework nie obsługuje bezpośrednio szyfrowania danych. Jeśli użytkownicy uzyskują dostęp do danych za pośrednictwem sieci publicznej, aplikacja powinna ustanowić szyfrowane połączenie ze źródłem danych, aby zwiększyć bezpieczeństwo. Aby uzyskać więcej informacji, zobacz dokumentację dotyczącą zabezpieczeń dla źródła danych. Aby uzyskać SQL Server źródło danych, zobacz [szyfrowanie połączeń do SQL Server](https://go.microsoft.com/fwlink/?LinkId=119544).  
  
#### <a name="secure-the-connection-string"></a>Zabezpiecz parametry połączenia.  
 Ochrona dostępu do źródła danych jest jednym z najważniejszych celów związanych z zabezpieczaniem aplikacji. Parametry połączenia przedstawiają potencjalną lukę w zabezpieczeniach, jeśli nie została zabezpieczona lub nieprawidłowo skonstruowana. Gdy przechowujesz informacje o połączeniu w postaci zwykłego tekstu lub utrwalasz je w pamięci, grozi sobie naruszeniem całego systemu. Poniżej przedstawiono zalecane metody zabezpieczania parametrów połączenia:  
  
- Użyj uwierzytelniania systemu Windows ze źródłem danych SQL Server.  
  
     Jeśli używasz uwierzytelniania systemu Windows do nawiązywania połączenia ze źródłem danych SQL Server, parametry połączenia nie zawierają informacji o logowaniu i haśle.  
  
- Szyfruj sekcje plików konfiguracyjnych przy użyciu konfiguracji chronionej.  
  
     ASP.NET udostępnia funkcję o nazwie Protected Configuration, która umożliwia szyfrowanie poufnych informacji w pliku konfiguracji. Chociaż program przeznaczony głównie do ASP.NET, można także użyć konfiguracji chronionej do szyfrowania sekcji plików konfiguracji w aplikacjach systemu Windows. Aby uzyskać szczegółowy opis nowych możliwości konfiguracji ochrony, zobacz [szyfrowanie informacji o konfiguracji za pomocą konfiguracji chronionej](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
- Przechowuj parametry połączenia w zabezpieczonych plikach konfiguracji.  
  
     Nie należy osadzać parametrów połączenia w kodzie źródłowym. Parametry połączenia można przechowywać w plikach konfiguracyjnych, co eliminuje konieczność osadzania ich w kodzie aplikacji. Domyślnie Kreator Entity Data Model przechowuje parametry połączenia w pliku konfiguracyjnym aplikacji. Należy zabezpieczyć ten plik, aby zapobiec nieautoryzowanemu dostępowi.  
  
- Podczas dynamicznego tworzenia połączeń używaj konstruktorów parametrów połączenia.  
  
     W przypadku konieczności konstruowania parametrów połączenia w czasie wykonywania należy <xref:System.Data.EntityClient.EntityConnectionStringBuilder> użyć klasy. Ta klasa konstruktora ciągów pomaga zapobiegać atakom przed iniekcją parametrów połączenia przez sprawdzenie poprawności i ucieczkę nieprawidłowych informacji wejściowych. Aby uzyskać więcej informacji, zobacz [jak: Kompiluj parametry](how-to-build-an-entityconnection-connection-string.md)połączenia usługi EntityConnection. Należy również użyć odpowiedniej klasy konstruktora ciągów, aby utworzyć parametry połączenia źródła danych, które są częścią parametrów połączenia Entity Framework. Aby uzyskać informacje na temat konstruktorów parametrów połączenia dla dostawców ADO.NET, zobacz [konstruktory parametrów połączenia](../connection-string-builders.md).  
  
 Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../protecting-connection-information.md).  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>Nie należy ujawniać EntityConnection niezaufanym użytkownikom.  
 <xref:System.Data.EntityClient.EntityConnection> Obiekt ujawnia parametry połączenia powiązanego połączenia. Użytkownik mający dostęp do <xref:System.Data.EntityClient.EntityConnection> obiektu może również <xref:System.Data.ConnectionState> zmienić połączenie bazowe. <xref:System.Data.EntityClient.EntityConnection> Klasa nie jest bezpieczna wątkowo.  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>Nie przekazuj połączeń poza kontekstem zabezpieczeń.  
 Po nawiązaniu połączenia nie należy go przekazywać poza kontekstem zabezpieczeń. Na przykład jeden wątek z uprawnieniem do otwierania połączenia nie powinien przechowywać połączenia w globalnej lokalizacji. Jeśli połączenie jest dostępne w lokalizacji globalnej, inny złośliwy wątek może korzystać z otwartego połączenia bez zezwolenia na jego jawne przyznanie.  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>Należy pamiętać, że informacje logowania i hasła mogą być widoczne w zrzucie pamięci.  
 Gdy w parametrach połączenia są podane informacje o logowaniu i haśle źródła danych, te informacje są przechowywane w pamięci, dopóki odzyskiwanie pamięci nie zostanie odzyskane. Uniemożliwia to ustalenie, kiedy ciąg hasła nie jest już w pamięci. Jeśli aplikacja ulegnie awarii, plik zrzutu pamięci może zawierać poufne informacje o zabezpieczeniach, a użytkownik uruchamiający aplikację i dowolny użytkownik mający dostęp administracyjny do komputera może wyświetlić plik zrzutu pamięci. Użyj uwierzytelniania systemu Windows na potrzeby połączeń do Microsoft SQL Server.  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>Udziel użytkownikom tylko niezbędnych uprawnień w źródle danych.  
 Administrator źródła danych powinien udzielić użytkownikom tylko niezbędnych uprawnień. [!INCLUDE[esql](../../../../../includes/esql-md.md)] Mimo że nie obsługuje instrukcji DML, które modyfikują dane, takie jak INSERT, Update lub DELETE, użytkownicy mogą nadal uzyskiwać dostęp do tego połączenia ze źródłem danych. Złośliwy użytkownik może użyć tego połączenia do wykonywania instrukcji DML w języku macierzystym źródła danych.  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>Uruchamianie aplikacji z minimalnymi uprawnieniami.  
 Po umożliwieniu uruchamiania aplikacji zarządzanej z uprawnieniem pełnego zaufania .NET Framework nie ogranicza dostępu aplikacji do komputera. Może to spowodować, że luka w zabezpieczeniach w aplikacji spowoduje naruszenie całego systemu. Aby korzystać z zabezpieczeń dostępu kodu i innych mechanizmów zabezpieczeń w .NET Framework, należy uruchamiać aplikacje przy użyciu uprawnień częściowej relacji zaufania i z minimalnym zestawem uprawnień, które są potrzebne, aby umożliwić działanie aplikacji. Następujące uprawnienia dostępu do kodu to minimalne uprawnienia wymagane przez aplikację Entity Framework:  
  
- <xref:System.Security.Permissions.FileIOPermission>: <xref:System.Security.Permissions.FileIOPermissionAccess.Write> aby otworzyć określone pliki metadanych lub <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> przeszukać katalog dla plików metadanych.  
  
- <xref:System.Security.Permissions.ReflectionPermission>: <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> do obsługi zapytań LINQ to Entities.  
  
- <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState.Unrestricted> do <xref:System.Transactions> rejestracji<xref:System.Transactions.Transaction>w usłudze.  
  
- <xref:System.Security.Permissions.SecurityPermission>: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> aby serializować wyjątki przy <xref:System.Runtime.Serialization.ISerializable> użyciu interfejsu.  
  
- Uprawnienie do otwierania połączenia z bazą danych i wykonywania poleceń względem bazy danych, na <xref:System.Data.SqlClient.SqlClientPermission> przykład dla bazy danych SQL Server.  
  
 Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../code-access-security.md).  
  
#### <a name="do-not-install-untrusted-applications"></a>Nie instaluj aplikacji niezaufanych.  
 Entity Framework nie wymusza żadnych uprawnień zabezpieczeń i wywoła kod obiektu danych podany przez użytkownika w procesie niezależnie od tego, czy jest on zaufany, czy nie. Upewnij się, że uwierzytelnianie i autoryzacja klienta są wykonywane przez magazyn danych i aplikację.  
  
#### <a name="restrict-access-to-all-configuration-files"></a>Ogranicz dostęp do wszystkich plików konfiguracji.  
 Administrator musi ograniczyć dostęp do zapisu do wszystkich plików, które określają konfigurację dla aplikacji, w tym do enterprisesec. config, Security. config, Machine. conf i \< *aplikacji*pliku konfiguracji aplikacji >. plik exe. config.  
  
 Niezmienna nazwa dostawcy jest modyfikowalna w pliku App. config. Aplikacja kliencka musi mieć obowiązek uzyskiwania dostępu do podstawowego dostawcy za pośrednictwem standardowego modelu fabryki dostawców przy użyciu silnej nazwy.  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>Ogranicz uprawnienia do modelu i plików mapowania.  
 Administrator musi ograniczyć dostęp do zapisu do modelu i plików mapowania (. edmx,. csdl,. ssdl i. MSL) tylko do użytkowników, którzy modyfikują model lub mapowania. Entity Framework wymaga tylko odczytu do tych plików w czasie wykonywania. Administrator powinien również ograniczyć dostęp do warstwy obiektów i wstępnie skompilowanych plików kodu źródłowego, które są generowane przez narzędzia Entity Data Model.  
  
## <a name="security-considerations-for-queries"></a>Zagadnienia dotyczące zabezpieczeń dotyczące zapytań  
 Podczas wykonywania zapytania dotyczącego modelu koncepcyjnego stosowane są następujące zagadnienia dotyczące zabezpieczeń. Te zagadnienia dotyczą [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytań korzystających z EntityClient i do zapytań obiektów przy [!INCLUDE[esql](../../../../../includes/esql-md.md)]użyciu metod LINQ, i konstruktora zapytań.  
  
#### <a name="prevent-sql-injection-attacks"></a>Zapobiegaj atakom iniekcji SQL.  
 Aplikacje często pobierają zewnętrzne dane wejściowe (od użytkownika lub innego agenta zewnętrznego) i wykonują działania na podstawie tych danych wejściowych. Wszelkie dane wejściowe bezpośrednio lub pośrednio pochodzące od użytkownika lub zewnętrznego agenta mogą zawierać zawartość, która używa składni języka docelowego w celu wykonywania nieautoryzowanych akcji. Gdy język docelowy to Structured Query Language (SQL), taki jak Transact-SQL, to manipulowanie jest znane jako atak iniekcji SQL. Złośliwy użytkownik może wstrzyknąć polecenia bezpośrednio do zapytania i usunąć tabelę bazy danych, spowodować odmowę usługi lub w inny sposób zmienić charakter wykonywanej operacji.  
  
- [!INCLUDE[esql](../../../../../includes/esql-md.md)]ataki z iniekcją:  
  
     Ataki iniekcji SQL można wykonać w [!INCLUDE[esql](../../../../../includes/esql-md.md)] programie, dostarczając złośliwe dane wejściowe do wartości, które są używane w predykacie zapytania i w nazwach parametrów. Aby uniknąć ryzyka iniekcji kodu SQL, nigdy nie należy łączyć danych wejściowych użytkownika [!INCLUDE[esql](../../../../../includes/esql-md.md)] z tekstem polecenia.  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)]zapytania akceptują parametry wszędzie tam, gdzie literały są akceptowane. Zamiast dodawać literały z zewnętrznego agenta bezpośrednio do zapytania, należy użyć sparametryzowanych zapytań. Należy również rozważyć użycie [metod konstruktora zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896238(v=vs.100)) do bezpiecznego konstruowania Entity SQL.  
  
- Ataki z iniekcją LINQ to Entities:  
  
     Chociaż kompozycja zapytania jest możliwa w LINQ to Entities, jest wykonywana za pomocą interfejsu API modelu obiektów. W przeciwieństwie [!INCLUDE[esql](../../../../../includes/esql-md.md)] do zapytań, LINQ to Entities zapytania nie są złożone przy użyciu manipulowania ciągami ani łączenia, i nie są podatne na tradycyjne ataki iniekcji SQL.  
  
#### <a name="prevent-very-large-result-sets"></a>Zapobiegaj bardzo dużym zestawom wyników.  
 Bardzo duży zestaw wyników może spowodować zamknięcie systemu klienta, jeśli klient wykonuje operacje, które zużywają zasoby proporcjonalnie do rozmiaru zestawu wyników. Nieoczekiwane duże zestawy wyników mogą wystąpić w następujących warunkach:  
  
- W zapytaniach dotyczących dużej bazy danych, które nie zawierają odpowiednich warunków filtrowania.  
  
- W zapytaniach, które tworzą sprzężenia kartezjańskiego na serwerze.  
  
- W zagnieżdżonych [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytaniach.  
  
 W przypadku przyjmowania danych wejściowych użytkownika należy upewnić się, że dane wejściowe nie mogą spowodować, że zestawy wyników będą większe niż to, co system może obsłużyć. Możesz również użyć <xref:System.Linq.Queryable.Take%2A> metody w LINQ to Entities lub operator [Limit](./language-reference/limit-entity-sql.md) w [!INCLUDE[esql](../../../../../includes/esql-md.md)] , aby ograniczyć rozmiar zestawu wyników.  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>Unikaj zwracania wyników w interfejsie IQueryable podczas ujawniania metod potencjalnie niezaufanym wywołującym.  
 Należy unikać <xref:System.Linq.IQueryable%601> powrotu typów z metod, które są dostępne dla potencjalnie niezaufanych wywołujących, z następujących powodów:  
  
- Konsument zapytania, który ujawnia <xref:System.Linq.IQueryable%601> typ, może wywoływać metody w wyniku, który uwidacznia bezpieczne dane lub zwiększa rozmiar zestawu wyników. Rozważmy na przykład następującą sygnaturę metody:  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     Odbiorca tego zapytania może wywołać `.Include("Orders")` zwracaną `IQueryable<Customer>` wartość, aby pobrać dane, które nie zostały ujawnione. Można to uniknąć przez zmianę zwracanego typu metody na <xref:System.Collections.Generic.IEnumerable%601> i wywołanie metody (na przykład `.ToList()`), która materializuje wyniki.  
  
- Ponieważ <xref:System.Linq.IQueryable%601> zapytania są wykonywane, gdy wyniki są powtarzane, konsument zapytania, który <xref:System.Linq.IQueryable%601> ujawnia typ, może przechwytywać wyjątki, które są generowane. Wyjątki mogą zawierać informacje, które nie są przeznaczone dla konsumenta.  
  
## <a name="security-considerations-for-entities"></a>Zagadnienia dotyczące zabezpieczeń jednostek  
 Podczas generowania i pracy z typami jednostek należy wziąć pod uwagę następujące zagadnienia dotyczące zabezpieczeń.  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>Nie udostępniaj obiektu ObjectContext między domenami aplikacji.  
 <xref:System.Data.Objects.ObjectContext> Udostępnianie z więcej niż jedną domeną aplikacji może ujawnić informacje w parametrach połączenia. Zamiast tego należy przenieść obiekty serializowane lub wykresy obiektów do innej domeny aplikacji, a następnie dołączyć te obiekty do <xref:System.Data.Objects.ObjectContext> domeny w tej domenie. Aby uzyskać więcej informacji, zobacz [Serializowanie obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
#### <a name="prevent-type-safety-violations"></a>Zapobiegaj naruszeniom bezpieczeństwa typów.  
 W przypadku naruszenia bezpieczeństwa typów Entity Framework nie gwarantuje integralności danych w obiektach. Naruszenia bezpieczeństwa typów mogą wystąpić, Jeśli zezwolisz niezaufanym aplikacjom na korzystanie z pełnego zaufania dostępu do kodu.  
  
#### <a name="handle-exceptions"></a>Obsługa wyjątków.  
 Dostęp do metod i właściwości <xref:System.Data.Objects.ObjectContext> w bloku try-catch. Przechwytywanie wyjątków zapobiega nieobsługiwanym wyjątkom od udostępniania wpisów w <xref:System.Data.Objects.ObjectStateManager> lub informacji o modelu (takich jak nazwy tabel) użytkownikom aplikacji.  
  
## <a name="security-considerations-for-aspnet-applications"></a>Zagadnienia dotyczące zabezpieczeń aplikacji ASP.NET  

Podczas pracy ze ścieżkami w aplikacjach ASP.NET należy wziąć pod uwagę następujące kwestie.  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>Sprawdź, czy host sprawdza ścieżki.  
 Gdy jest używany ciąg podstawienia (ujętywsymbolepotoku),ADO.NETsprawdza,czyrozpoznanaścieżkajestobsługiwana.`|DataDirectory|` Na przykład, ".." jest niedozwolone w `DataDirectory`tle. To samo sprawdzenie w celu rozpoznania głównego operatora aplikacji sieci Web`~`() jest wykonywane przez proces obsługujący ASP.NET. Program IIS wykonuje tę kontrolę; jednak hosty inne niż usługi IIS mogą nie sprawdzać, czy rozpoznana ścieżka jest obsługiwana. Należy znać zachowanie hosta, na którym jest wdrażana aplikacja Entity Framework.  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>Nie należy tworzyć założeń dotyczących rozwiązanych nazw ścieżek.  
 Chociaż wartości, do których operator główny (`~`) `DataDirectory` i ciąg podstawienia powinny być stałe w czasie wykonywania aplikacji, Entity Framework nie ograniczają hosta do modyfikowania tych wartości.  
  
#### <a name="verify-the-path-length-before-deployment"></a>Przed wdrożeniem sprawdź długość ścieżki.  
 Przed wdrożeniem aplikacji Entity Framework należy upewnić się, że wartości operatora głównego (~) i `DataDirectory` ciągu podstawienia nie przekraczają limitów długości ścieżki w systemie operacyjnym. Dostawcy danych ADO.NET nie zapewniają, że długość ścieżki należy do zakresu prawidłowych limitów.  
  
## <a name="security-considerations-for-adonet-metadata"></a>Zagadnienia dotyczące zabezpieczeń dla metadanych ADO.NET  
 Podczas generowania i pracy z modelem i mapowaniem plików obowiązują następujące zagadnienia dotyczące zabezpieczeń.  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>Nie ujawniaj poufnych informacji za poorednictwem rejestrowania.  
Składniki usługi metadanych ADO.NET nie rejestrują żadnych prywatnych informacji. Jeśli istnieją wyniki, których nie można zwrócić ze względu na ograniczenia dostępu, systemy zarządzania bazami danych i systemy plików powinny zwracać zero wyników zamiast podnieść wyjątek, który może zawierać poufne informacje.  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>Nie Akceptuj obiektów MetadataWorkspace z niezaufanych źródeł.  
 Aplikacje nie powinny akceptować wystąpień <xref:System.Data.Metadata.Edm.MetadataWorkspace> klasy z niezaufanych źródeł. Zamiast tego należy jawnie utworzyć i wypełnić obszar roboczy z takiego źródła.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Zagadnienia dotyczące wdrażania](deployment-considerations.md)
- [Zagadnienia dotyczące migracji](migration-considerations.md)
