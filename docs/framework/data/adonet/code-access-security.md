---
title: Zabezpieczenia dostępu kodu i ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: ea5dbcc128f97ebbec72273378adb042bbe34e1e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="code-access-security-and-adonet"></a>Zabezpieczenia dostępu kodu i ADO.NET
.NET Framework oferuje opartej na rolach zabezpieczeń, a także zabezpieczenia dostępu kodu (CAS), które są implementowane za pomocą wspólnej infrastruktury dostarczanych przez środowisko uruchomieniowe języka wspólnego (CLR). Większość aplikacji na świecie kodu niezarządzanego, wykonywane za pomocą uprawnienia użytkownika lub podmiot zabezpieczeń. W związku z tym systemów komputerowych może być uszkodzony i prywatnych danych zagrożone, gdy złośliwe lub wypełnione błąd oprogramowania jest uruchamiane przez użytkownika z podniesionymi uprawnieniami.  
  
 Z kolei wykonywania kodu zarządzanego w programie .NET Framework obejmuje zabezpieczeń dostępu kodu, co dotyczy wyłącznie kodu. Określa, czy kod może zostać uruchomiony lub nie zależy od pochodzenia kodu lub innych aspektów tożsamości kodu, nie wyłącznie tożsamości podmiotu zabezpieczeń. Zmniejsza to prawdopodobieństwo, że zarządzane precyzyjnym kodu.  
  
## <a name="code-access-permissions"></a>Uprawnienia dostępu kodu  
 Podczas wykonywania kodu stanowi dowód obliczonego przez system zabezpieczeń CLR. Zwykle to świadectwo obejmuje źródła kodu, w tym adresy URL, lokacji i strefy i podpisy cyfrowe, które zapewniają tożsamość zestawu.  
  
 Środowisko CLR umożliwia kod, aby wykonać te operacje, które kod ma uprawnienia do wykonania. Kod może zażądać uprawnień, a te żądania są honorowane na podstawie zasad zabezpieczeń ustawionych przez administratora.  
  
> [!NOTE]
>  Kod wykonywany w środowisku CLR nie można udzielić uprawnienia do samej siebie. Na przykład kod mogą żądać i przyznać uprawnienia mniej niż zasady zabezpieczeń, ale będzie można nigdy nie przyznano więcej uprawnień. Podczas udzielania uprawnień, zaczynać się w ogóle nie ma uprawnień, a następnie dodaj najwęższym uprawnienia dla określonego zadania wykonywane. Następnie odrzuciła pojedyncze pliki, począwszy od wszystkie uprawnienia prowadzi do niebezpieczne aplikacje, które mogą zawierać luk w zabezpieczeniach niezamierzone z udzielanie więcej uprawnień niż jest to wymagane. Aby uzyskać więcej informacji, zobacz [NIB: Konfigurowanie zasad zabezpieczeń](http://msdn.microsoft.com/library/0f130bcd-1bba-4346-b231-0bcca7dab1a4) i [NIB: Zarządzanie zasadami dotyczącymi zabezpieczeń](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9).  
  
 Istnieją trzy typy uprawnień dostępu do kodu:  
  
-   `Code access permissions` pochodzić od <xref:System.Security.CodeAccessPermission> klasy. Uprawnienia są wymagane, aby uzyskać dostęp do chronionych zasobów, takie jak pliki i zmienne środowiskowe i wykonywanie operacji chronionych, takich jak uzyskiwanie dostępu do kodu niezarządzanego.  
  
-   `Identity permissions` reprezentuje właściwości, które identyfikują zestawu. Przyznano uprawnienia do zestawu na podstawie dowodów, które obejmują elementy, takie jak podpisu cyfrowego lub pochodzenie kod. Uprawnienia dotyczące tożsamości również pochodzić od <xref:System.Security.CodeAccessPermission> klasy podstawowej.  
  
-   `Role-based security permissions` są na podstawie tego, czy podmiot zabezpieczeń ma określoną tożsamością lub jest członkiem określonej roli. <xref:System.Security.Permissions.PrincipalPermission> Klasa umożliwia kontroli zarówno uprawnienia deklaratywne i nadrzędnych względem aktywny podmiot zabezpieczeń.  
  
 Aby ustalić, czy kod jest autoryzowany do uzyskania dostępu do zasobu lub wykonania operacji, system zabezpieczeń środowiska uruchomieniowego przechodzi przez stos wywołań, porównanie uprawnienia nadanego każdy obiekt wywołujący, aby uprawnienia są wymagane. Jeśli każdego obiektu wywołującego w stosie wywołań nie ma wymaganego uprawnienia <xref:System.Security.SecurityException> jest generowany, a w przypadku odmowy dostępu.  
  
### <a name="requesting-permissions"></a>Żądanie uprawnień  
 Celem żądania uprawnień jest poinformowanie uprawnienia, które aplikacja wymaga, aby można było uruchomić i zapewnia, że otrzyma uprawnienia faktycznie wymagane przez środowisko uruchomieniowe. Na przykład jeśli aplikacja wymaga do zapisywania danych na dysku lokalnym, wymaga <xref:System.Security.Permissions.FileIOPermission>. Jeśli nie zostało udzielone uprawnienie, aplikacja zakończy się niepowodzeniem podczas próby zapisu na dysku. Jednak jeśli aplikacja żąda `FileIOPermission` i nie udzielono uprawnienia, aplikacja zostanie wygenerowany wyjątek na początku i nie zostanie załadowany.  
  
 W przypadku której aplikacja musi tylko do odczytu danych z dysku możesz zażądać, że go nigdy nie zostać przyznane uprawnienia do zapisu. W przypadku usterki lub złośliwymi atakami kodu nie może uszkodzić dane, na którym działa. Aby uzyskać więcej informacji, zobacz [NIB: żąda uprawnienia](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
## <a name="role-based-security-and-cas"></a>Zabezpieczenia oparte na rolach i urzędy certyfikacji  
 Implementacja oparta na rolach zabezpieczeń i zabezpieczeń dostępu do kodu (CAS) zwiększa ogólną zabezpieczeń aplikacji. Oparta na rolach zabezpieczeń może opierać się na konto systemu Windows lub tożsamość niestandardowa, udostępniając informacji na temat podmiotu zabezpieczeń bieżącego wątku. Ponadto aplikacje często są wymagane w celu zapewnienia dostępu do danych i zasobów na podstawie poświadczeń dostarczonych przez użytkownika. Zazwyczaj takie aplikacje Sprawdź rolę użytkownika i umożliwiają dostęp do zasobów na podstawie tych ról.  
  
 Zabezpieczenia oparte na rolach umożliwia składnik, aby zidentyfikować bieżąca liczba użytkowników i ich skojarzone role w czasie wykonywania. Te informacje jest następnie mapowany do określania zestawu uprawnień w czasie wykonywania za pomocą zasad CAS. W domenie określonej aplikacji hosta można zmienić domyślnych zasad zabezpieczeń opartych na rolach i ustawianie podmiotu zabezpieczeń domyślny, który reprezentuje użytkownika oraz role skojarzone z użytkownikiem.  
  
 Środowisko CLR używa uprawnienia do implementacji jego mechanizmu wymuszania ograniczeń kodu zarządzanego. Uprawnienia zabezpieczeń opartych na rolach udostępniają mechanizm wykrywania, czy użytkownik (lub agenta, działając w imieniu użytkownika) ma określonej tożsamości lub jest członkiem określonej roli. Aby uzyskać więcej informacji, zobacz [uprawnień zabezpieczeń](http://msdn.microsoft.com/library/b03757b4-e926-4196-b738-3733ced2bda0).  
  
 W zależności od typu aplikacji, które tworzysz należy również rozważyć wdrożenie oparte na rolach uprawnienia w bazie danych. Aby uzyskać więcej informacji dotyczących zabezpieczeń opartych na rolach w programie SQL Server, zobacz [zabezpieczeń serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Zestawy  
 Zestawy stanowią podstawową jednostkę wdrożenia, kontroli wersji, ponownemu, zakresu aktywacji i uprawnień zabezpieczeń dla aplikacji .NET Framework. Zestaw zawiera kolekcję typów i zasobów, które są przeznaczone do współpracują ze sobą i utworzenia jednostki logicznej funkcji. Do środowiska CLR typ nie istnieje poza kontekstem zestawu. Aby uzyskać więcej informacji na temat tworzenia i wdrażania zestawy, zobacz [programowanie za pomocą zestawów](../../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
### <a name="strong-naming-assemblies"></a>Silnych nazw zestawów  
 Silnej nazwy lub podpisu cyfrowego, składa się z tożsamości zestawu, w tym jego nazwa zwykłego tekstu, numer wersji i informacji o kulturze (jeśli jest dostępny), oraz klucz publiczny i podpis cyfrowy. Podpis cyfrowy jest generowany na podstawie pliku zestawu przy użyciu odpowiedniego klucza prywatnego. Plik zestawu zawiera manifest zestawu, który zawiera nazwy i wartości skrótu wszystkie pliki wchodzące w skład zestawu.  
  
 Silne nazewnictwo zestawu daje aplikację lub składnik unikatową tożsamość używaną przez inne oprogramowanie do jawnie odwoływać się do niego. Silne nazwy chroni zestawy przed fałszowania przez zestaw, który zawiera szkodliwy kod. Nazewnictwo silne gwarantuje również versioning spójności między różnymi wersjami składnika. Należy silnych nazwach, które zostaną wdrożone do globalnej pamięci podręcznej zestawów (GAC). Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="partial-trust-in-adonet-20"></a>Częściowej relacji zaufania w ADO.NET 2.0  
 W ADO.NET 2.0 .NET Framework Data Provider for SQL Server, dostawcy danych programu .NET Framework dla OLE DB, .NET Framework Data Provider for ODBC i .NET Framework Data Provider for Oracle można teraz wszystkie działania w środowiskach częściowo zaufany. W poprzednich wersjach programu .NET Framework, tylko <xref:System.Data.SqlClient> jest obsługiwana w aplikacjach mniej niż pełnego zaufania.  
  
 Co najmniej częściowo zaufanych aplikacji, przy użyciu dostawcy programu SQL Server musi mieć wykonanie i <xref:System.Data.SqlClient.SqlClientPermission> uprawnienia.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Właściwości atrybutów uprawnień dla częściowej relacji zaufania  
 Scenariusze częściowej relacji zaufania, można użyć <xref:System.Data.SqlClient.SqlClientPermissionAttribute> elementy członkowskie, aby jeszcze bardziej ograniczyć możliwości, które są dostępne dla dostawcy danych programu .NET Framework dla programu SQL Server.  
  
 Poniższa tabela zawiera listę dostępnych <xref:System.Data.SqlClient.SqlClientPermissionAttribute> właściwości i ich opisy:  
  
|Właściwość atrybutu uprawnień|Opis|  
|-----------------------------------|-----------------|  
|`Action`|Pobiera lub ustawia akcję zabezpieczeń. Dziedziczone z <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Włącza lub wyłącza użycie pustego hasła w parametrach połączenia. Prawidłowe wartości to `true` (Aby włączyć użycie pustego hasła) i `false` (Aby zablokować używanie pustych haseł). Dziedziczone z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|Określa ciąg dozwolone połączenia. Można określić wiele parametrów połączenia. **Uwaga:** nie dołączaj nazwy użytkownika i hasła w ciągu połączenia. W tej wersji nie można zmienić ograniczenia ciągu połączenia za pomocą narzędzia konfiguracji programu .NET Framework. <br /><br /> Dziedziczone z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|Określa parametry ciągu połączenia, które ma być dozwolony lub niedozwolony. Parametry ciągu połączenia są identyfikowane w formularzu  *\<parametru name > =*. Można określić wiele parametrów, rozdzielone średnikami (;). **Uwaga:** Jeśli nie określisz `KeyRestrictions`, ale zostanie ustawiona `KeyRestrictionBehavior` właściwości `AllowOnly` lub `PreventUsage`, bez parametrów ciągu dodatkowego połączenia są dozwolone. Dziedziczone z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|Określa parametry połączenia w ciągu jako tylko dodatkowe parametry, które są niedozwolone (`AllowOnly`), lub określa dodatkowe parametry, które nie są dozwolone (`PreventUsage`). `AllowOnly` jest ustawieniem domyślnym. Dziedziczone z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Pobiera unikatowy identyfikator dla tego atrybutu w przypadku zaimplementowania w klasie pochodnej. Dziedziczone z <xref:System.Attribute>.|  
|`Unrestricted`|Wskazuje, czy zadeklarowano nieograniczone uprawnienia do tego zasobu. Dziedziczone z <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### <a name="connectionstring-syntax"></a>Składnia ConnectionString  
 W poniższym przykładzie pokazano sposób użycia `connectionStrings` element pliku konfiguracji, aby zezwolić tylko określony ciąg połączenia do użycia. Zobacz [parametry połączenia](../../../../docs/framework/data/adonet/connection-strings.md) Aby uzyskać więcej informacji na przechowywanie i pobieranie parametrów połączenia z plików konfiguracyjnych.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>Składnia KeyRestrictions  
 Poniższy przykład umożliwia włączenie tych samych parametrach połączenia, umożliwia korzystanie z `Encrypt` i `Packet``Size` parametry połączenia opcje, lecz ogranicza korzystanie z innych opcji ciągu połączenia.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>KeyRestrictionBehavior ze składnią PreventUsage  
 Poniższy przykład umożliwia te same parametry połączenia i umożliwia wszystkie pozostałe parametry połączenia, z wyjątkiem `User Id`, `Password` i `Persist Security Info`.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>KeyRestrictionBehavior ze składnią AllowOnly  
 Poniższy przykład umożliwia włączenie dwa parametry połączenia, które zawierają również `Initial Catalog`, `Connection Timeout`, `Encrypt`, i `Packet Size` parametrów. Wszystkie pozostałe parametry ciągu połączenia są ograniczone.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
  
  <add name="DatabaseConnection2"   
    connectionString="Data Source=SqlServer2;Initial   
    Catalog=Northwind2;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Włączanie częściowej relacji zaufania z zestawem uprawnień niestandardowych  
 Aby włączyć korzystanie z <xref:System.Data.SqlClient> uprawnienia dla określonej strefy, administrator systemu musi utworzyć niestandardowe uprawnienia ustawić i ustaw go jako zestawu uprawnień dla określonej strefy. Domyślne zestawy uprawnień, takich jak `LocalIntranet`, nie może być modyfikowany. Na przykład, aby uwzględnić <xref:System.Data.SqlClient> uprawnienia dla kodu, który ma <xref:System.Security.Policy.Zone> z `LocalIntranet`, administrator systemu można skopiować zestawu uprawnień dla `LocalIntranet`, zmień jego nazwę na "CustomLocalIntranet", Dodaj <xref:System.Data.SqlClient> zaimportować uprawnienia zestawu przy użyciu uprawnień CustomLocalIntranet [Caspol.exe (narzędzie zasad zabezpieczenia dostępu kodu)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)i ustaw zestaw uprawnień `LocalIntranet_Zone` do CustomLocalIntranet.  
  
### <a name="sample-permission-set"></a>Przykładowy zestaw uprawnień  
 Poniżej przedstawiono przykładowe zestawu uprawnień dla dostawcy danych programu .NET Framework dla programu SQL Server w scenariuszu częściowo zaufany. Aby uzyskać informacje o tworzeniu zestawów uprawnień niestandardowych, zobacz [NIB: Konfigurowanie uprawnień ustawia przy użyciu Caspol.exe](http://msdn.microsoft.com/library/94e2625e-21ad-4038-af36-6d1f9df40a57).  
  
```xml  
<PermissionSet class="System.Security.NamedPermissionSet"  
  version="1"  
  Name="CustomLocalIntranet"  
  Description="Custom permission set given to applications on  
    the local intranet">  
  
<IPermission class="System.Data.SqlClient.SqlClientPermission, System.Data, Version=2.0.0000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
version="1"  
AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Integrated Security=true;"  
 KeyRestrictions="Initial Catalog=;Connection Timeout=;  
   Encrypt=;Packet Size=;"   
 KeyRestrictionBehavior="AllowOnly" />  
 </IPermission>  
</PermissionSet>  
```  
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>Weryfikowanie przy użyciu uprawnień zabezpieczeń dostępu kodu ADO.NET  
 W scenariuszach częściowo zaufane, można wymagają uprawnień urzędów certyfikacji dla określonej metody w kodzie, określając <xref:System.Data.SqlClient.SqlClientPermissionAttribute>. Jeśli to uprawnienie jest niedozwolone przez zasady zabezpieczeń z ograniczeniami w celu, jest zwracany wyjątek, przed uruchomieniem kodu. Aby uzyskać więcej informacji dotyczących zasad zabezpieczeń, zobacz [NIB: Zarządzanie zasadami dotyczącymi zabezpieczeń](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9) i [NIB: najlepszych rozwiązań dotyczących zasad zabezpieczeń](http://msdn.microsoft.com/library/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak napisać kod, który wymaga ciągu określonego połączenia. Symuluje, odmawianie nieograniczonych uprawnień do <xref:System.Data.SqlClient>, które administrator systemu może zaimplementować przy użyciu zasad CAS w świecie rzeczywistym.  
  
> [!IMPORTANT]
>  Podczas projektowania uprawnienia urzędów certyfikacji dla ADO.NET, poprawne wzorzec jest rozpoczynać się od przypadku najbardziej restrykcyjne (nie uprawnienia we wszystkich), a następnie dodaj określone uprawnienia, które są wymagane dla określonego zadania, które musi wykonać kod. Wzorzec przeciwnej, następnie odrzuciła określone uprawnienia, począwszy od wszystkich uprawnień nie jest bezpieczne, ponieważ istnieje wiele sposobów wyrażenia te same parametry połączenia. Na przykład, jeśli rozpoczynać wszystkie uprawnienia, a następnie spróbuj zezwolić na korzystanie z parametrów połączenia "serwera = someserver", ciąg "server=someserver.mycompany.com" nadal będzie dozwolony. Należy zawsze uruchomić przyznając w ogóle nie ma uprawnień, można zmniejszyć prawdopodobieństwo, że istnieją luk w zestaw uprawnień.  
  
 Poniższy kod przedstawia sposób `SqlClient` wykonuje żądanie zabezpieczeń, która zgłasza <xref:System.Security.SecurityException> Jeśli odpowiednie uprawnienia urzędów certyfikacji, które nie są stosowane. <xref:System.Security.SecurityException> Dane wyjściowe są wyświetlane w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Powinny pojawić się te dane wyjściowe w oknie konsoli:  
  
```  
Failed, as expected: <IPermission class="System.Data.SqlClient.  
SqlClientPermission, System.Data, Version=2.0.0.0,   
  Culture=neutral, PublicKeyToken=b77a5c561934e089" version="1"  
  AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Initial Catalog=  
  Northwind;Integrated Security=SSPI" KeyRestrictions=""  
KeyRestrictionBehavior="AllowOnly"/>  
</IPermission>  
  
Connection opened, as expected.  
Failed, as expected: Request failed.  
```  
  
## <a name="interoperability-with-unmanaged-code"></a>Współdziałanie z kodem niezarządzanym  
 Kod uruchamiany poza środowiskiem CLR jest nazywany kodu niezarządzanego. W związku z tym mechanizmy zabezpieczeń, takich jak urzędy certyfikacji nie można zastosować do kodu niezarządzanego. Składniki modelu COM, interfejsy ActiveX i funkcji Win32 API są przykłady kodu niezarządzanego. Zabezpieczenia specjalne kwestie podczas wykonywania kodu niezarządzanego, aby nie stanowią zagrożenia zabezpieczeń ogólną aplikacji. Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md).  
  
 .NET Framework obsługuje także zgodności z poprzednimi wersjami istniejących składników COM dzięki dostępowi do COM interop. COM — składniki można zastosować do aplikacji autonomicznej .NET Framework za pomocą narzędzi międzyoperacyjnego COM do importowania odpowiednich typów COM. Po zaimportowaniu typów COM są gotowe do użycia. Współdziałanie z COM umożliwia również COM klientom dostęp do kodu zarządzanego, eksportowanie metadanych zestawu do biblioteki typów i rejestrowanie zarządzanego składnika jako składnik modelu COM. Aby uzyskać więcej informacji, zobacz [zaawansowane współdziałanie COM](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Pave – zabezpieczeń w trybie macierzystym i kodu platformy .NET Framework](http://msdn.microsoft.com/library/bd61be84-c143-409a-a75a-44253724f784)  
 [Zabezpieczenia dostępu kodu](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)  
 [Zabezpieczenia oparte na rolach](http://msdn.microsoft.com/library/239442e3-5be4-4203-b7fd-793baffea803)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
