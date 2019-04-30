---
title: Schemat pliku konfiguracji dla programu .NET Framework
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
ms.openlocfilehash: 6ebb6487136bff567c57143e3000a20270c1f87e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705288"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="431f2-102">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="431f2-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="431f2-103">Pliki konfiguracyjne są standardowymi plikami XML, które służy do zmiany ustawień i ustawienia zasad dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="431f2-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="431f2-104">Schemat konfiguracji .NET Framework składa się z elementów, w której można w plikach konfiguracyjnych do sterowania zachowaniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="431f2-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="431f2-105">Spis treści dla tej sekcji odzwierciedla hierarchię schematów dla uruchamiania, środowisko uruchomieniowe, sieci i innych rodzajów ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="431f2-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="431f2-106">Aby uzyskać informacje o typach, formatu i lokalizacji plików konfiguracji, zobacz artykuł [konfigurowania aplikacji](~/docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="431f2-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](~/docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="431f2-107">Zapoznaj się z danymi XML, jeśli chcesz bezpośrednio edytować pliki konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="431f2-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="431f2-108">Znaczniki i atrybuty w plikach konfiguracji XML jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="431f2-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="431f2-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="431f2-109">In this section</span></span>

<span data-ttu-id="431f2-110">[**\<Konfiguracja >** elementu](~/docs/framework/configure-apps/file-schema/configuration-element.md) w tym artykule opisano `<configuration>` element, który jest elementem najwyższego poziomu dla wszystkich plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="431f2-110">[**\<configuration>** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="431f2-111">[**\<assemblybinding — >** elementu](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) określa politykę powiązania zestawu na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="431f2-111">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="431f2-112">[**\<linkedconfiguration — >** elementu](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) określa wymagający uwzględnienia plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="431f2-112">[**\<linkedConfiguration>** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="431f2-113">[Schemat ustawień uruchamiania](~/docs/framework/configure-apps/file-schema/startup/index.md) w tym artykule opisano elementy określające, która wersja środowiska uruchomieniowego języka wspólnego do użycia.</span><span class="sxs-lookup"><span data-stu-id="431f2-113">[Startup Settings Schema](~/docs/framework/configure-apps/file-schema/startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="431f2-114">[Schemat ustawień środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/index.md) w tym artykule opisano elementy, które konfigurują zachowanie zestawu powiązania i środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="431f2-114">[Runtime Settings Schema](~/docs/framework/configure-apps/file-schema/runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="431f2-115">[Schemat ustawień sieci](~/docs/framework/configure-apps/file-schema/network/index.md) opisano elementy, które określają, jak .NET Framework łączy się z Internetem.</span><span class="sxs-lookup"><span data-stu-id="431f2-115">[Network Settings Schema](~/docs/framework/configure-apps/file-schema/network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="431f2-116">[Schemat ustawień kryptografii](~/docs/framework/configure-apps/file-schema/cryptography/index.md) opisano elementy, które mapują przyjazne nazwy algorytmu na klasy, które implementują algorytmy kryptograficzne.</span><span class="sxs-lookup"><span data-stu-id="431f2-116">[Cryptography Settings Schema](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="431f2-117">[Schemat sekcji konfiguracji](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) opisano elementy używane do tworzenia i korzystanie z sekcji konfiguracji dla ustawień niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="431f2-117">[Configuration Sections Schema](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="431f2-118">[Debugowanie schemat ustawień śledzenia i](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) opisano elementy, które określają przełączniki śledzenia i detektory.</span><span class="sxs-lookup"><span data-stu-id="431f2-118">[Trace and Debug Settings Schema](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="431f2-119">[Schemat ustawień dostawcy języka kompilatora i](~/docs/framework/configure-apps/file-schema/compiler/index.md) opisano elementy, które określają konfigurację kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="431f2-119">[Compiler and Language Provider Settings Schema](~/docs/framework/configure-apps/file-schema/compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="431f2-120">[Schemat ustawień aplikacji](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) opisano elementy, które umożliwiają aplikacji Windows Forms i ASP.NET w do przechowywania i pobierania ustawień o zakresie aplikacji i zakresie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="431f2-120">[Application Settings Schema](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="431f2-121">[Schemat ustawień aplikacji](~/docs/framework/configure-apps/file-schema/appsettings/index.md) zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="431f2-121">[App Settings Schema](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="431f2-122">[Schemat ustawień internetowych](~/docs/framework/configure-apps/file-schema/web/index.md) wszystkie elementy w schemacie ustawień sieci Web zawierają elementy umożliwiające konfigurację działania programu ASP.NET z aplikacją hosta, takich jak usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="431f2-122">[Web Settings Schema](~/docs/framework/configure-apps/file-schema/web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="431f2-123">Używane w *Aspnet.config* plików.</span><span class="sxs-lookup"><span data-stu-id="431f2-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="431f2-124">[Schemat konfiguracji programu Windows Forms](winforms/index.md) wszystkie elementy w sekcji Konfiguracja aplikacji Windows Forms, która zawiera dostosowania, takie jak obsługa rozdzielczości DPI wielu monitorów i wysoka.</span><span class="sxs-lookup"><span data-stu-id="431f2-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="431f2-125">[Schemat konfiguracji programu WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md) wszystkie elementy, które umożliwiają konfigurowanie aplikacji usługi i klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="431f2-125">[WCF Configuration Schema](~/docs/framework/configure-apps/file-schema/wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="431f2-126">[Składnia dyrektywy programu WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) w tym artykule opisano `@ServiceHost` dyrektywy, który definiuje atrybuty specyficzne dla strony, używane przez kompilator .svc.</span><span class="sxs-lookup"><span data-stu-id="431f2-126">[WCF Directive Syntax](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="431f2-127">[Schemat konfiguracji programu WIF](windows-identity-foundation/index.md) wszystkie elementy schematu konfiguracji Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="431f2-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="431f2-128">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="431f2-128">Related sections</span></span>

<span data-ttu-id="431f2-129">[Schemat ustawień komunikacji zdalnej](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) w tym artykule opisano elementy, które konfigurują aplikacje klienckie i serwerowe, które implementują komunikację zdalną.</span><span class="sxs-lookup"><span data-stu-id="431f2-129">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="431f2-130">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) opisano elementy, które kontrolują zachowanie aplikacji sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="431f2-130">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="431f2-131">[Schemat ustawień usługi w sieci Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) opisano elementy, które kontrolują zachowanie swoich klientów i usług sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="431f2-131">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="431f2-132">[Konfigurowanie aplikacji programu .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) opisano, jak skonfigurować zabezpieczenia, zmontować zestaw i komunikacji zdalnej w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="431f2-132">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
