---
title: Konfiguracja aplikacji
description: Dowiedz się, jak skonfigurować aplikacje Blazor bez użycia ConfigurationManager.
author: csharpfritz
ms.author: jefritz
ms.date: 04/01/2020
ms.openlocfilehash: c780a395f72e2520af86c20c7f6618953a528ff7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588247"
---
# <a name="app-configuration"></a><span data-ttu-id="ce00d-103">Konfiguracja aplikacji</span><span class="sxs-lookup"><span data-stu-id="ce00d-103">App configuration</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ce00d-104">Podstawowym sposobem ładowania konfiguracji aplikacji w formularzach sieci Web są&mdash;wpisy w pliku *web.config* na serwerze lub powiązany plik konfiguracyjny, do którego odwołuje się *plik web.config*. Obiekt statyczny `ConfigurationManager` służy do interakcji z ustawieniami aplikacji, ciągami połączeń repozytorium danych i innymi dostawcami konfiguracji rozszerzonej, które są dodawane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="ce00d-105">Typowe jest, aby zobaczyć interakcje z konfiguracją aplikacji, jak widać w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ce00d-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="ce00d-106">W przypadku ASP.NET Core i blazora po stronie serwera plik *web.config* może być obecny, jeśli aplikacja jest hostowana na serwerze Windows IIS.</span><span class="sxs-lookup"><span data-stu-id="ce00d-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="ce00d-107">Jednak nie ma `ConfigurationManager` interakcji z tej konfiguracji i można odbierać więcej konfiguracji aplikacji strukturalnych z innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="ce00d-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="ce00d-108">Przyjrzyjmy się, jak konfiguracja jest zbierana i jak nadal można uzyskać dostęp do informacji o konfiguracji z pliku *web.config.*</span><span class="sxs-lookup"><span data-stu-id="ce00d-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="ce00d-109">Źródła konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ce00d-109">Configuration sources</span></span>

<span data-ttu-id="ce00d-110">ASP.NET Core rozpoznaje, że istnieje wiele źródeł konfiguracji, których możesz użyć dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="ce00d-111">Struktura próbuje zaoferować najlepsze z tych funkcji domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ce00d-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="ce00d-112">Konfiguracja jest odczytywana i agregowana z tych różnych źródeł przez ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce00d-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="ce00d-113">Później załadowane wartości dla tego samego klucza konfiguracji mają pierwszeństwo przed wcześniejszymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="ce00d-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="ce00d-114">ASP.NET Core został zaprojektowany tak, aby był świadomy chmury i ułatwiał konfigurację aplikacji zarówno operatorom, jak i deweloperom.</span><span class="sxs-lookup"><span data-stu-id="ce00d-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="ce00d-115">ASP.NET Core jest świadomy środowiska i wie, czy działa `Production` `Development` w Twoim lub środowisku.</span><span class="sxs-lookup"><span data-stu-id="ce00d-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="ce00d-116">Wskaźnik środowiska jest ustawiony `ASPNETCORE_ENVIRONMENT` w zmiennej środowiskowej systemu.</span><span class="sxs-lookup"><span data-stu-id="ce00d-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="ce00d-117">Jeśli żadna wartość nie jest skonfigurowana, `Production` domyślnie aplikacja działa w środowisku.</span><span class="sxs-lookup"><span data-stu-id="ce00d-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="ce00d-118">Aplikacja może wyzwalać i dodawać konfigurację z kilku źródeł na podstawie nazwy środowiska.</span><span class="sxs-lookup"><span data-stu-id="ce00d-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="ce00d-119">Domyślnie konfiguracja jest ładowana z następujących zasobów w podanej kolejności:</span><span class="sxs-lookup"><span data-stu-id="ce00d-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="ce00d-120">*appsettings.json,* jeśli jest obecny</span><span class="sxs-lookup"><span data-stu-id="ce00d-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="ce00d-121">*appsettings. {ENVIRONMENT_NAME}.json,* jeśli jest obecny</span><span class="sxs-lookup"><span data-stu-id="ce00d-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="ce00d-122">Plik wpisów tajnych użytkownika na dysku, jeśli jest obecny</span><span class="sxs-lookup"><span data-stu-id="ce00d-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="ce00d-123">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="ce00d-123">Environment variables</span></span>
1. <span data-ttu-id="ce00d-124">Argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ce00d-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="ce00d-125">appsettings.json format i dostęp</span><span class="sxs-lookup"><span data-stu-id="ce00d-125">appsettings.json format and access</span></span>

<span data-ttu-id="ce00d-126">Plik *appsettings.json* może być hierarchiczny z wartościami ustrukturyzowanymi w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ce00d-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

<span data-ttu-id="ce00d-127">Po przedstawieniu z poprzednim JSON, system konfiguracji spłaszcza wartości podrzędne i odwołuje się do ich w pełni kwalifikowanych ścieżek hierarchicznych.</span><span class="sxs-lookup"><span data-stu-id="ce00d-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="ce00d-128">Dwukropek`:`( ) oddziela każdą właściwość w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="ce00d-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="ce00d-129">Na przykład klucz `section1:key0` konfiguracji uzyskuje `section1` dostęp do `key0` wartości literału obiektu.</span><span class="sxs-lookup"><span data-stu-id="ce00d-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="ce00d-130">Wpisy tajne użytkownika</span><span class="sxs-lookup"><span data-stu-id="ce00d-130">User secrets</span></span>

<span data-ttu-id="ce00d-131">Wpisy tajne użytkownika to:</span><span class="sxs-lookup"><span data-stu-id="ce00d-131">User secrets are:</span></span>

* <span data-ttu-id="ce00d-132">Wartości konfiguracji, które są przechowywane w pliku JSON na stacji roboczej dewelopera, poza folderem tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="ce00d-133">Ładowany tylko `Development` podczas pracy w środowisku.</span><span class="sxs-lookup"><span data-stu-id="ce00d-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="ce00d-134">Skojarzone z określoną aplikacją.</span><span class="sxs-lookup"><span data-stu-id="ce00d-134">Associated with a specific app.</span></span>
* <span data-ttu-id="ce00d-135">Zarządzane za pomocą `user-secrets` polecenia .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="ce00d-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="ce00d-136">Skonfiguruj aplikację dla magazynu `user-secrets` wpisów tajnych, wykonując polecenie:</span><span class="sxs-lookup"><span data-stu-id="ce00d-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="ce00d-137">Poprzednie polecenie dodaje `UserSecretsId` element do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ce00d-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="ce00d-138">Element zawiera identyfikator GUID, który jest używany do kojarzenia wpisów tajnych z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="ce00d-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="ce00d-139">Następnie można zdefiniować klucz `set` tajny za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="ce00d-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="ce00d-140">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ce00d-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="ce00d-141">Poprzednie polecenie udostępnia `Parent:ApiKey` klucz konfiguracji na stacji roboczej dewelopera `12345`o wartości .</span><span class="sxs-lookup"><span data-stu-id="ce00d-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="ce00d-142">Aby uzyskać więcej informacji na temat tworzenia, przechowywania i zarządzania wpisami tajnymi użytkowników, zobacz [Bezpieczne przechowywanie wpisów tajnych aplikacji w rozwoju w dokumencie ASP.NET Core.](/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="ce00d-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="ce00d-143">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="ce00d-143">Environment variables</span></span>

<span data-ttu-id="ce00d-144">Następny zestaw wartości załadowanych do konfiguracji aplikacji to zmienne środowiskowe systemu.</span><span class="sxs-lookup"><span data-stu-id="ce00d-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="ce00d-145">Wszystkie ustawienia zmiennych środowiskowych systemu są teraz dostępne za pośrednictwem interfejsu API konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="ce00d-146">Wartości hierarchiczne są spłaszczane i oddzielone znakami dwukropek podczas odczytu wewnątrz aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="ce00d-147">Jednak niektóre systemy operacyjne nie zezwalają na nazwy zmiennych środowiska znaków dwukropka.</span><span class="sxs-lookup"><span data-stu-id="ce00d-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="ce00d-148">ASP.NET Core rozwiązuje to ograniczenie, konwertując wartości,`__`które mają podwójne podkreślenia ( ) na dwukropek, gdy są dostępne.</span><span class="sxs-lookup"><span data-stu-id="ce00d-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="ce00d-149">Wartość `Parent:ApiKey` z sekcji wpisów tajnych użytkownika powyżej można `Parent__ApiKey`zastąpić zmienną środowiskową .</span><span class="sxs-lookup"><span data-stu-id="ce00d-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="ce00d-150">Argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ce00d-150">Command-line arguments</span></span>

<span data-ttu-id="ce00d-151">Konfigurację można również podać jako argumenty wiersza polecenia po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="ce00d-152">Użyj notacji double-dash (`--`)`/`lub forward-slash ( ( ), aby wskazać nazwę ustawionej wartości konfiguracji i wartość, która ma być skonfigurowana.</span><span class="sxs-lookup"><span data-stu-id="ce00d-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="ce00d-153">Składnia przypomina następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="ce00d-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="ce00d-154">Powrót web.config</span><span class="sxs-lookup"><span data-stu-id="ce00d-154">The return of web.config</span></span>

<span data-ttu-id="ce00d-155">Jeśli aplikacja została wdrożona w systemie Windows w serwisach IIS, plik *web.config* nadal konfiguruje usługi IIS do zarządzania aplikacją.</span><span class="sxs-lookup"><span data-stu-id="ce00d-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="ce00d-156">Domyślnie iIS dodaje odwołanie do ASP.NET Core Module (ANCM).</span><span class="sxs-lookup"><span data-stu-id="ce00d-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="ce00d-157">ANCM to natywny moduł usług IIS, który obsługuje aplikację zamiast serwera sieci Web Kestrel.</span><span class="sxs-lookup"><span data-stu-id="ce00d-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="ce00d-158">Ta sekcja *web.config* przypomina następujące znaczniki XML:</span><span class="sxs-lookup"><span data-stu-id="ce00d-158">This *web.config* section resembles the following XML markup:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

<span data-ttu-id="ce00d-159">Konfiguracja specyficzne dla aplikacji można `environmentVariables` zdefiniować `aspNetCore` przez zagnieżdżanie elementu w elemencie.</span><span class="sxs-lookup"><span data-stu-id="ce00d-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="ce00d-160">Wartości zdefiniowane w tej sekcji są przedstawiane aplikacji ASP.NET Core jako zmienne środowiskowe.</span><span class="sxs-lookup"><span data-stu-id="ce00d-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="ce00d-161">Zmienne środowiskowe ładują się odpowiednio podczas tego segmentu uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-161">The environment variables load appropriately during that segment of app startup.</span></span>

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="ce00d-162">Odczyt konfiguracji w aplikacji</span><span class="sxs-lookup"><span data-stu-id="ce00d-162">Read configuration in the app</span></span>

<span data-ttu-id="ce00d-163">ASP.NET Core zapewnia konfigurację <xref:Microsoft.Extensions.Configuration.IConfiguration> aplikacji za pośrednictwem interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ce00d-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="ce00d-164">Ten interfejs konfiguracyjny powinien być wymagany przez składniki Blazora, strony Blazora i wszelkie inne ASP.NET klasy zarządzanej przez core, która wymaga dostępu do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="ce00d-165">Struktura ASP.NET Core automatycznie wypełni ten interfejs wcześniej skonfigurowaną konfiguracją rozwiązaną.</span><span class="sxs-lookup"><span data-stu-id="ce00d-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="ce00d-166">Na stronie Blazor lub narzutów Razor składnika można `IConfiguration` wstrzyknąć obiekt z dyrektywą `@inject` u góry pliku *.brzytwa* w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="ce00d-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="ce00d-167">Ta poprzednia instrukcja udostępnia `IConfiguration` `Configuration` obiekt jako zmienną w pozostałej części szablonu Razor.</span><span class="sxs-lookup"><span data-stu-id="ce00d-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="ce00d-168">Poszczególne ustawienia konfiguracji można odczytać, określając hierarchię ustawień konfiguracji poszukiwaną jako parametr indeksatora:</span><span class="sxs-lookup"><span data-stu-id="ce00d-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="ce00d-169">Można pobrać całe sekcje konfiguracji <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> przy użyciu metody, aby pobrać kolekcję kluczy w `GetSection("section1")` określonej lokalizacji ze składnią podobną do pobierania konfiguracji dla sekcji 1 z wcześniejszego przykładu.</span><span class="sxs-lookup"><span data-stu-id="ce00d-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="ce00d-170">Konfiguracja silnie typizowana</span><span class="sxs-lookup"><span data-stu-id="ce00d-170">Strongly typed configuration</span></span>

<span data-ttu-id="ce00d-171">Za pomocą formularzy sieci Web można było utworzyć silnie typ <xref:System.Configuration.ConfigurationSection> konfiguracji, który dziedziczył z typu i skojarzonych typów.</span><span class="sxs-lookup"><span data-stu-id="ce00d-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="ce00d-172">A `ConfigurationSection` można skonfigurować niektóre reguły biznesowe i przetwarzania dla tych wartości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="ce00d-173">W ASP.NET Core można określić hierarchię klas, która będzie odbierać wartości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="ce00d-174">Klasy te:</span><span class="sxs-lookup"><span data-stu-id="ce00d-174">These classes:</span></span>

* <span data-ttu-id="ce00d-175">Nie trzeba dziedziczyć z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="ce00d-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="ce00d-176">Powinien `public` zawierać właściwości, które pasują do właściwości i odwołania do typu dla struktury konfiguracji, którą chcesz przechwycić.</span><span class="sxs-lookup"><span data-stu-id="ce00d-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="ce00d-177">W przypadku wcześniejszego przykładu *appsettings.json* można zdefiniować następujące klasy do przechwytywania wartości:</span><span class="sxs-lookup"><span data-stu-id="ce00d-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

<span data-ttu-id="ce00d-178">Tę hierarchię klas można wypełnić, dodając `Startup.ConfigureServices` następujący wiersz do metody:</span><span class="sxs-lookup"><span data-stu-id="ce00d-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="ce00d-179">W pozostałej części aplikacji można dodać parametr wejściowy `@inject` do klas lub dyrektywy `IOptions<MyConfig>` w szablonach razor typu, aby otrzymać silnie wpisane ustawienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="ce00d-180">Właściwość `IOptions<MyConfig>.Value` przyniesie `MyConfig` wartość wypełniona z ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ce00d-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="ce00d-181">Więcej informacji na temat funkcji Opcje można znaleźć we [wzorcu Opcje w](/aspnet/core/fundamentals/configuration/options#options-interfaces) dokumencie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce00d-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ce00d-182">[Poprzedni](middleware.md)
>[następny](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="ce00d-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
