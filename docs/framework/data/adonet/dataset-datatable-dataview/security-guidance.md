---
title: Wskazówki dotyczące zabezpieczeń zestawów danych i DataTable
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: c6b32afeadccc3fd22d6611d282840233280440f
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86382459"
---
# <a name="dataset-and-datatable-security-guidance"></a>Wskazówki dotyczące zabezpieczeń zestawów danych i DataTable

Ten artykuł ma zastosowanie do:

* .NET Framework (wszystkie wersje)
* .NET Core i nowsze
* .NET 5,0 i nowsze

[Zestaw](/dotnet/api/system.data.dataset) danych i typy [DataTable](/dotnet/api/system.data.datatable) są starszymi składnikami platformy .NET, które umożliwiają reprezentowania zestawów danych jako obiektów zarządzanych. Te składniki zostały wprowadzone w środowisku .NET 1,0 w ramach oryginalnej [infrastruktury ADO.NET](/dotnet/framework/data/adonet/dataset-datatable-dataview/). Ich celem było zapewnienie widoku zarządzanego na potrzeby relacyjnego zestawu danych, który jest bardziej abstrakcyjny, niezależnie od tego, czy bazowe źródło danych było XML, SQL czy inną technologią.

Aby uzyskać więcej informacji na temat ADO.NET, w tym bardziej nowoczesnych odmian widoku danych, zapoznaj [się z dokumentacją ADO.NET](/dotnet/framework/data/adonet/).

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a>Domyślne ograniczenia podczas deserializacji zestawu danych lub elementu DataTable z pliku XML

We wszystkich obsługiwanych wersjach .NET Framework, .NET Core i .NET `DataSet` i należy `DataTable` wprowadzić następujące ograniczenia dotyczące typów obiektów, które mogą być obecne w deserializowanych danych. Domyślnie ta lista jest ograniczona do:

* Elementy podstawowe i równoważne podstawowe:,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, `bool` `char` `sbyte` `byte` `short` `ushort` `int` `uint` `long` `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` i `SqlString` .
* Często używane elementy inne niż pierwotne: `Type` , `Uri` , i `BigInteger` .
* Najczęściej używane typy _System. Drawing_ : `Color` ,,,,, `Point` `PointF` `Rectangle` `RectangleF` `Size` i `SizeF` .
* `Enum`Typ.
* Tablice i listy powyższych typów.

Jeśli dane przychodzące XML zawierają obiekt, którego typ nie znajduje się na tej liście:

* Zgłaszany jest wyjątek.
* Operacja deserializacji kończy się niepowodzeniem.

Podczas ładowania kodu XML do istniejącego `DataSet` `DataTable` wystąpienia lub istniejące definicje kolumn są również brane pod uwagę. Jeśli tabela zawiera już definicję kolumny typu niestandardowego, ten typ jest tymczasowo dodawany do listy dozwolonych w czasie trwania operacji deserializacji XML.

```cs
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

Ograniczenia typu obiektu mają zastosowanie również w przypadku `XmlSerializer` deserializacji wystąpienia `DataSet` lub `DataTable` . Jednak mogą nie stosować `BinaryFormatter` się do deserializacji wystąpienia `DataSet` lub `DataTable` .

Ograniczenia dotyczące typu obiektu nie mają zastosowania, na przykład `DataAdapter.Fill` gdy `DataTable` wystąpienie jest wypełniane bezpośrednio z bazy danych bez użycia interfejsów API deserializacji XML.

### <a name="extend-the-list-of-allowed-types"></a>Rozwiń listę dozwolonych typów

Aplikacja może rozbudować listę dozwolonych typów, aby uwzględnić niestandardowe typy oprócz wbudowanych typów wymienionych powyżej. Jeśli rozszerzasz listę dozwolonych typów, zmiana ma wpływ na _wszystkie_ `DataSet` `DataTable` wystąpienia w aplikacji. Typów nie można usunąć z listy wbudowanych typów dozwolonych.

#### <a name="extend-through-configuration-net-framework-40---48"></a>Przechodzenie do konfiguracji (.NET Framework 4,0 – 4,8)

_App.config_ można użyć do rozszerania listy dozwolonych typów. Aby rozwinąć listę dozwolonych typów:

* Użyj `<configSections>` elementu, aby dodać odwołanie do sekcji Konfiguracja _System. Data_ .
* Użyj `<system.data.dataset.serialization>` / `<allowedTypes>` , aby określić dodatkowe typy.

Każdy `<add>` element musi określać tylko jeden typ za pomocą nazwy typu kwalifikowanego zestawu. Aby dodać dodatkowe typy do listy dozwolonych typów, Użyj wielu `<add>` elementów.

Poniższy przykład pokazuje Rozszerzanie listy dozwolonych typów przez dodanie typu niestandardowego `Fabrikam.CustomType` .

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

Aby pobrać kwalifikowaną nazwę zestawu typu, użyj właściwości [Type. AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) , jak pokazano w poniższym kodzie.

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a>Przechodzenie do konfiguracji (.NET Framework 2,0 – 3,5)

Jeśli aplikacja jest przeznaczona dla .NET Framework 2,0 lub 3,5, nadal możesz użyć powyższego mechanizmu _App.config_ , aby rozwinąć listę dozwolonych typów. Jednak `<configSections>` element będzie wyglądał nieco inaczej, jak pokazano w poniższym kodzie:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a>Zwiększ programowo (.NET Framework, .NET Core, .NET 5.0 +)

Listę dozwolonych typów można również rozszerzyć programowo przy użyciu [elementu AppDomain. SetData](/dotnet/api/system.appdomain.setdata) z dobrze znanym kluczem _System. Data. DataSetDefaultAllowedTypes_, jak pokazano w poniższym kodzie.

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

W przypadku używania mechanizmu rozszerzenia wartość skojarzona z kluczem _System. Data. DataSetDefaultAllowedTypes_ musi być typu `Type[]` .

Na .NET Framework lista dozwolonych typów może być rozszerzona zarówno z _App.config_ , jak i `AppDomain.SetData` . W tym przypadku `DataSet` i `DataTable` zezwoli na deserializacji obiektu w ramach danych, jeśli jego typ znajduje się na liście.

### <a name="run-an-app-in-audit-mode-net-framework"></a>Uruchom aplikację w trybie inspekcji (.NET Framework)

W .NET Framework `DataSet` i `DataTable` zapewniają możliwość trybu inspekcji. Gdy tryb inspekcji jest włączony, `DataSet` należy `DataTable` porównać typy obiektów przychodzących z listą dozwolonych typów. Jeśli jednak obiekt, którego typ jest niedozwolony, jest widoczny, wyjątek **nie** zostanie zgłoszony. Zamiast tego `DataSet` należy `DataTable` powiadomić wszystkie dołączone `TraceListener` wystąpienia o typie podejrzanym, co pozwala na `TraceListener` rejestrowanie tych informacji. Nie jest zgłaszany żaden wyjątek, a operacja deserializacji będzie kontynuowana.

> [!WARNING]
> Uruchamianie aplikacji w trybie inspekcji powinna być tylko tymczasowym środkiem używanym do testowania. Gdy tryb inspekcji jest włączony `DataSet` i `DataTable` nie Wymuszaj ograniczeń typu, co może spowodować powstanie sieci w aplikacji. Aby uzyskać więcej informacji, zobacz sekcje zatytułowane [usuwanie wszystkich ograniczeń typu](#ratr) i [bezpieczeństwo w odniesieniu do niezaufanych danych wejściowych](#swr).

Tryb inspekcji można włączyć za _App.config_:

* Zapoznaj się z sekcją [rozszerzanie przez konfigurację](#etc) w tym dokumencie, aby uzyskać informacje na temat właściwej wartości do umieszczenia dla `<configSections>` elementu.
* Użyj `<allowedTypes auditOnly="true">` , aby włączyć tryb inspekcji, jak pokazano w poniższej tabeli.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

Gdy tryb inspekcji jest włączony, można użyć _App.config_ , aby połączyć preferowaną z `TraceListener` `DataSet` wbudowaną nazwą wbudowanego `TraceSource.` źródła śledzenia jest _System. Data. DataSet_. Poniższy przykład ilustruje zapisywanie zdarzeń śledzenia w konsoli programu _i_ w pliku dziennika na dysku.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

Aby uzyskać więcej informacji na temat `TraceSource` i `TraceListener` , zobacz dokument [How to: use TraceSource and filters with Trace detektors](/dotnet/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners).

**Uwaga**: uruchamianie aplikacji w trybie inspekcji nie jest dostępne w programie .NET Core ani w programie .NET 5,0 i nowszych wersjach.

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a>Usuń wszystkie ograniczenia typów

Jeśli aplikacja musi usunąć wszystkie ograniczenia dotyczące ograniczania typów z `DataSet` i `DataTable` :

* Istnieje kilka opcji, aby pominąć ograniczenia ograniczające typy.
* Dostępne opcje zależą od struktury docelowej aplikacji.

> [!WARNING]
> Usunięcie wszystkich ograniczeń dotyczących typów może spowodować powstanie otworu zabezpieczeń wewnątrz aplikacji. W przypadku korzystania z tego mechanizmu upewnij się, że aplikacja nie używa lub **nie** `DataSet` `DataTable` odczytuje niezaufanych danych wejściowych. Aby uzyskać więcej informacji, zobacz [CVE-2020-1147](https://portal.msrc.microsoft.com/security-guidance/advisory/CVE-2020-1147) i w poniższej sekcji zatytułowanej [bezpieczeństwo w odniesieniu do niezaufanych danych wejściowych](#swr).

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a>Za poorednictwem konfiguracji AppContext (.NET Framework 4,6-4,8, .NET Core 2,1 i nowszych, .NET 5,0 i nowsze)

`AppContext`Przełącznik, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` , po ustawieniu, aby `true` usunąć wszystkie ograniczenia dotyczące ograniczania typów z `DataSet` i `DataTable` .

W .NET Framework tego przełącznika można włączyć za pośrednictwem _App.config_, jak pokazano w następującej konfiguracji:

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

W ASP.NET `<AppContextSwitchOverrides>` element nie jest dostępny. Zamiast tego przełącznik można włączyć za pośrednictwem _Web.config_, jak pokazano w następującej konfiguracji:

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

Aby uzyskać więcej informacji, zobacz [\<AppContextSwitchOverrides>](/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) element.

W przypadku platformy .NET Core, .NET 5 i ASP.NET Core to ustawienie jest kontrolowane przez _runtimeconfig.jsna_, jak pokazano w poniższym kodzie JSON:

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

Aby uzyskać więcej informacji, zobacz ["podstawowe ustawienia konfiguracji środowiska uruchomieniowego .NET"](/dotnet/core/run-time-config/).

`AllowArbitraryDataSetTypeInstantiation`można również ustawić programowo za pośrednictwem [AppContext. setswitch](/dotnet/api/system.appcontext.setswitch) zamiast przy użyciu pliku konfiguracji, jak pokazano w poniższym kodzie:

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 W przypadku wybrania wcześniejszego podejścia programistycznego wywołanie `AppContext.SetSwitch` powinno odbywać się wczesne podczas uruchamiania aplikacji.

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a>Za pomocą rejestru na całym komputerze (.NET Framework 2,0 – 4,8)

Jeśli `AppContext` program nie jest dostępny, sprawdzanie ograniczające typy można wyłączyć za pomocą rejestru systemu Windows:

* Administrator musi skonfigurować rejestr.
* Korzystanie z rejestru jest zmianą dla całego komputera i wpłynie na _wszystkie_ aplikacje działające na tym komputerze.

| Typ  |  Wartość |
|---|---|
| **Klucz rejestru** | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| **Nazwa wartości** | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| **Typ wartości** | `REG_SZ` |
| **Dane wartości** | `true` |

W 64-bitowym systemie operacyjnym, ta wartość musi być dodana zarówno dla klucza 64-bitowego (podanego powyżej), jak i klucza 32-bitowego. Klucz 32-bitowy znajduje się w lokalizacji `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` .

Aby uzyskać więcej informacji na temat korzystania z rejestru do konfigurowania `AppContext` , zobacz ["AppContext for Library](/dotnet/api/system.appcontext#appcontext-for-library-consumers)consumers".

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a>Bezpieczeństwo w odniesieniu do niezaufanych danych wejściowych

Chociaż `DataSet` i `DataTable` nakładają domyślne ograniczenia dotyczące typów, które mogą być obecne podczas deserializacji ładunków XML __ `DataSet` i `DataTable` są ogólnie niebezpieczne, gdy są wypełniane niezaufanymi danymi wejściowymi.__ Poniżej znajduje się niepełna lista sposobów `DataSet` `DataTable` odczytywania niezaufanych danych wejściowych lub wystąpienia.

* Odwołuje się do `DataAdapter` bazy danych, a `DataAdapter.Fill` Metoda jest używana do wypełniania `DataSet` zawartością zapytania bazy danych.
* `DataSet.ReadXml`Metoda or `DataTable.ReadXml` służy do odczytywania pliku XML zawierającego informacje o kolumnie i wierszu.
* `DataSet`Wystąpienie lub `DataTable` jest serializowane jako część usług sieci Web ASP.NET (SOAP) lub punktu końcowego WCF.
* Serializator, taki jak `XmlSerializer` jest używany do deserializacji `DataSet` `DataTable` wystąpienia lub ze strumienia XML.
* Serializator, taki jak `JsonConvert` jest używany do deserializacji `DataSet` `DataTable` wystąpienia lub ze strumienia JSON. `JsonConvert`to metoda w popularnejNewtonsoft.Jsinnej firmy [w](https://www.newtonsoft.com/json) bibliotece.
* Serializator, taki jak `BinaryFormatter` jest używany do deserializacji `DataSet` `DataTable` wystąpienia lub z strumienia nieprzetworzonych bajtów.

W tym dokumencie omówiono zagadnienia dotyczące bezpieczeństwa w przypadku wcześniejszych scenariuszy.

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a>Użyj `DataAdapter.Fill` , aby wypełnić `DataSet` z niezaufanego źródła danych

`DataSet`Wystąpienie może być wypełniane za `DataAdapter` pomocą [ `DataAdapter.Fill` metody](/dotnet/api/system.data.common.dataadapter.fill), jak pokazano w poniższym przykładzie.

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

(Przykładowy kod jest częścią większego przykładu znalezionego podczas [wypełniania zestawu danych z elementu DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter)).

> Większość aplikacji może uprościć i założyć, że ich warstwa bazy danych jest zaufana. Niemniej jednak w wykonywaćniu aplikacji do [modelowania zagrożeń](https://www.microsoft.com/securityengineering/sdl/threatmodeling) model zagrożeń może być uważany za granicę zaufania między aplikacją a warstwą bazy danych (serwera). Korzystanie z uwierzytelniania [wzajemnego](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) i uwierzytelniania usługi [AAD](/azure/azure-sql/database/authentication-aad-overview) między klientem a serwerem jest jednym ze sposobów, aby pomóc w rozwiązywaniu ryzyka związanego z tym. W pozostałej części tej sekcji omówiono możliwy wynik połączenia klienta z niezaufanym serwerem.

Konsekwencje wskazywania `DataAdapter` niezaufanego źródła danych zależą od implementacji `DataAdapter` samego siebie.

### <a name="sqldataadapter"></a>Element SqlDataAdapter

W przypadku typu wbudowanego [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter)odwołującego się do niezaufanego źródła danych może spowodować atak typu "odmowa usługi" (DOS). Atak na system DoS może spowodować, że aplikacja przestanie odpowiadać lub ulegnie awarii. Jeśli osoba atakująca może zakładać bibliotekę DLL wraz z aplikacją, mogą oni również uzyskać dostęp do lokalnego wykonywania kodu.

### <a name="other-dataadapter-types"></a>Inne typy DataAdapter

`DataAdapter`Implementacje innych firm muszą dokonać własnych ocen, które zapewniają gwarancje bezpieczeństwa, które są przez nie związane z niezaufanymi danymi wejściowymi. Platforma .NET nie może podejmować żadnych gwarancji bezpieczeństwa dotyczących tych implementacji.

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a>DataSet. ReadXml i DataTable. ReadXml

`DataSet.ReadXml`Metody i `DataTable.ReadXml` nie są bezpieczne, gdy są używane z niezaufanymi danymi wejściowymi. Zdecydowanie zalecamy, aby zamiast tego rozważyć użycie jednego z alternatyw opisanych w dalszej części tego dokumentu.

Implementacje `DataSet.ReadXml` i `DataTable.ReadXml` zostały pierwotnie utworzone przed lukami w serializacji jako dobrze zrozumieć kategorię zagrożeń. W związku z tym kod nie przestrzega bieżących najlepszych rozwiązań w zakresie zabezpieczeń. Te interfejsy API mogą służyć jako wektory dla osób atakujących do wykonywania ataków w systemie DoS względem aplikacji sieci Web. Ataki te mogą spowodować, że usługa sieci Web nie odpowiada, lub spowodować zakończenie nieoczekiwanego procesu. Struktura nie zapewnia środków zaradczych dla tych kategorii ataków i .NET traktuje to zachowanie "według projektu".

Program .NET wydał aktualizacje zabezpieczeń, aby wyeliminować niektóre problemy, takie jak ujawnienie informacji lub zdalne wykonywanie kodu w programie `DataSet.ReadXml` i `DataTable.ReadXml` . Aktualizacje zabezpieczeń platformy .NET mogą nie zapewniać pełnej ochrony przed tymi kategoriami zagrożeń. Konsumenci powinni ocenić swoje poszczególne scenariusze i rozważyć ich potencjalną ekspozycję na te zagrożenia.

Klienci powinni mieć świadomość, że aktualizacje zabezpieczeń tych interfejsów API mogą mieć wpływ na zgodność aplikacji w niektórych sytuacjach. Ponadto istnieje możliwość, że nowa Luka w zabezpieczeniach tych interfejsów API zostanie odnaleziona, dla której platforma .NET nie może praktycznie opublikować aktualizacji zabezpieczeń.

Zalecamy, aby konsumenci tych interfejsów API:

* Rozważ użycie jednego z alternatyw opisanych w dalszej części tego dokumentu.
* Wykonaj indywidualne oceny ryzyka w swoich aplikacjach.

Jedyną odpowiedzialnością dla użytkownika jest określenie, czy mają być używane te interfejsy API. Konsumenci powinni ocenić wszelkie zagrożenia bezpieczeństwa, techniczne i prawne, w tym wymagania prawne, które mogą towarzyszyć za pomocą tych interfejsów API.

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a>DataSet i DataTable za pośrednictwem usług sieci Web ASP.NET lub WCF

Możliwe jest zaakceptowanie `DataSet` lub `DataTable` wystąpienie w usłudze sieci Web ASP.NET (SOAP), jak pokazano w poniższym kodzie:

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

Odmiana tego nie jest akceptowana `DataSet` ani `DataTable` bezpośrednio jako parametr, ale zamiast tego akceptuje ją w ramach ogólnego grafu serializowanego obiektu SOAP, jak pokazano w poniższym kodzie:

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Lub przy użyciu programu WCF zamiast usług sieci Web ASP.NET:

```cs
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

We wszystkich tych przypadkach model zagrożeń i gwarancje bezpieczeństwa są takie same, jak w [sekcji DataSet. ReadXml i DataTable. ReadXml](#dsrdtr).

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a>Deserializacja zestawu danych lub DataTable za pomocą elementu XmlSerializer

Deweloperzy mogą używać `XmlSerializer` do deserializacji `DataSet` i `DataTable` wystąpień, jak pokazano w poniższym kodzie:

```cs
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

W takich przypadkach model zagrożeń i gwarancje bezpieczeństwa są takie same, jak w [sekcji DataSet. ReadXml i DataTable. ReadXml](#dsrdtr)

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a>Deserializacja zestawu danych lub DataTable za pośrednictwem JsonConvert

Popularnej biblioteki Newtonsoft innej firmy [JSON.NET](https://www.newtonsoft.com/json) może służyć do deserializacji `DataSet` i `DataTable` wystąpień, jak pokazano w poniższym kodzie:

```cs
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObect<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObect<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Deserializacja a `DataSet` lub `DataTable` w ten sposób z niezaufanego obiektu BLOB JSON nie jest bezpieczna. Ten wzorzec jest narażony na atak typu "odmowa usługi". Atak może ulec awarii lub nie reagować.

**Uwaga**: Firma Microsoft nie gwarantuje ani nie obsługuje implementacji bibliotek innych firm, takich jak _Newtonsoft.Json_. Te informacje są dostarczane w celu zapewnienia kompletności i są dokładne od momentu tego zapisu.

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a>Deserializacja zestawu danych lub DataTable za pośrednictwem BinaryFormatter

Deweloperzy nie muszą używać `BinaryFormatter` , `NetDataContractSerializer` , `SoapFormatter` ani pokrewnych ***niebezpiecznych*** elementów formatujących do deserializacji `DataSet` `DataTable` wystąpienia lub z niezaufanego ładunku:

* Jest to podatne na pełny atak wykonywania kodu zdalnego.
* Użycie niestandardowych `SerializationBinder` nie jest wystarczające, aby zapobiec takim atakom.

## <a name="safe-replacements"></a>Bezpieczne zamienniki

W przypadku aplikacji, które:

* Akceptuj `DataSet` lub `DataTable` za pomocą punktu końcowego protokołu SOAP lub punktu końcowego WCF.
* Deserializacja niezaufanych danych do wystąpienia `DataSet` lub `DataTable` .

Rozważ zastępowanie modelu obiektów, aby użyć [Entity Framework](/ef). Entity Framework:

* To rozbudowana, nowoczesne, zorientowane obiektowo środowisko, które może reprezentować dane relacyjne.
* Program udostępnia [zróżnicowany ekosystem](/ef/core/providers/) dostawców baz danych, co ułatwia tworzenie zapytań w bazie danych przy użyciu modeli obiektów Entity Framework.
* Oferuje wbudowane zabezpieczenia podczas deserializacji danych z niezaufanych źródeł.

W przypadku aplikacji korzystających z `.aspx` punktów końcowych protokołu SOAP Rozważ zmianę tych punktów końcowych na potrzeby korzystania z [platformy WCF](/dotnet/framework/wcf/). WCF to bardziej zaproponowana wymiana `.asmx` usług sieci Web. Punkty końcowe WCF [mogą być udostępniane za pośrednictwem protokołu SOAP](/dotnet/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients) w celu zapewnienia zgodności z istniejącymi wywołaniami.
