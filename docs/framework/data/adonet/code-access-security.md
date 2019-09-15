---
title: Zabezpieczenia dostępu kodu i ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: 6340bc3fb2291601ba2a9812e0a438839f0718bc
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971817"
---
# <a name="code-access-security-and-adonet"></a>Zabezpieczenia dostępu kodu i ADO.NET
.NET Framework oferuje zabezpieczenia oparte na rolach, a także zabezpieczenia dostępu kodu (CAS), które są implementowane przy użyciu wspólnej infrastruktury dostarczanej przez środowisko uruchomieniowe języka wspólnego (CLR). W świecie kodu niezarządzanego większość aplikacji jest wykonywanych z uprawnieniami użytkownika lub podmiotu zabezpieczeń. W związku z tym systemy komputerowe mogą być uszkodzone, a dane prywatne zostały naruszone, gdy złośliwe lub błędne oprogramowanie jest uruchamiane przez użytkownika z podniesionymi uprawnieniami.  
  
 Z kolei kod zarządzany wykonywany w .NET Framework obejmuje zabezpieczenia dostępu kodu, który ma zastosowanie tylko do kodu. Czy kod może być uruchamiany lub nie zależy od pochodzenia kodu lub innych aspektów tożsamości kodu, nie tylko tożsamości podmiotu zabezpieczeń. Zmniejsza to prawdopodobieństwo, że kod zarządzany może być nieużywany.  
  
## <a name="code-access-permissions"></a>Uprawnienia dostępu kodu  
 Gdy kod jest wykonywany, prezentuje dowód, który jest oceniany przez system zabezpieczeń środowiska CLR. Zazwyczaj ten dowód obejmuje pochodzenie kodu, w tym adres URL, witrynę i strefę, oraz podpisy cyfrowe, które zapewniają tożsamość zestawu.  
  
 Środowisko CLR umożliwia kod do wykonywania tylko tych operacji, do których kod ma uprawnienia do wykonania. Kod może zażądać uprawnień i te żądania są honorowane na podstawie zasad zabezpieczeń ustawionych przez administratora.  
  
> [!NOTE]
> Kod wykonywany w środowisku CLR nie może udzielić uprawnień do samego siebie. Na przykład kod może zażądać i uzyskać mniejsze uprawnienia niż zezwala na to zasady zabezpieczeń, ale nigdy nie zostanie przyznane więcej uprawnień. Podczas udzielania uprawnień Zacznij od braku uprawnień, a następnie Dodaj najwęższe uprawnienia dla danego wykonywanego zadania. Począwszy od wszystkich uprawnień, a następnie odmowy poszczególnym osobom potencjalną ochronę niezabezpieczonych aplikacji, które mogą zawierać niezamierzone luki w zabezpieczeniach przed przyznaniem im więcej uprawnień niż jest to wymagane. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) i [Zarządzanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
 Istnieją trzy typy uprawnień dostępu kodu:  
  
- `Code access permissions`pochodny od <xref:System.Security.CodeAccessPermission> klasy. Uprawnienia są wymagane w celu uzyskania dostępu do chronionych zasobów, takich jak pliki i zmienne środowiskowe, oraz do wykonywania operacji chronionych, takich jak uzyskiwanie dostępu do kodu niezarządzanego.  
  
- `Identity permissions`reprezentuje charakterystykę identyfikującą zestaw. Uprawnienia są przyznawane zestawowi w oparciu o dowód, który może zawierać elementy, takie jak podpis cyfrowy lub kod pochodzący z programu. Uprawnienia tożsamości pochodzą także od <xref:System.Security.CodeAccessPermission> klasy bazowej.  
  
- `Role-based security permissions`są zależne od tego, czy podmiot zabezpieczeń ma określoną tożsamość, czy jest członkiem określonej roli. <xref:System.Security.Permissions.PrincipalPermission> Klasa umożliwia zarówno deklaratywne, jak i bezwzględne sprawdzanie uprawnień względem aktywnego podmiotu zabezpieczeń.  
  
 Aby ustalić, czy kod jest autoryzowany do uzyskania dostępu do zasobu lub wykonywania operacji, system zabezpieczeń środowiska uruchomieniowego przechodzi przez stos wywołań, porównując przyznane uprawnienia każdego wywołującego z wymaganym uprawnieniem. Jeśli jakikolwiek obiekt wywołujący w stosie wywołań nie ma wymaganego uprawnienia, <xref:System.Security.SecurityException> zgłaszany jest wyjątek i dostęp zostaje odrzucony.  
  
### <a name="requesting-permissions"></a>Żądanie uprawnień  
 Celem żądania uprawnień jest informowanie środowiska uruchomieniowego o uprawnieniach wymaganych przez aplikację w celu ich uruchomienia i upewnienia się, że otrzymuje tylko uprawnienia, których rzeczywiście potrzebuje. Na przykład, jeśli aplikacja wymaga zapisu danych na dysku lokalnym, wymaga <xref:System.Security.Permissions.FileIOPermission>. Jeśli to uprawnienie nie zostało przyznane, aplikacja zakończy się niepowodzeniem podczas próby zapisu na dysku. Jeśli jednak aplikacja nie udzieliła `FileIOPermission` żądań, a to uprawnienie nie zostało przyznane, aplikacja będzie generować wyjątek na początku i nie będzie ładować.  
  
 W scenariuszu, w którym aplikacja musi tylko odczytywać dane z dysku, można zażądać, aby nigdy nie mieć uprawnień do zapisu. W przypadku usterki lub złośliwego ataku kod nie może uszkodzić danych, na których działa. Aby uzyskać więcej informacji, zobacz [żądanie uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).  
  
## <a name="role-based-security-and-cas"></a>Zabezpieczenia oparte na rolach i urzędy certyfikacji  
 Implementowanie zabezpieczeń opartych na rolach i zabezpieczeń dostępu do kodu (CAS) zwiększa ogólne zabezpieczenia aplikacji. Zabezpieczenia oparte na rolach mogą opierać się na koncie systemu Windows lub tożsamości niestandardowej, co umożliwia tworzenie informacji o podmiotu zabezpieczeń dostępnym dla bieżącego wątku. Ponadto aplikacje są często wymagane w celu zapewnienia dostępu do danych lub zasobów na podstawie poświadczeń dostarczonych przez użytkownika. Zazwyczaj takie aplikacje sprawdzają rolę użytkownika i zapewniają dostęp do zasobów na podstawie tych ról.  
  
 Zabezpieczenia oparte na rolach umożliwiają składnikowi identyfikację bieżących użytkowników i skojarzonych z nimi ról w czasie wykonywania. Te informacje są następnie mapowane przy użyciu zasad CAS w celu określenia zestawu uprawnień udzielanego w czasie wykonywania. Dla określonej domeny aplikacji host może zmienić domyślne zasady zabezpieczeń oparte na rolach i ustawić domyślny podmiot zabezpieczeń, który reprezentuje użytkownika i role skojarzone z tym użytkownikiem.  
  
 Środowisko CLR używa uprawnień do zaimplementowania mechanizmu do wymuszania ograniczeń w kodzie zarządzanym. Uprawnienia zabezpieczeń oparte na rolach zapewniają mechanizm wykrywania, czy użytkownik (lub agent działający w imieniu użytkownika) ma określoną tożsamość lub jest członkiem określonej roli. Aby uzyskać więcej informacji, zobacz [uprawnienia zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100)).  
  
 W zależności od typu kompilowanej aplikacji należy również rozważyć zaimplementowanie uprawnień opartych na rolach w bazie danych. Aby uzyskać więcej informacji na temat zabezpieczeń opartych na rolach w SQL Server, zobacz [SQL Server Security](./sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Zestawy  
 Zestawy stanowią podstawową jednostkę wdrożenia, kontrolę wersji, ponowne użycie, zakres aktywacji i uprawnienia zabezpieczeń dla aplikacji .NET Framework. Zestaw zawiera kolekcję typów i zasobów, które są tworzone w celu współdziałania i tworzą logiczną jednostkę funkcjonalności. W środowisku CLR typ nie istnieje poza kontekstem zestawu. Aby uzyskać więcej informacji na temat tworzenia i wdrażania zestawów, zobacz [programowanie z zestawami](../../../standard/assembly/program.md).  
  
### <a name="strong-naming-assemblies"></a>Zestawy o silnych nazwach  
 Silna nazwa lub podpis cyfrowy składa się z tożsamości zestawu, która obejmuje jego prostą nazwę tekstu, numer wersji i informacje o kulturze (jeśli zostały podane) oraz klucz publiczny i podpis cyfrowy. Podpis cyfrowy jest generowany na podstawie pliku zestawu przy użyciu odpowiedniego klucza prywatnego. Plik zestawu zawiera manifest zestawu, który zawiera nazwy i skróty wszystkich plików, które tworzą zestaw.  
  
 Silne nazewnictwo zestawu daje aplikacji lub składnikowi unikatową tożsamość, która może być używana przez inne oprogramowanie do jawnego odwoływania się do niego. Zestawy chroniące silne nazewnictwo przed fałszowaniem przez zestaw, który zawiera kod nieszkodliwy. Silne nazewnictwo zapewnia także spójność wersji między różnymi wersjami składnika. Należy wdrożyć zestawy o silnych nazwach, które zostaną wdrożone w globalnej pamięci podręcznej zestawów (GAC). Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnej nazwie](../../../standard/assembly/create-use-strong-named.md).  
  
## <a name="partial-trust-in-adonet-20"></a>Częściowe zaufanie w ADO.NET 2,0  
 W ADO.NET 2,0 Dostawca danych .NET Framework, SQL Server .NET Framework Dostawca danych dla OLE DB, .NET Framework dostawca danych dla ODBC, a .NET Framework dostawca danych dla programu Oracle można teraz uruchamiać w częściowo zaufanych środowiskach. W poprzednich wersjach .NET Framework były obsługiwane tylko <xref:System.Data.SqlClient> w mniej niż aplikacje w pełni zaufane.  
  
 Co najmniej częściowo zaufana Aplikacja korzystająca z dostawcy SQL Server musi mieć uprawnienia wykonywania <xref:System.Data.SqlClient.SqlClientPermission> i uprawnień.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Właściwości atrybutu uprawnienia dla częściowej relacji zaufania  
 W przypadku scenariuszy częściowej relacji zaufania można <xref:System.Data.SqlClient.SqlClientPermissionAttribute> użyć elementów członkowskich, aby dodatkowo ograniczyć możliwości dostępne dla dostawca danych .NET Framework SQL Server.  
  
 W poniższej tabeli wymieniono dostępne <xref:System.Data.SqlClient.SqlClientPermissionAttribute> właściwości i ich opisy:  
  
|Właściwość atrybutu uprawnienia|Opis|  
|-----------------------------------|-----------------|  
|`Action`|Pobiera lub ustawia akcję zabezpieczeń. Dziedziczone z <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Włącza lub wyłącza użycie pustego hasła w parametrach połączenia. Prawidłowe wartości to `true` (aby umożliwić korzystanie z pustych haseł) i `false` (Aby wyłączyć używanie pustych haseł). Dziedziczone z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|Identyfikuje dozwolone parametry połączenia. Można zidentyfikować wiele parametrów połączenia. **Uwaga:**  W parametrach połączenia nie należy umieszczać identyfikatora użytkownika ani hasła. W tej wersji nie można zmienić ograniczeń parametrów połączenia za pomocą narzędzia konfiguracji .NET Framework. <br /><br /> Dziedziczone z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|Określa parametry parametrów połączenia, które są dozwolone lub niedozwolone. Parametry parametrów połączenia są identyfikowane w  *\<nazwie parametru formularza > =* . Można określić wiele parametrów, rozdzielając je przy użyciu średnika (;). **Uwaga:**  Jeśli nie określisz `KeyRestrictions`, ale ustawisz `KeyRestrictionBehavior` właściwość na `AllowOnly` lub `PreventUsage`, nie są dozwolone dodatkowe parametry parametrów połączenia. Dziedziczone z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|Identyfikuje parametry parametrów połączenia jako jedyne dozwolone dodatkowe parametry (`AllowOnly`) lub identyfikuje dodatkowe parametry, które nie są dozwolone (`PreventUsage`). `AllowOnly`jest wartością domyślną. Dziedziczone z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Pobiera unikatowy identyfikator dla tego atrybutu, gdy jest zaimplementowany w klasie pochodnej. Dziedziczone z <xref:System.Attribute>.|  
|`Unrestricted`|Wskazuje, czy nieograniczone uprawnienia do zasobu są zadeklarowane. Dziedziczone z <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### <a name="connectionstring-syntax"></a>Składnia ConnectionString  
 Poniższy przykład pokazuje, `connectionStrings` jak używać elementu pliku konfiguracji, aby zezwalać na użycie tylko określonych parametrów połączenia. Zobacz [parametry połączeń](connection-strings.md) , aby uzyskać więcej informacji na temat przechowywania i pobierania parametrów połączenia z plików konfiguracji.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>Składnia ograniczeń dla  
 Poniższy przykład włącza te same parametry połączenia, umożliwia korzystanie z `Encrypt` opcji i `Packet Size` parametrów połączenia, ale ogranicza użycie innych opcji parametrów połączenia.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>KeyRestrictionBehavior z składnią PreventUsage  
 W poniższym przykładzie są włączane te same parametry połączenia i można je wszystkie inne parametrów `User Id`połączenia `Password` z `Persist Security Info`wyjątkiem dla i.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>KeyRestrictionBehavior z składnią AllowOnly  
 Poniższy przykład włącza dwa parametry połączenia, które zawierają `Initial Catalog`również parametry, `Encrypt` `Connection Timeout`, i `Packet Size` . Wszystkie inne parametry parametrów połączenia są ograniczone.  
  
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
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Włączanie częściowej relacji zaufania z niestandardowym zestawem uprawnień  
 Aby umożliwić korzystanie z <xref:System.Data.SqlClient> uprawnień dla określonej strefy, administrator systemu musi utworzyć niestandardowy zestaw uprawnień i ustawić go jako uprawnienie ustawione dla określonej strefy. Domyślne zestawy uprawnień, takie jak `LocalIntranet`, nie mogą być modyfikowane. <xref:System.Data.SqlClient> Na przykład aby uwzględnić uprawnienia dla kodu, który <xref:System.Security.Policy.Zone> ma `LocalIntranet`, administrator systemu może skopiować zestaw uprawnień dla `LocalIntranet`, zmienić nazwę na "CustomLocalIntranet", dodać <xref:System.Data.SqlClient> uprawnienia, zaimportować uprawnienie CustomLocalIntranet ustawia się za pomocą [Caspol. exe (Narzędzie zasad zabezpieczeń dostępu kodu)](../../tools/caspol-exe-code-access-security-policy-tool.md)i ustawia zestaw `LocalIntranet_Zone` uprawnień do CustomLocalIntranet.  
  
### <a name="sample-permission-set"></a>Przykładowy zestaw uprawnień  
 Poniżej znajduje się przykładowy zestaw uprawnień dla Dostawca danych .NET Framework w przypadku SQL Server w częściowo zaufanym scenariuszu. Aby uzyskać informacje na temat tworzenia niestandardowych zestawów uprawnień, zobacz [konfigurowanie zestawów uprawnień przy użyciu Caspol. exe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100)).  
  
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
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>Weryfikowanie dostępu kodu ADO.NET przy użyciu uprawnień zabezpieczeń  
 W przypadku scenariuszy częściowej relacji zaufania można wymagać uprawnień urzędów certyfikacji dla określonych metod w kodzie, określając <xref:System.Data.SqlClient.SqlClientPermissionAttribute>a. Jeśli to uprawnienie nie jest dozwolone przez zasady zabezpieczeń z ograniczeniami, przed uruchomieniem kodu zostanie zgłoszony wyjątek. Aby uzyskać więcej informacji na temat zasad zabezpieczeń, Zobacz najlepsze rozwiązania dotyczące [zarządzania zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) i [zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100)).  
  
### <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób pisania kodu, który wymaga określonych parametrów połączenia. Symuluje odrzucanie nieograniczonych uprawnień <xref:System.Data.SqlClient>do, które mogą zostać wdrożone przez administratora systemu przy użyciu zasad CAS w świecie rzeczywistym.  
  
> [!IMPORTANT]
> Podczas projektowania uprawnień urzędów certyfikacji dla ADO.NET, prawidłowym wzorcem jest rozpoczęcie od najbardziej restrykcyjnego przypadku (bez uprawnień w ogóle), a następnie dodanie określonych uprawnień, które są wymagane dla konkretnego zadania, które kod musi wykonać. Wzorzec odwrotny, zaczynający się od wszystkich uprawnień, a następnie odmawiający określonego uprawnienia, nie jest zabezpieczony, ponieważ istnieje wiele sposobów wyrażania tych samych parametrów połączenia. Jeśli na przykład zaczniesz korzystać z wszystkich uprawnień, a następnie spróbujesz odrzucić użycie parametrów połączenia "serwer = someserver", ciąg "Server = someserver. webcompany. com" nadal będzie dozwolony. Zawsze, gdy w ogóle nie przyznano żadnych uprawnień, zmniejszasz prawdopodobieństwo wystąpienia w zestawie uprawnień.  
  
 Poniższy kod demonstruje, jak `SqlClient` program wykonuje żądanie zabezpieczeń, które <xref:System.Security.SecurityException> zgłasza, czy nie są odpowiednie uprawnienia do urzędów certyfikacji. <xref:System.Security.SecurityException> Dane wyjściowe są wyświetlane w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Dane wyjściowe powinny być widoczne w oknie konsoli:  
  
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
 Kod, który jest uruchamiany poza środowiskiem CLR, jest nazywany kodem niezarządzanym. Z tego względu mechanizmy zabezpieczeń, takie jak urzędy certyfikacji, nie mogą być stosowane do kodu niezarządzanego. Składniki COM, interfejsy ActiveX i funkcje interfejsu API systemu Windows to przykłady kodu niezarządzanego. Specjalne kwestie dotyczące zabezpieczeń są stosowane podczas wykonywania kodu niezarządzanego, aby nie zagrażać ogólnym zabezpieczeniom aplikacji. Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../interop/index.md).  
  
 .NET Framework obsługuje również zgodność z poprzednimi wersjami z istniejącymi składnikami COM przez zapewnienie dostępu za pomocą międzyoperacyjności modelu COM. Składniki COM można dołączać do aplikacji .NET Framework przy użyciu narzędzi międzyoperacyjnych modelu COM do importowania odpowiednich typów COM. Po zaimportowaniu typy COM są gotowe do użycia. Współdziałanie modelu COM umożliwia również klientom COM dostęp do kodu zarządzanego przez wyeksportowanie metadanych zestawu do biblioteki typów i zarejestrowanie składnika zarządzanego jako składnika modelu COM. Aby uzyskać więcej informacji, zobacz [Zaawansowane współdziałanie com](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx).  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](securing-ado-net-applications.md)
- [Zabezpieczenia w kodzie natywnym i .NET Framework](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))
- [Zabezpieczenia oparte na rolach](../../../standard/security/role-based-security.md)
- [Omówienie ADO.NET](ado-net-overview.md)
