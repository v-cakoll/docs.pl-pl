---
title: Konfiguracja aplikacji
description: Dowiedz się, jak skonfigurować Blazor aplikacje bez korzystania z programu ConfigurationManager.
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/01/2020
ms.openlocfilehash: a13f663c2c6908ba906e42cb939c3b8707b8cccd
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173318"
---
# <a name="app-configuration"></a><span data-ttu-id="4227a-103">Konfiguracja aplikacji</span><span class="sxs-lookup"><span data-stu-id="4227a-103">App configuration</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="4227a-104">Podstawowym sposobem ładowania konfiguracji aplikacji w formularzach sieci Web jest wprowadzenie wpisów w pliku *web.config* &mdash; na serwerze lub związanym pliku konfiguracji, do którego odwołuje się *web.config*. Można użyć obiektu statycznego `ConfigurationManager` do współpracy z ustawieniami aplikacji, parametrami połączenia repozytorium danych i innymi dostawcami konfiguracji rozszerzonej, które są dodawane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4227a-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="4227a-105">Typowym sposobem jest wyświetlenie interakcji z konfiguracją aplikacji, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4227a-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="4227a-106">W przypadku ASP.NET Core i po stronie serwera Blazor *web.config* plik może być obecny, jeśli aplikacja jest hostowana na serwerze Windows IIS.</span><span class="sxs-lookup"><span data-stu-id="4227a-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="4227a-107">Nie ma jednak `ConfigurationManager` interakcji z tą konfiguracją i można uzyskać bardziej strukturalną konfigurację aplikacji z innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="4227a-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="4227a-108">Zapoznaj się z informacjami na temat sposobu zbierania konfiguracji i uzyskiwania dostępu do informacji konfiguracyjnych z pliku *web.config* .</span><span class="sxs-lookup"><span data-stu-id="4227a-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="4227a-109">Źródła konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4227a-109">Configuration sources</span></span>

<span data-ttu-id="4227a-110">ASP.NET Core rozpoznaje istnieje wiele źródeł konfiguracji, które mogą być używane w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4227a-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="4227a-111">Platforma próbuje domyślnie oferować najlepsze z tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="4227a-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="4227a-112">Konfiguracja jest odczytywana i agregowana z tych różnych źródeł przez ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4227a-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="4227a-113">Późniejsze wartości załadowane dla tego samego klucza konfiguracji mają pierwszeństwo przed wcześniejszymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="4227a-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="4227a-114">ASP.NET Core zaprojektowano tak, aby była oparta na chmurze, a konfiguracja aplikacji była łatwiejsza dla operatorów i deweloperów.</span><span class="sxs-lookup"><span data-stu-id="4227a-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="4227a-115">ASP.NET Core jest oparta na środowisku i wie, że jest uruchomiona w `Production` środowisku lub `Development` .</span><span class="sxs-lookup"><span data-stu-id="4227a-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="4227a-116">Wskaźnik środowiska jest ustawiany w `ASPNETCORE_ENVIRONMENT` zmiennej środowiskowej system.</span><span class="sxs-lookup"><span data-stu-id="4227a-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="4227a-117">Jeśli żadna wartość nie jest skonfigurowana, domyślnie działa w `Production` środowisku.</span><span class="sxs-lookup"><span data-stu-id="4227a-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="4227a-118">Aplikacja może wyzwolić konfigurację i dodać ją z kilku źródeł na podstawie nazwy środowiska.</span><span class="sxs-lookup"><span data-stu-id="4227a-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="4227a-119">Domyślnie konfiguracja jest ładowana z następujących zasobów w podanej kolejności:</span><span class="sxs-lookup"><span data-stu-id="4227a-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="4227a-120">*appsettings.jsw* pliku, jeśli jest obecny</span><span class="sxs-lookup"><span data-stu-id="4227a-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="4227a-121">*appSettings. {ENVIRONMENT_NAME}. plik JSON* (jeśli istnieje)</span><span class="sxs-lookup"><span data-stu-id="4227a-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="4227a-122">Plik tajny użytkownika na dysku, jeśli jest obecny</span><span class="sxs-lookup"><span data-stu-id="4227a-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="4227a-123">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="4227a-123">Environment variables</span></span>
1. <span data-ttu-id="4227a-124">Argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="4227a-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="4227a-125">appsettings.jsw formacie i dostępie</span><span class="sxs-lookup"><span data-stu-id="4227a-125">appsettings.json format and access</span></span>

<span data-ttu-id="4227a-126">*appsettings.jsw* pliku może być hierarchiczny z wartościami strukturalnymi, takimi jak poniższy kod JSON:</span><span class="sxs-lookup"><span data-stu-id="4227a-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

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

<span data-ttu-id="4227a-127">W przypadku powyższego kodu JSON system konfiguracji spłaszcza wartości podrzędne i odwołuje się do ich w pełni kwalifikowanych hierarchicznych ścieżek.</span><span class="sxs-lookup"><span data-stu-id="4227a-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="4227a-128">Znak dwukropka ( `:` ) oddziela każdą właściwość w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="4227a-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="4227a-129">Na przykład klucz konfiguracji `section1:key0` uzyskuje dostęp do `section1` wartości literału obiektu `key0` .</span><span class="sxs-lookup"><span data-stu-id="4227a-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="4227a-130">Wpisy tajne użytkownika</span><span class="sxs-lookup"><span data-stu-id="4227a-130">User secrets</span></span>

<span data-ttu-id="4227a-131">Wpisy tajne użytkownika:</span><span class="sxs-lookup"><span data-stu-id="4227a-131">User secrets are:</span></span>

* <span data-ttu-id="4227a-132">Wartości konfiguracyjne przechowywane w pliku JSON na stacji roboczej dewelopera poza folderem tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4227a-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="4227a-133">Ładowany tylko w `Development` środowisku.</span><span class="sxs-lookup"><span data-stu-id="4227a-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="4227a-134">Skojarzone z określoną aplikacją.</span><span class="sxs-lookup"><span data-stu-id="4227a-134">Associated with a specific app.</span></span>
* <span data-ttu-id="4227a-135">Zarządzane za pomocą polecenia interfejs wiersza polecenia platformy .NET Core `user-secrets` .</span><span class="sxs-lookup"><span data-stu-id="4227a-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="4227a-136">Skonfiguruj aplikację do przechowywania wpisów tajnych, wykonując `user-secrets` polecenie:</span><span class="sxs-lookup"><span data-stu-id="4227a-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="4227a-137">Poprzednie polecenie dodaje `UserSecretsId` element do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="4227a-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="4227a-138">Element zawiera identyfikator GUID, który jest używany do kojarzenia wpisów tajnych z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="4227a-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="4227a-139">Następnie można zdefiniować wpis tajny za pomocą `set` polecenia.</span><span class="sxs-lookup"><span data-stu-id="4227a-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="4227a-140">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4227a-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="4227a-141">Poprzednie polecenie sprawia, że `Parent:ApiKey` klucz konfiguracji jest dostępny na stacji roboczej dewelopera z wartością `12345` .</span><span class="sxs-lookup"><span data-stu-id="4227a-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="4227a-142">Aby uzyskać więcej informacji na temat tworzenia, przechowywania i zarządzania kluczami tajnymi użytkowników, zobacz [bezpieczny magazyn wpisów tajnych aplikacji w programie Development w ASP.NET Core](/aspnet/core/security/app-secrets) dokumencie.</span><span class="sxs-lookup"><span data-stu-id="4227a-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="4227a-143">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="4227a-143">Environment variables</span></span>

<span data-ttu-id="4227a-144">Następny zbiór wartości załadowanych do konfiguracji aplikacji jest zmiennymi środowiskowymi systemu.</span><span class="sxs-lookup"><span data-stu-id="4227a-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="4227a-145">Wszystkie ustawienia zmiennych środowiskowych systemu są teraz dostępne przez interfejs API konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4227a-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="4227a-146">Wartości hierarchiczne są spłaszczone i oddzielane średnikami podczas odczytu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4227a-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="4227a-147">Jednak niektóre systemy operacyjne nie zezwalają na nazwy zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="4227a-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="4227a-148">ASP.NET Core rozwiązuje to ograniczenie przez konwertowanie wartości, które mają podwójne podkreślenia ( `__` ) na dwukropek, gdy są dostępne.</span><span class="sxs-lookup"><span data-stu-id="4227a-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="4227a-149">`Parent:ApiKey`Wartość z powyższej sekcji Secret użytkownika może zostać zastąpiona zmienną środowiskową `Parent__ApiKey` .</span><span class="sxs-lookup"><span data-stu-id="4227a-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="4227a-150">Argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="4227a-150">Command-line arguments</span></span>

<span data-ttu-id="4227a-151">Konfigurację można również określić jako argumenty wiersza polecenia, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="4227a-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="4227a-152">Użyj podwójnej kreski ( `--` ) lub zapisu do przodu ( `/` ), aby wskazać nazwę wartości konfiguracji do ustawienia i wartość do skonfigurowania.</span><span class="sxs-lookup"><span data-stu-id="4227a-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="4227a-153">Składnia przypomina następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="4227a-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="4227a-154">Zwrot web.config</span><span class="sxs-lookup"><span data-stu-id="4227a-154">The return of web.config</span></span>

<span data-ttu-id="4227a-155">Jeśli aplikacja została wdrożona w systemie Windows w usługach IIS, plik *web.config* nadal KONFIGURUJE usługi IIS do zarządzania aplikacją.</span><span class="sxs-lookup"><span data-stu-id="4227a-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="4227a-156">Domyślnie usługi IIS dodają odwołanie do modułu ASP.NET Core (ANCM).</span><span class="sxs-lookup"><span data-stu-id="4227a-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="4227a-157">ANCM to natywny moduł IIS, który hostuje aplikację zamiast serwera sieci Web Kestrel.</span><span class="sxs-lookup"><span data-stu-id="4227a-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="4227a-158">Ta sekcja *web.config* przypomina następujące znaczniki XML:</span><span class="sxs-lookup"><span data-stu-id="4227a-158">This *web.config* section resembles the following XML markup:</span></span>

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

<span data-ttu-id="4227a-159">Konfigurację specyficzną dla aplikacji można zdefiniować przez zagnieżdżanie `environmentVariables` elementu w `aspNetCore` elemencie.</span><span class="sxs-lookup"><span data-stu-id="4227a-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="4227a-160">Wartości zdefiniowane w tej sekcji są prezentowane ASP.NET Core aplikacji jako zmienne środowiskowe.</span><span class="sxs-lookup"><span data-stu-id="4227a-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="4227a-161">Zmienne środowiskowe są ładowane odpowiednio w ramach tego segmentu uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4227a-161">The environment variables load appropriately during that segment of app startup.</span></span>

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

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="4227a-162">Odczytaj konfigurację w aplikacji</span><span class="sxs-lookup"><span data-stu-id="4227a-162">Read configuration in the app</span></span>

<span data-ttu-id="4227a-163">ASP.NET Core zapewnia konfigurację aplikacji za pomocą <xref:Microsoft.Extensions.Configuration.IConfiguration> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4227a-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="4227a-164">Ten interfejs konfiguracji powinien być żądany przez Blazor składniki, Blazor strony i wszystkie inne klasy zarządzane przez ASP.NET Core, które wymagają dostępu do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4227a-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="4227a-165">Platforma ASP.NET Core automatycznie wypełni ten interfejs ze skonfigurowaną wcześniej rozpoznaną konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="4227a-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="4227a-166">Na Blazor stronie lub znaczniku Razor składnika można wstrzyknąć `IConfiguration` obiekt z `@inject` dyrektywą w górnej części pliku *. Razor* , jak to:</span><span class="sxs-lookup"><span data-stu-id="4227a-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="4227a-167">Ta Poprzednia instrukcja sprawia, że `IConfiguration` obiekt jest dostępny jako `Configuration` zmienna w całej pozostałej części szablonu Razor.</span><span class="sxs-lookup"><span data-stu-id="4227a-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="4227a-168">Poszczególne ustawienia konfiguracji można odczytać, określając hierarchię ustawień konfiguracji poszukiwaną jako parametr indeksatora:</span><span class="sxs-lookup"><span data-stu-id="4227a-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="4227a-169">Wszystkie sekcje konfiguracji można pobrać przy użyciu <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> metody pobierania kolekcji kluczy w określonej lokalizacji z składnią podobną do `GetSection("section1")` , aby pobrać konfigurację Section1 z wcześniejszego przykładu.</span><span class="sxs-lookup"><span data-stu-id="4227a-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="4227a-170">Konfiguracja o jednoznacznie określonym typie</span><span class="sxs-lookup"><span data-stu-id="4227a-170">Strongly typed configuration</span></span>

<span data-ttu-id="4227a-171">Za pomocą formularzy sieci Web można utworzyć typ konfiguracji o jednoznacznie określonym typie, który dziedziczy z <xref:System.Configuration.ConfigurationSection> typu i skojarzonych typów.</span><span class="sxs-lookup"><span data-stu-id="4227a-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="4227a-172">`ConfigurationSection`Można skonfigurować niektóre reguły biznesowe i przetwarzać te wartości konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="4227a-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="4227a-173">W ASP.NET Core można określić hierarchię klas, która będzie odbierać wartości konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="4227a-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="4227a-174">Następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="4227a-174">These classes:</span></span>

* <span data-ttu-id="4227a-175">Nie trzeba dziedziczyć z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="4227a-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="4227a-176">Powinien zawierać `public` właściwości, które pasują do właściwości i typów odwołań dla struktury konfiguracji, która ma zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="4227a-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="4227a-177">W przypadku wcześniejszych *appsettings.jsna* przykład można zdefiniować następujące klasy do przechwytywania wartości:</span><span class="sxs-lookup"><span data-stu-id="4227a-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

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

<span data-ttu-id="4227a-178">Tę hierarchię klas można wypełnić, dodając następujący wiersz do `Startup.ConfigureServices` metody:</span><span class="sxs-lookup"><span data-stu-id="4227a-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="4227a-179">W pozostałej części aplikacji można dodać parametr wejściowy do klas lub `@inject` dyrektywy w szablonach Razor typu, `IOptions<MyConfig>` Aby otrzymać ustawienia konfiguracji o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="4227a-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="4227a-180">`IOptions<MyConfig>.Value`Właściwość zwróci `MyConfig` wartość wypełnioną z ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4227a-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="4227a-181">Więcej informacji o funkcji opcji można znaleźć w [wzorcu opcji w ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) dokumencie.</span><span class="sxs-lookup"><span data-stu-id="4227a-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4227a-182">[Poprzedni](middleware.md) 
> [Dalej](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="4227a-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
