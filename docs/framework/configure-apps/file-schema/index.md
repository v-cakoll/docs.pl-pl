---
title: Schemat pliku konfiguracji dla .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: c3b5518b4b86c2e6f47825d552f49579c5ac0a6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921019"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="308d1-102">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="308d1-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="308d1-103">Pliki konfiguracji to standardowe pliki XML, których można użyć do zmiany ustawień i ustawienia zasad dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="308d1-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="308d1-104">Schemat konfiguracji .NET Framework składa się z elementów, których można użyć w plikach konfiguracji w celu sterowania zachowaniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="308d1-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="308d1-105">Spis treści tej sekcji odzwierciedla hierarchię schematu dla uruchamiania, środowiska uruchomieniowego, sieci i innych typów ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="308d1-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="308d1-106">Informacje o typach, formatach i lokalizacji plików konfiguracji znajdują się w artykule [Konfigurowanie aplikacji](../index.md).</span><span class="sxs-lookup"><span data-stu-id="308d1-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](../index.md).</span></span> <span data-ttu-id="308d1-107">Zapoznaj się z plikiem XML, jeśli chcesz bezpośrednio edytować pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="308d1-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="308d1-108">W przypadku tagów i atrybutów XML w plikach konfiguracji rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="308d1-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="308d1-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="308d1-109">In this section</span></span>

<span data-ttu-id="308d1-110">[ **> elementukonfiguracji\<** ](configuration-element.md) `<configuration>` Opisuje element, który jest elementem najwyższego poziomu dla wszystkich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="308d1-110">[**\<configuration>** Element](configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="308d1-111">[zestawbinding > element określa zasady powiązań zestawu na poziomie konfiguracji.  **\<** ](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="308d1-111">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="308d1-112">[linkedConfiguration > element Określa plik konfiguracji, który ma zostać uwzględniony.  **\<** ](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="308d1-112">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="308d1-113">[Schemat ustawień uruchamiania](./startup/index.md) Opisuje elementy, które określają, która wersja środowiska uruchomieniowego języka wspólnego ma być używana.</span><span class="sxs-lookup"><span data-stu-id="308d1-113">[Startup Settings Schema](./startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="308d1-114">[Schemat ustawień środowiska uruchomieniowego](./runtime/index.md) Opisuje elementy, które konfigurują powiązanie zestawu i zachowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="308d1-114">[Runtime Settings Schema](./runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="308d1-115">[Schemat ustawień sieciowych](./network/index.md) Opisuje elementy, które określają, w jaki sposób .NET Framework nawiązuje połączenie z Internetem.</span><span class="sxs-lookup"><span data-stu-id="308d1-115">[Network Settings Schema](./network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="308d1-116">[Schemat ustawień kryptografii](./cryptography/index.md) Opisuje elementy, które mapują przyjazne nazwy algorytmów na klasy implementujące algorytmy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="308d1-116">[Cryptography Settings Schema](./cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="308d1-117">[Schemat sekcji konfiguracji](configuration-sections-schema.md) Opisuje elementy używane do tworzenia i używania sekcji konfiguracyjnych ustawień niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="308d1-117">[Configuration Sections Schema](configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="308d1-118">[Schemat ustawień śledzenia i debugowania](./trace-debug/index.md) Opisuje elementy, które określają przełączniki śledzenia i odbiorniki.</span><span class="sxs-lookup"><span data-stu-id="308d1-118">[Trace and Debug Settings Schema](./trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="308d1-119">[Schemat ustawień kompilatora i dostawcy języka](./compiler/index.md) Opisuje elementy, które określają konfigurację kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="308d1-119">[Compiler and Language Provider Settings Schema](./compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="308d1-120">[Schemat ustawień aplikacji](application-settings-schema.md) Opisuje elementy, które umożliwiają aplikacji Windows Forms lub ASP.NET przechowywanie i pobieranie ustawień zakresu aplikacji i zakresu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="308d1-120">[Application Settings Schema](application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="308d1-121">[Schemat ustawień aplikacji](./appsettings/index.md) Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="308d1-121">[App Settings Schema](./appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="308d1-122">[Schemat ustawień sieci Web](./web/index.md) Wszystkie elementy w schemacie ustawień sieci Web, w tym elementy służące do konfigurowania sposobu działania programu ASP.NET z aplikacją hosta, taką jak usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="308d1-122">[Web Settings Schema](./web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="308d1-123">Używany w plikach *ASPNET. config* .</span><span class="sxs-lookup"><span data-stu-id="308d1-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="308d1-124">[Schemat konfiguracji Windows Forms](winforms/index.md) Wszystkie elementy w sekcji Konfiguracja aplikacji Windows Forms, w tym takie dostosowania, jak obsługa wielomonitorów i wysokiej rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="308d1-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="308d1-125">[Schemat konfiguracji WCF](./wcf/index.md) Wszystkie elementy, które umożliwiają skonfigurowanie usługi WCF i aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="308d1-125">[WCF Configuration Schema](./wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="308d1-126">[Składnia dyrektywy WCF](./wcf-directive/index.md) `@ServiceHost` Opisuje dyrektywę, która definiuje atrybuty specyficzne dla strony używane przez kompilator SVC.</span><span class="sxs-lookup"><span data-stu-id="308d1-126">[WCF Directive Syntax](./wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="308d1-127">[Schemat konfiguracji WIF](windows-identity-foundation/index.md) Wszystkie elementy schematu konfiguracji Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="308d1-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="308d1-128">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="308d1-128">Related sections</span></span>

<span data-ttu-id="308d1-129">[Schemat ustawień komunikacji zdalnej](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Opisuje elementy, które konfigurują aplikacje klienta i serwera, które implementują komunikację zdalną.</span><span class="sxs-lookup"><span data-stu-id="308d1-129">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="308d1-130">[Schemat ustawień ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Opisuje elementy kontrolujące zachowanie aplikacji sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="308d1-130">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="308d1-131">[Schemat ustawień usług sieci Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Opisuje elementy kontrolujące zachowanie usług sieci Web ASP.NET i ich klientów.</span><span class="sxs-lookup"><span data-stu-id="308d1-131">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="308d1-132">[Konfigurowanie aplikacji .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Opisuje sposób konfigurowania zabezpieczeń, powiązań zestawów i komunikacji zdalnej w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="308d1-132">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
