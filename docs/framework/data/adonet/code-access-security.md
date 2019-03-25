---
title: Zabezpieczenia dostępu kodu i ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: af3fe9a233972e939dc14117fc08343bca9d5fd6
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411567"
---
# <a name="code-access-security-and-adonet"></a>Zabezpieczenia dostępu kodu i ADO.NET
.NET Framework oferuje zabezpieczenia oparte na rolach, a także zabezpieczeń dostępu kodu (CAS), które są implementowane przy użyciu wspólnej infrastruktury, dostarczane przez środowisko uruchomieniowe języka wspólnego (CLR). W świecie kodu niezarządzanego większość aplikacji są wykonywane z uprawnienia użytkownika lub jednostki. W rezultacie systemów komputerowych, może być uszkodzone i prywatnych danych naruszenia zabezpieczeń w przypadku złośliwego lub wypełnione błąd oprogramowania jest uruchamiane przez użytkownika z podwyższonym poziomem uprawnień.  
  
 Z drugiej strony wykonywanie kodu zarządzanego programu .NET Framework zawiera zabezpieczeń dostępu kodu, która dotyczy tylko kodu. Czy kod może być uruchomiona lub nie jest zależny od pochodzenia kodu lub innych aspektów tożsamości kodu, a nie wyłącznie tożsamości podmiotu zabezpieczeń. Zmniejsza to prawdopodobieństwo, że zarządzane precyzyjnego kodu.  
  
## <a name="code-access-permissions"></a>Uprawnienia dostępu kodu  
 Gdy kod jest wykonywany, przedstawia dowody, które jest obliczane przez system zabezpieczeń CLR. Zazwyczaj te dowody składa się z źródła kodu, w tym adres URL, lokacji i strefy i podpisy cyfrowe, które zapewniają tożsamość zestawu.  
  
 Środowisko CLR umożliwia kod do wykonywania tych operacji, które kod ma uprawnienia do wykonania. Kod może zażądać uprawnień, a te żądania są honorowane, na podstawie zasad zabezpieczeń ustawione przez administratora.  
  
> [!NOTE]
>  Kod wykonywany w CLR nie można udzielić uprawnień do samego siebie. Na przykład kod może żądać i mieć przyznane uprawnienia mniej, niż zezwala na zasady zabezpieczeń, ale nigdy nie zostanie udzielony mieć większe uprawnienia. Podczas nadawania uprawnień należy rozpoczynać się w ogóle nie ma uprawnień, a następnie dodaj najwęższego uprawnienia do danego zadania wykonywane. Począwszy od wszystkich uprawnień, a następnie odmawianie pojedyncze pliki prowadzi do niezabezpieczone aplikacje, które mogą zawierać luki w zabezpieczeniach niezamierzone z udzielanie więcej uprawnień niż jest to wymagane. Aby uzyskać więcej informacji, zobacz [konfigurowania zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) i [Zarządzanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
 Istnieją trzy typy uprawnień dostępu do kodu:  
  
-   `Code access permissions` pochodzi od <xref:System.Security.CodeAccessPermission> klasy. Uprawnienia są wymagane, aby uzyskać dostęp do chronionych zasobów, takich jak pliki i zmiennych środowiskowych i wykonywanie chronionej operacji, takich jak uzyskiwanie dostępu do kodu niezarządzanego.  
  
-   `Identity permissions` reprezentuje właściwości, które identyfikują zestawu. Uprawnienia są przyznawane na podstawie dowodów, które mogą zawierać elementy, takie jak podpis cyfrowy lub którego pochodzi ten kod zestawu. Uprawnienia tożsamości, ale również dziedziczyć <xref:System.Security.CodeAccessPermission> klasy bazowej.  
  
-   `Role-based security permissions` zależą od tego, czy podmiot zabezpieczeń ma określonej tożsamości lub jest członkiem określonej roli. <xref:System.Security.Permissions.PrincipalPermission> Klasa umożliwia zarówno kontroli deklaratywnego i imperatywnego uprawnienia względem aktywny podmiot zabezpieczeń.  
  
 Aby ustalić, czy kod jest autoryzowany do uzyskania dostępu do zasobu lub wykonania operacji, system zabezpieczeń w środowisku uruchomieniowym przechodzi przez stos wywołań, porównywanie udzielone uprawnienia każdy obiekt wywołujący, aby uprawnienia są wymagane. Jeśli dowolny obiekt wywołujący na stosie wywołań nie ma wymaganego uprawnienia <xref:System.Security.SecurityException> jest generowany i następuje odmowa dostępu.  
  
### <a name="requesting-permissions"></a>Żądanie uprawnień  
 Żądanie uprawnień ma na celu poinformować środowiska uruchomieniowego, uprawnienia, które aplikacja wymaga, aby można było uruchomić i upewnij się, że będzie ona otrzymywać tylko uprawnienia, które jest faktycznie potrzebny. Na przykład, jeśli Twoja aplikacja potrzebuje do zapisywania danych na dysku lokalnym, wymaga <xref:System.Security.Permissions.FileIOPermission>. Jeśli nie zostało udzielone uprawnienie, aplikacja zakończy się niepowodzeniem podczas próby zapisania na dysku. Jednak jeśli aplikacja żąda `FileIOPermission` i że nie przyznano uprawnienia aplikacji zostanie wygenerowany wyjątek na początku i nie zostanie załadowany.  
  
 W przypadku której aplikacja musi tylko do odczytu danych z dysku możesz poprosić, że jej nigdy nie zostać przyznane uprawnienia do zapisu. W przypadku błędu lub złośliwymi atakami kod nie może uszkodzić dane, na którym działa. Aby uzyskać więcej informacji, zobacz [żąda uprawnienia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).  
  
## <a name="role-based-security-and-cas"></a>Zabezpieczenia oparte na rolach i urzędy certyfikacji  
 Implementowanie zabezpieczeń opartych na rolach i zabezpieczeń dostępne z kodu (CAS) zwiększa ogólną zabezpieczeń aplikacji. Zabezpieczenia oparte na rolach może opierać się na konto Windows lub tożsamość niestandardowa, udostępniając informacje podmiotu zabezpieczeń bieżącego wątku. Ponadto aplikacje często są wymagane w celu zapewnienia dostępu do danych lub zasobów, w oparciu o poświadczenia podane przez użytkownika. Zazwyczaj takie aplikacje sprawdzić rolę użytkownika i umożliwiają dostęp do zasobów na podstawie tych ról.  
  
 Zabezpieczenia oparte na rolach umożliwia składnikowi zidentyfikować bieżących użytkowników i ich skojarzone role w czasie wykonywania. Informacja ta jest następnie mapowana do określania zestawu uprawnień przyznanych w czasie wykonywania za pomocą zasad CAS. W domenie określonej aplikacji hosta można zmienić domyślne zasady zabezpieczeń opartej na rolach i skonfigurować podmiotu zabezpieczeń domyślny, który reprezentuje użytkownika, jak i role skojarzone z tym użytkownikiem.  
  
 Środowisko CLR używa uprawnień do implementacji jego mechanizm wymuszania ograniczenia dotyczące kodu zarządzanego. Uprawnienia zabezpieczeń oparte na rolach, zapewniają mechanizm do wykrywania, czy użytkownik (lub agent działający w imieniu użytkownika) ma określoną tożsamość lub jest członkiem określonej roli. Aby uzyskać więcej informacji, zobacz [uprawnienia zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100)).  
  
 W zależności od typu aplikacji, które tworzysz należy również rozważyć Implementowanie opartej na rolach uprawnień w bazie danych. Aby uzyskać więcej informacji na temat zabezpieczeń opartych na rolach w programie SQL Server, zobacz [zabezpieczeń serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Zestawy  
 Zespoły tworzą podstawową jednostką wdrażania, kontroli wersji, ponownego użycia, określania zakresu aktywacji i uprawnień zabezpieczeń dla aplikacji programu .NET Framework. Zestaw zawiera kolekcję typów i zasobów, które zostały opracowane w celu współpracują ze sobą i tworzą jednostkę logiczną funkcji. Do środowiska CLR typem nie istnieje poza kontekstem zestawu. Aby uzyskać więcej informacji o tworzeniu i wdrażaniu zestawów, zobacz [programowanie za pomocą zestawów](../../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
### <a name="strong-naming-assemblies"></a>Zestawy o silnych nazw  
 Silna nazwa lub podpis cyfrowy składa się z tożsamości zestawu, który zawiera nazwy zwykły tekst, numeru wersji i informacji o kulturze (jeśli zostały zapewnione), oraz klucza publicznego i podpisu cyfrowego. Podpis cyfrowy jest generowany na podstawie pliku zestawu przy użyciu odpowiedniego klucza prywatnego. Plik zestawu zawiera manifest zestawu, który zawiera nazwy i wartości skrótów wszystkich plików, wchodzące w skład zestawu.  
  
 Silne nazewnictwo zestawu daje aplikacji lub składnika unikatową tożsamość używaną przez inne oprogramowanie do jawnie się do niego odwoływać. Silne nazwy chroni zestawy względem fałszowania przez zestaw, który zawiera kod szkodliwy. Nazewnictwo silne zapewnia również przechowywanie wersji spójność różnych wersji składnika. Należy najpierw zestawy o silnych nazwach, które zostaną wdrożone do globalnej pamięci podręcznej zestawów (GAC). Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="partial-trust-in-adonet-20"></a>Częściowej relacji zaufania w ADO.NET w wersji 2.0  
 ADO.NET w wersji 2.0 dla programu .NET Framework Data Provider for SQL Server dla programu .NET Framework Data Provider for OLE DB dla programu .NET Framework Data Provider for ODBC i .NET Framework Data Provider for Oracle można teraz wszystkie działania w środowiskach częściowo zaufany. W poprzednich wersjach programu .NET Framework, tylko <xref:System.Data.SqlClient> była obsługiwana w aplikacjach mniej niż pełnego zaufania.  
  
 Co najmniej częściowo zaufanych aplikacji, przy użyciu dostawcy programu SQL Server musi mieć wykonywania i <xref:System.Data.SqlClient.SqlClientPermission> uprawnienia.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Właściwości atrybutów uprawnieniami częściowego zaufania  
 W scenariuszach częściowej relacji zaufania, można użyć <xref:System.Data.SqlClient.SqlClientPermissionAttribute> elementy członkowskie, aby jeszcze bardziej ograniczyć możliwości, które są dostępne dla dostawcy danych .NET Framework dla programu SQL Server.  
  
 Poniższa tabela zawiera listę dostępnych <xref:System.Data.SqlClient.SqlClientPermissionAttribute> właściwości i ich opisy:  
  
|Właściwość atrybutu uprawnień|Opis|  
|-----------------------------------|-----------------|  
|`Action`|Pobiera lub ustawia akcji zabezpieczeń. Odziedziczone po <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Włącza lub wyłącza przyciski regulacji puste hasło w parametrach połączenia. Prawidłowe wartości to `true` (Aby włączyć używanie pustych haseł) i `false` (Aby zablokować używanie pustych haseł). Odziedziczone po <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|Określa ciąg dozwolone połączenia. Można określić wiele parametrów połączenia. **Uwaga:**  Nie dołączaj nazwy użytkownika i hasła w ciągu połączenia. W tej wersji nie można zmienić ograniczenia parametrów połączenia przy użyciu narzędzia .NET Framework Configuration Tool. <br /><br /> Odziedziczone po <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|Określa parametry połączenia, które są dozwolone lub niedozwolone. Parametry połączenia są identyfikowane w formie  *\<Nazwa parametru > =*. Można określić wiele parametrów, rozdzielonych średnikami (;). **Uwaga:**  Jeśli nie określisz `KeyRestrictions`, ale ustawisz `KeyRestrictionBehavior` właściwości `AllowOnly` lub `PreventUsage`, nie dodatkowych parametrów połączenia są dozwolone. Odziedziczone po <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|Określa parametry połączenia jako tylko dodatkowe parametry, które są niedozwolone (`AllowOnly`), lub identyfikuje dodatkowe parametry, które nie są dozwolone (`PreventUsage`). `AllowOnly` jest ustawieniem domyślnym. Odziedziczone po <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Pobiera unikatowy identyfikator dla tego atrybutu w przypadku zaimplementowania w klasie pochodnej. Odziedziczone po <xref:System.Attribute>.|  
|`Unrestricted`|Wskazuje, czy zadeklarowano nieograniczonych uprawnień do zasobu. Odziedziczone po <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### <a name="connectionstring-syntax"></a>Element ConnectionString składni  
 Poniższy przykład pokazuje sposób użycia `connectionStrings` element pliku konfiguracji, aby zezwolić tylko określony ciąg połączenia ma być używany. Zobacz [parametry połączenia](../../../../docs/framework/data/adonet/connection-strings.md) Aby uzyskać więcej informacji na temat przechowywania i pobierania parametrów połączenia z plików konfiguracji.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>Składnia KeyRestrictions  
 Poniższy przykład umożliwia włączenie tych samych parametrach połączenia, umożliwia korzystanie z `Encrypt` i `Packet Size` parametry opcji, ale ogranicza użycie inne opcje parametrów połączenia.  
  
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
 Poniższy przykład umożliwia te same parametry połączenia i zezwala na wszystkie inne parametry połączenia, z wyjątkiem `User Id`, `Password` i `Persist Security Info`.  
  
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
 Poniższy przykład umożliwia dwa ciągi połączeń, które również zawierać `Initial Catalog`, `Connection Timeout`, `Encrypt`, i `Packet Size` parametrów. Wszystkie inne parametry połączenia są ograniczone.  
  
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
 Aby włączyć korzystanie z <xref:System.Data.SqlClient> uprawnienia dla określonej strefy, administrator systemu należy utworzyć niestandardowe uprawnienie ustawić i ustawić go jako zestawu uprawnień dla określonej strefy. Domyślne zestawy uprawnień, takich jak `LocalIntranet`, nie może być modyfikowany. Na przykład w celu uwzględnienia <xref:System.Data.SqlClient> uprawnień do kodu, który ma <xref:System.Security.Policy.Zone> z `LocalIntranet`, administrator systemu można skopiować zestawu uprawnień dla `LocalIntranet`, zmień jego nazwę na "CustomLocalIntranet", Dodaj <xref:System.Data.SqlClient> importowanie uprawnień uprawnienie CustomLocalIntranet można ustawić przy użyciu [Caspol.exe (narzędzie zasad zabezpieczeń dostępu kodu)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)i ustaw zestaw uprawnień `LocalIntranet_Zone` do CustomLocalIntranet.  
  
### <a name="sample-permission-set"></a>Przykładowy zestaw uprawnień  
 Oto przykład zestawu uprawnień dla dostawcy danych .NET Framework dla programu SQL Server w scenariuszu częściowo zaufanych. Aby uzyskać informacje na temat tworzenia zestawów uprawnień niestandardowych, zobacz [konfigurowania uprawnień ustawia za pomocą Caspol.exe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100)).  
  
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
 W przypadku scenariuszy częściowego zaufania może wymagać uprawnienia urzędów certyfikacji dla określonej metody w kodzie, określając <xref:System.Data.SqlClient.SqlClientPermissionAttribute>. Jeśli to uprawnienie nie jest dozwolone przez zasady zabezpieczeń z ograniczeniami obowiązuje, wyjątek jest zgłaszany, przed uruchomieniem kodu. Aby uzyskać więcej informacji na temat zasad zabezpieczeń, zobacz [Zarządzanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) i [najlepszych rozwiązań dotyczących zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100)).  
  
### <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak napisać kod, który wymaga ciągu określonego połączenia. Symuluje, odmawianie nieograniczonych uprawnień do <xref:System.Data.SqlClient>, której administrator systemu może zaimplementować, za pomocą zasady CAS w świecie rzeczywistym.  
  
> [!IMPORTANT]
>  Podczas projektowania uprawnienia urzędów certyfikacji dla ADO.NET, prawidłowy wzorzec jest rozpoczynać się najbardziej restrykcyjne przypadek (uprawnień nie wszystkie), a następnie dodaj określonych uprawnień, które są wymagane dla określonego zadania, które musi wykonać kod. Wzorzec przeciwnej, począwszy od wszystkich uprawnień, a następnie odmawianie określone uprawnienie nie jest bezpieczne, ponieważ istnieje wiele sposobów może przedstawiać tych samych parametrach połączenia. Na przykład, jeśli rozpoczynać wszystkie uprawnienia, a następnie ponów próbę odmawianie ciągu połączenia "server = someserver", ciąg "server=someserver.mycompany.com" będzie nadal dozwolone. Uruchamiając zawsze po udzieleniu w ogóle nie ma uprawnień, można zmniejszyć prawdopodobieństwo, że nie istnieją luki w zestawie uprawnień.  
  
 Poniższy kod przedstawia sposób `SqlClient` wykonuje żądanie zabezpieczeń, który generuje <xref:System.Security.SecurityException> Jeśli odpowiednie uprawnienia urzędy certyfikacji nie są stosowane. <xref:System.Security.SecurityException> Dane wyjściowe są wyświetlane w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Powinny zostać wyświetlone te dane wyjściowe w oknie konsoli:  
  
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
 Kod, który działa poza środowisko CLR jest nazywany kodem niezarządzanym. W związku z tym mechanizmy zabezpieczeń, takich jak urzędy certyfikacji nie można zastosować do kodu niezarządzanego. Składniki COM, interfejsów ActiveX i funkcje Windows API są przykłady kodu niezarządzanego. Zagadnienia dotyczące zabezpieczeń specjalne się podczas wykonywania kodu niezarządzanego, tak aby nie stanowią zagrożenia bezpieczeństwa cała aplikacja. Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md).  
  
 .NET Framework obsługuje także zgodności z poprzednimi wersjami istniejących składników COM, zapewniając dostęp za pośrednictwem współdziałania z modelem COM. Za pomocą narzędzia międzyoperacyjności modelu COM do importowania odpowiednich typów modelu COM, można zastosować składników modelu COM w aplikacji .NET Framework. Po zaimportowaniu typy modelu COM są gotowe do użycia. Usługa międzyoperacyjna modelu COM umożliwia również klientów modelu COM uzyskać dostęp do kodu zarządzanego, eksportowanie metadanych zestawu na bibliotekę typów i rejestrując składnik zarządzany jako składnik COM. Aby uzyskać więcej informacji, zobacz [zaawansowane współdziałanie COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx).  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Zabezpieczenia w kodzie natywnym i kodzie .NET Framework](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))
- [Zabezpieczenia oparte na rolach](../../../../docs/standard/security/role-based-security.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
