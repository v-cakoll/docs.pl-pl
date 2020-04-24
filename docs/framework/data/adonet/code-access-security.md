---
title: Zabezpieczenia dostępu kodu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: 7b0f269bd4dce8ddaaaa72c3760a4d7a0e3eb8b9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646013"
---
# <a name="code-access-security-and-adonet"></a>Zabezpieczenia dostępu kodu i ADO.NET
Program .NET Framework oferuje zabezpieczenia oparte na rolach, a także zabezpieczenia dostępu do kodu (CAS), które są implementowane przy użyciu wspólnej infrastruktury dostarczanej przez środowisko wykonawcze języka wspólnego (CLR). W świecie kodu niezarządzanego większość aplikacji jest wykonywana z uprawnieniami użytkownika lub podmiotu. W rezultacie systemy komputerowe mogą zostać uszkodzone, a prywatne dane zagrożone, gdy złośliwe lub wypełnione błędami oprogramowanie jest uruchamiane przez użytkownika z podwyższonymi uprawnieniami.  
  
 Z drugiej strony kod zarządzany wykonywany w programie .NET Framework zawiera zabezpieczenia dostępu do kodu, które mają zastosowanie do samego kodu. Czy kod jest dozwolone do uruchomienia lub nie zależy od źródła kodu lub innych aspektów tożsamości kodu, a nie wyłącznie tożsamości podmiotu zabezpieczeń. Zmniejsza to prawdopodobieństwo, że kod zarządzany może być nadużywane.  
  
## <a name="code-access-permissions"></a>Uprawnienia dostępu kodu  
 Po wykonaniu kodu przedstawiono dowody, które są oceniane przez system zabezpieczeń CLR. Zazwyczaj ten dowód obejmuje pochodzenie kodu, w tym adres URL, witryny i strefy i podpisów cyfrowych, które zapewniają tożsamość zestawu.  
  
 CLR umożliwia kod do wykonywania tylko te operacje, które kod ma uprawnienia do wykonywania. Kod może żądać uprawnień, a te żądania są honorowane na podstawie zasad zabezpieczeń ustawionych przez administratora.  
  
> [!NOTE]
> Kod wykonywany w programie CLR nie może udzielić uprawnień do siebie. Na przykład kod może żądać i mieć przyznane mniej uprawnień niż pozwala na to zasady zabezpieczeń, ale nigdy nie zostanie przyznany więcej uprawnień. Podczas udzielania uprawnień, należy rozpocząć bez uprawnień w ogóle, a następnie dodać najwęższe uprawnienia dla określonego zadania wykonywane. Począwszy od wszystkich uprawnień, a następnie odrzucanie poszczególnych prowadzi do niezabezpieczonych aplikacji, które mogą zawierać niezamierzone luki w zabezpieczeniach od przyznania więcej uprawnień niż jest to wymagane. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) i [zarządzania zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
 Istnieją trzy typy uprawnień dostępu do kodu:  
  
- `Code access permissions`pochodzą z <xref:System.Security.CodeAccessPermission> klasy. Uprawnienia są wymagane w celu uzyskania dostępu do chronionych zasobów, takich jak pliki i zmienne środowiskowe, oraz do wykonywania chronionych operacji, takich jak uzyskiwanie dostępu do kodu niezarządzanego.  
  
- `Identity permissions`reprezentują cechy identyfikujące zespół. Uprawnienia są przyznawane zestawowi na podstawie dowodów, które mogą zawierać elementy, takie jak podpis cyfrowy lub skąd pochodzi kod. Uprawnienia tożsamości również pochodzą <xref:System.Security.CodeAccessPermission> z klasy podstawowej.  
  
- `Role-based security permissions`są oparte na tym, czy podmiot zabezpieczeń ma określoną tożsamość lub jest członkiem określonej roli. Klasa <xref:System.Security.Permissions.PrincipalPermission> umożliwia zarówno deklaratywne i imperatywne sprawdzanie uprawnień względem aktywnego podmiotu.  
  
 Aby ustalić, czy kod jest autoryzowany do uzyskiwania dostępu do zasobu lub wykonywania operacji, system zabezpieczeń środowiska wykonawczego przechodzi przez stos wywołań, porównując przyznane uprawnienia każdego obiektu wywołującego z wymaganym uprawnieniem. Jeśli dowolna wywołująca w stosie wywołań <xref:System.Security.SecurityException> nie ma żądanego uprawnienia, a jest odrzucany i dostęp jest odrzucany.  
  
### <a name="requesting-permissions"></a>Żądanie uprawnień  
 Celem żądania uprawnień jest poinformowanie środowiska wykonawczego, które aplikacja wymaga w celu uruchomienia i upewnić się, że otrzymuje tylko uprawnienia, które faktycznie potrzebuje. Na przykład, jeśli aplikacja musi zapisywać dane na <xref:System.Security.Permissions.FileIOPermission>dysku lokalnym, wymaga . Jeśli to uprawnienie nie zostało przyznane, aplikacja zakończy się niepowodzeniem, gdy próbuje zapisać na dysku. Jeśli jednak aplikacja `FileIOPermission` zażąda i że uprawnienie nie zostało przyznane, aplikacja wygeneruje wyjątek na początku i nie zostanie załadowany.  
  
 W scenariuszu, w którym aplikacja musi tylko odczytać dane z dysku, można zażądać, aby nigdy nie przyznano żadnych uprawnień do zapisu. W przypadku błędu lub złośliwego ataku kod nie może uszkodzić danych, na których działa. Aby uzyskać więcej informacji, zobacz [Żądanie uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).  
  
## <a name="role-based-security-and-cas"></a>Zabezpieczenia oparte na rolach i CAS  
 Implementacja zabezpieczeń opartych na rolach i zabezpieczeń dostępu do kodu (CAS) zwiększa ogólne bezpieczeństwo aplikacji. Zabezpieczenia oparte na rolach mogą być oparte na koncie systemu Windows lub tożsamości niestandardowej, dzięki czemu informacje o zabezpieczeń są dostępne dla bieżącego wątku. Ponadto aplikacje są często wymagane do zapewnienia dostępu do danych lub zasobów na podstawie poświadczeń dostarczonych przez użytkownika. Zazwyczaj takie aplikacje sprawdzić rolę użytkownika i zapewnić dostęp do zasobów na podstawie tych ról.  
  
 Zabezpieczenia oparte na rolach umożliwiają składnikowi identyfikowanie bieżących użytkowników i skojarzonych z nimi ról w czasie wykonywania. Te informacje są następnie mapowane przy użyciu zasad CAS w celu określenia zestawu uprawnień przyznanych w czasie wykonywania. W przypadku określonej domeny aplikacji host może zmienić domyślną zasadę zabezpieczeń opartą na rolach i ustawić domyślny podmiot zabezpieczeń reprezentujący użytkownika i role skojarzone z tym użytkownikiem.  
  
 Program CLR używa uprawnień do implementowania mechanizmu wymuszania ograniczeń dotyczących kodu zarządzanego. Uprawnienia zabezpieczeń oparte na rolach zapewniają mechanizm wykrywania, czy użytkownik (lub agent działający w imieniu użytkownika) ma określoną tożsamość lub jest członkiem określonej roli. Aby uzyskać więcej informacji, zobacz [Uprawnienia zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100)).  
  
 W zależności od typu aplikacji, które są budowane, należy również rozważyć implementowanie uprawnień opartych na rolach w bazie danych. Aby uzyskać więcej informacji na temat zabezpieczeń opartych na rolach w programie SQL Server, zobacz [SQL Server Security](./sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Zestawy  
 Zestawy tworzą podstawową jednostkę wdrażania, kontroli wersji, ponownego użycia, zakresu aktywacji i uprawnień zabezpieczeń dla aplikacji .NET Framework. Zestaw zawiera zbiór typów i zasobów, które są zbudowane do współpracy i tworzą logiczną jednostkę funkcjonalności. Do CLR typu nie istnieje poza kontekstem zestawu. Aby uzyskać więcej informacji na temat tworzenia i wdrażania zestawów, zobacz [Programowanie za pomocą zestawów](../../../standard/assembly/index.md).  
  
### <a name="strong-naming-assemblies"></a>Zestawy o silnym nazewnictwie  
 Silna nazwa lub podpis cyfrowy składa się z tożsamości zestawu, która zawiera jego prostą nazwę tekstową, numer wersji i informacje o kulturze (jeśli są dostarczane), a także klucz publiczny i podpis cyfrowy. Podpis cyfrowy jest generowany z pliku zestawu przy użyciu odpowiedniego klucza prywatnego. Plik zestawu zawiera manifest zestawu, który zawiera nazwy i skróty wszystkich plików, które tworzą zestaw.  
  
 Silne nazywanie zestawu nadaje aplikacji lub składnikowi unikatową tożsamość, której inne oprogramowanie może używać do wyraźnego odwoływania się do niego. Silne nazewnictwa strażników zestawy przed fałszowany przez zestaw, który zawiera wrogi kod. Silne nazewnictwo zapewnia również spójność przechowywania wersji między różnymi wersjami składnika. Musisz silne zestawy nazw, które zostaną wdrożone w globalnej pamięci podręcznej zestawów (GAC). Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../standard/assembly/create-use-strong-named.md).  
  
## <a name="partial-trust-in-adonet-20"></a>Częściowe zaufanie do ADO.NET 2.0  
 W ADO.NET 2.0 dostawca danych .NET Framework dla programu SQL Server, dostawca danych .NET Framework dla ole db, dostawca danych .NET Framework dla odbc i dostawca danych .NET Framework dla oracle mogą teraz działać w częściowo zaufanych środowiskach. W poprzednich wersjach programu .NET Framework tylko <xref:System.Data.SqlClient> był obsługiwany w mniej niż pełne zaufanie aplikacji.  
  
 Co najmniej częściowo zaufana aplikacja przy użyciu dostawcy <xref:System.Data.SqlClient.SqlClientPermission> programu SQL Server musi mieć wykonanie i uprawnienia.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Właściwości atrybutu uprawnień dla częściowego zaufania  
 W przypadku scenariuszy częściowego <xref:System.Data.SqlClient.SqlClientPermissionAttribute> zaufania można użyć elementów członkowskich, aby dodatkowo ograniczyć możliwości dostępne dla dostawcy danych programu .NET Framework dla programu SQL Server.  
  
 W poniższej tabeli wymieniono dostępne <xref:System.Data.SqlClient.SqlClientPermissionAttribute> właściwości i ich opisy:  
  
|Właściwość atrybutu uprawnienia|Opis|  
|-----------------------------------|-----------------|  
|`Action`|Pobiera lub ustawia akcję zabezpieczeń. Odziedziczony <xref:System.Security.Permissions.SecurityAttribute>po pliku .|  
|`AllowBlankPassword`|Włącza lub wyłącza użycie pustego hasła w ciągu połączenia. Prawidłowe `true` wartości to (aby umożliwić używanie `false` pustych haseł) i (aby wyłączyć używanie pustych haseł). Odziedziczony <xref:System.Data.Common.DBDataPermissionAttribute>po pliku .|  
|`ConnectionString`|Identyfikuje dozwolony ciąg połączenia. Można zidentyfikować wiele ciągów połączeń. **Uwaga:**  Nie należy dołączać identyfikatora użytkownika ani hasła do ciągu połączenia. W tej wersji nie można zmienić ograniczeń ciągu połączenia za pomocą narzędzia konfiguracyjnego programu .NET Framework. <br /><br /> Odziedziczony <xref:System.Data.Common.DBDataPermissionAttribute>po pliku .|  
|`KeyRestrictions`|Identyfikuje parametry ciągu połączenia, które są dozwolone lub niedozwolone. Parametry ciągu połączenia są identyfikowane w * \<nazwie parametru*formularza>= . Można określić wiele parametrów, rozdzielonych za pomocą średnika (;). **Uwaga:**  `KeyRestrictions`Jeśli nie określisz , `KeyRestrictionBehavior` ale `AllowOnly` ustawisz właściwość lub `PreventUsage`, nie są dozwolone żadne dodatkowe parametry ciągu połączenia. Odziedziczony <xref:System.Data.Common.DBDataPermissionAttribute>po pliku .|  
|`KeyRestrictionBehavior`|Identyfikuje parametry ciągu połączenia jako jedyne dodatkowe`AllowOnly`parametry dozwolone ( ) lub identyfikuje dodatkowe`PreventUsage`parametry, które nie są dozwolone ( ). Wartość domyślna to `AllowOnly`. Odziedziczony <xref:System.Data.Common.DBDataPermissionAttribute>po pliku .|  
|`TypeID`|Pobiera unikatowy identyfikator dla tego atrybutu, gdy zaimplementowane w klasie pochodnej. Odziedziczony <xref:System.Attribute>po pliku .|  
|`Unrestricted`|Wskazuje, czy nieograniczone uprawnienie do zasobu jest zadeklarowane. Odziedziczony <xref:System.Security.Permissions.SecurityAttribute>po pliku .|  
  
#### <a name="connectionstring-syntax"></a>Składnia połączenia  
 W poniższym przykładzie pokazano, jak używać `connectionStrings` elementu pliku konfiguracji, aby zezwolić tylko na określony ciąg połączenia do użycia. Zobacz [Parametry połączenia, aby](connection-strings.md) uzyskać więcej informacji na temat przechowywania i pobierania ciągów połączeń z plików konfiguracyjnych.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>Składnia wytrysków klawiszy  
 Poniższy przykład włącza ten sam ciąg połączenia, umożliwia korzystanie z opcji ciągu połączenia `Encrypt` i, `Packet Size` ale ogranicza użycie innych opcji ciągu połączenia.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>KeyRestrictionBehavior z preventUsage Składnia  
 Poniższy przykład włącza ten sam ciąg połączenia i `User Id` `Password` zezwala `Persist Security Info`na wszystkie inne parametry połączenia z wyjątkiem , i .  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>KeyRestrictionBehavior z allowonly składni  
 Poniższy przykład umożliwia dwa parametry `Initial Catalog`połączenia, `Encrypt`które `Packet Size` również zawierają , `Connection Timeout`, i parametry. Wszystkie inne parametry ciągu połączenia są ograniczone.  
  
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
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Włączanie częściowego zaufania przy za pomocą niestandardowego zestawu uprawnień  
 Aby włączyć korzystanie <xref:System.Data.SqlClient> z uprawnień dla określonej strefy, administrator systemu musi utworzyć niestandardowy zestaw uprawnień i ustawić go jako zestaw uprawnień dla określonej strefy. Domyślne zestawy uprawnień, takie jak `LocalIntranet`, nie mogą być modyfikowane. Na przykład, <xref:System.Data.SqlClient> aby uwzględnić uprawnienia <xref:System.Security.Policy.Zone> do `LocalIntranet`kodu, który ma , `LocalIntranet`administrator systemu może skopiować zestaw uprawnień dla <xref:System.Data.SqlClient> , zmień jego nazwę na "CustomLocalIntranet", dodać uprawnienia, zaimportować customlocalIntranet zestaw uprawnień za pomocą [Caspol.exe (Narzędzie zasad zabezpieczeń dostępu do kodu)](../../tools/caspol-exe-code-access-security-policy-tool.md)i ustawić zestaw uprawnień `LocalIntranet_Zone` na CustomLocalIntranet.  
  
### <a name="sample-permission-set"></a>Przykładowy zestaw uprawnień  
 Poniżej przedstawiono przykładowy zestaw uprawnień dla dostawcy danych programu .NET Framework dla programu SQL Server w scenariuszu częściowo zaufanym. Aby uzyskać informacje dotyczące tworzenia niestandardowych zestawów uprawnień, zobacz [Konfigurowanie zestawów uprawnień przy użyciu pliku Caspol.exe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100)).  
  
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
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>Weryfikowanie dostępu ADO.NET kodu przy użyciu uprawnień zabezpieczeń  
 W przypadku scenariuszy częściowego zaufania można wymagać uprawnień CAS dla <xref:System.Data.SqlClient.SqlClientPermissionAttribute>określonych metod w kodzie, określając plik . Jeśli to uprawnienie nie jest dozwolone przez zasady zabezpieczeń z ograniczeniami w życie, wyjątek jest zgłaszany przed uruchomieniem kodu. Aby uzyskać więcej informacji na temat zasad zabezpieczeń, zobacz [Zasady zarządzania zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) i [najważniejsze wskazówki dotyczące zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100)).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak napisać kod, który wymaga określonego ciągu połączenia. Symuluje odmawianie nieograniczonych <xref:System.Data.SqlClient>uprawnień do programu , które administrator systemu zaimplementowałby przy użyciu zasad CAS w świecie rzeczywistym.  
  
> [!IMPORTANT]
> Podczas projektowania uprawnień CAS dla ADO.NET, prawidłowy wzorzec jest, aby rozpocząć od najbardziej restrykcyjne przypadku (brak uprawnień w ogóle), a następnie dodać określone uprawnienia, które są potrzebne do określonego zadania, które kod musi wykonać. Przeciwny wzorzec, począwszy od wszystkich uprawnień, a następnie odmawiając określonego uprawnienia, nie jest bezpieczny, ponieważ istnieje wiele sposobów wyrażania tego samego ciągu połączenia. Na przykład, jeśli zaczniesz od wszystkich uprawnień, a następnie spróbujesz odmówić użycia ciągu połączenia "server=someserver", ciąg "server=someserver.mycompany.com" będzie nadal dozwolony. Zawsze uruchamiając, nie przyznając żadnych uprawnień, można zmniejszyć szanse, że istnieją luki w zestawie uprawnień.  
  
 Poniższy kod pokazuje, jak `SqlClient` wykonuje żądanie zabezpieczeń, <xref:System.Security.SecurityException> który zgłasza, jeśli odpowiednie uprawnienia CAS nie są w miejscu. Dane <xref:System.Security.SecurityException> wyjściowe są wyświetlane w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Dane wyjściowe powinny być widoczne w oknie konsoli:  
  
```output  
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
  
## <a name="interoperability-with-unmanaged-code"></a>Interoperacyjność z kodem niezarządzanym  
 Kod, który działa poza CLR jest nazywany kodem niezarządzanym. W związku z tym mechanizmy zabezpieczeń, takie jak CAS nie można zastosować do kodu niezarządzanego. Składniki COM, interfejsy ActiveX i funkcje interfejsu API systemu Windows są przykładami niezarządzanego kodu. Specjalne względy bezpieczeństwa mają zastosowanie podczas wykonywania kodu niezarządzanego, dzięki czemu nie zagrażają ogólne bezpieczeństwo aplikacji. Aby uzyskać więcej informacji, zobacz [Interoperating with Unmanaged Code](../../interop/index.md).  
  
 .NET Framework obsługuje również zgodność wsteczną z istniejącymi składnikami COM, zapewniając dostęp za pośrednictwem współdziałania COM. Składniki COM można włączyć do aplikacji .NET Framework przy użyciu narzędzi współdziałania COM do importowania odpowiednich typów COM. Po zaimportowaniu typy COM są gotowe do użycia. Com interop umożliwia również klientom COM dostęp do kodu zarządzanego, eksportując metadane zestawu do biblioteki typów i rejestrując zarządzany składnik jako składnik COM. Aby uzyskać więcej informacji, zobacz [Zaawansowana interoperacyjność COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie aplikacji ADO.NET](securing-ado-net-applications.md)
- [Zabezpieczenia w kodzie macierzystym i net framework](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))
- [Zabezpieczenia oparte na rolach](../../../standard/security/role-based-security.md)
- [Omówienie ADO.NET](ado-net-overview.md)
