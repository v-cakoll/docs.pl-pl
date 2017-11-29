---
title: Schemat pliku konfiguracji dla programu .NET Framework
ms.custom: 
ms.date: 05/01/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7f2dec0d71c1a0822bf39ae420d4e56bdaf99e0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="4f803-102">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4f803-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="4f803-103">Pliki konfiguracji są standardowe pliki XML, które można zmienić ustawienia, a następnie ustawić zasady dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f803-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="4f803-104">Schemat konfiguracji .NET Framework składa się z elementów, że można użyć w plikach konfiguracji, aby kontrolować działanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f803-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="4f803-105">Spis treści dla tej sekcji przedstawiają dane hierarchii schematu na potrzeby uruchamiania, środowisko uruchomieniowe sieci i innych ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4f803-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="4f803-106">Dla informacji o typach, format i lokalizację plików konfiguracji, zobacz artykuł [konfigurowania aplikacji](~/docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f803-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](~/docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="4f803-107">Zapoznaj się z XML, jeśli chcesz bezpośrednio modyfikować pliki konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="4f803-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4f803-108">Tagi XML oraz atrybuty w plikach konfiguracji jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="4f803-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4f803-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4f803-109">In this section</span></span>

<span data-ttu-id="4f803-110">[**\<Konfiguracja >** elementu](~/docs/framework/configure-apps/file-schema/configuration-element.md) w tym artykule opisano `<configuration>` element, który jest elementem najwyższego poziomu dla wszystkich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4f803-110">[**\<configuration>** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="4f803-111">[**\<assemblybinding — >** elementu](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) określa zestaw powiązania zasad na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4f803-111">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="4f803-112">[**\<linkedconfiguration — >** elementu](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Określa plik konfiguracji do uwzględnienia.</span><span class="sxs-lookup"><span data-stu-id="4f803-112">[**\<linkedConfiguration>** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="4f803-113">[Schemat ustawień uruchamiania](~/docs/framework/configure-apps/file-schema/startup/index.md) opisano elementy, które określenie, którą wersję środowiska CLR do użycia.</span><span class="sxs-lookup"><span data-stu-id="4f803-113">[Startup Settings Schema](~/docs/framework/configure-apps/file-schema/startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="4f803-114">[Schemat ustawień środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/index.md) opisano elementy, które skonfigurować zachowanie zestawu powiązania i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4f803-114">[Runtime Settings Schema](~/docs/framework/configure-apps/file-schema/runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="4f803-115">[Schemat ustawień sieci](~/docs/framework/configure-apps/file-schema/network/index.md) opisano elementy, które określają sposób programu .NET Framework łączy się z Internetem.</span><span class="sxs-lookup"><span data-stu-id="4f803-115">[Network Settings Schema](~/docs/framework/configure-apps/file-schema/network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="4f803-116">[Schemat ustawień kryptografii](~/docs/framework/configure-apps/file-schema/cryptography/index.md) opisano elementy, które mapują algorytm przyjaznej nazwy klasy, które implementują algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="4f803-116">[Cryptography Settings Schema](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="4f803-117">[Schemat sekcji konfiguracji](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) opisano elementy służące do tworzenia i Użyj sekcji konfiguracji w celu ustawienia niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="4f803-117">[Configuration Sections Schema](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="4f803-118">[Schemat ustawień debugowania i śledzenia](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) opisano elementy określające przełączniki śledzenia i odbiorników.</span><span class="sxs-lookup"><span data-stu-id="4f803-118">[Trace and Debug Settings Schema](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="4f803-119">[Schemat ustawień dostawcy języka i kompilatora](~/docs/framework/configure-apps/file-schema/compiler/index.md) opisano elementy, które będzie określić konfigurację kompilatora dla dostawcy dostępnych języków.</span><span class="sxs-lookup"><span data-stu-id="4f803-119">[Compiler and Language Provider Settings Schema](~/docs/framework/configure-apps/file-schema/compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="4f803-120">[Schemat ustawień aplikacji](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) opisano elementy, które umożliwiają aplikacji dla formularzy systemu Windows lub programu ASP.NET do przechowywania i pobierania ustawień zakresu aplikacji i zakresu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4f803-120">[Application Settings Schema](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="4f803-121">[Schemat ustawień aplikacji](~/docs/framework/configure-apps/file-schema/appsettings/index.md) zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki plików, adresy URL usługi XML sieci Web lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f803-121">[App Settings Schema](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="4f803-122">[Schemat ustawień w sieci Web](~/docs/framework/configure-apps/file-schema/web/index.md) wszystkie elementy w schemat ustawień sieci Web, który zawiera elementy dotyczące konfigurowania, jak działa ASP.NET przy użyciu aplikacji hosta, takich jak IIS.</span><span class="sxs-lookup"><span data-stu-id="4f803-122">[Web Settings Schema](~/docs/framework/configure-apps/file-schema/web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="4f803-123">Używane w *konfigurację Aspnet.config* plików.</span><span class="sxs-lookup"><span data-stu-id="4f803-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="4f803-124">[Schemat konfiguracji formularzy systemu Windows](winforms/index.md) wszystkie elementy w sekcji konfiguracji aplikacji formularzy systemu Windows, która zawiera dostosowania, takie jak obsługa DPI wielu monitorów i wysoki.</span><span class="sxs-lookup"><span data-stu-id="4f803-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="4f803-125">[Schemat konfiguracji programu WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md) wszystkie elementy, które umożliwiają skonfigurowanie WCF usługi i aplikacje klienckie.</span><span class="sxs-lookup"><span data-stu-id="4f803-125">[WCF Configuration Schema](~/docs/framework/configure-apps/file-schema/wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="4f803-126">[Składnia dyrektywy WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) w tym artykule opisano `@ServiceHost` dyrektywy, który definiuje atrybuty specyficzne dla strony używany przez kompilator .svc.</span><span class="sxs-lookup"><span data-stu-id="4f803-126">[WCF Directive Syntax](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="4f803-127">[Schemat konfiguracji WIF](windows-identity-foundation/index.md) wszystkie elementy schemat konfiguracji systemu Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="4f803-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4f803-128">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="4f803-128">Related sections</span></span>

<span data-ttu-id="4f803-129">[Schemat ustawień komunikacji zdalnej](http://msdn.microsoft.com/en-us/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) opisano elementy służące do konfiguracji klienta i serwera aplikacji, które implementuje komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="4f803-129">[Remoting Settings Schema](http://msdn.microsoft.com/en-us/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="4f803-130">[Schemat ustawień programu ASP.NET](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) opisano elementy, które określają zachowanie aplikacji sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4f803-130">[ASP.NET Settings Schema](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="4f803-131">[Schemat ustawień usługi w sieci Web](http://msdn.microsoft.com/en-us/f84d6d55-1add-4eb7-ae46-33df5833ea2e) opisano elementy, które kontrolują zachowanie usługi sieci Web ASP.NET i klientów.</span><span class="sxs-lookup"><span data-stu-id="4f803-131">[Web Services Settings Schema](http://msdn.microsoft.com/en-us/f84d6d55-1add-4eb7-ae46-33df5833ea2e) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="4f803-132">[Konfigurowanie aplikacji programu .NET Framework](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) opisano sposób konfigurowania zabezpieczeń, powiązań zestawów i komunikacji zdalnej w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f803-132">[Configuring .NET Framework Apps](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
