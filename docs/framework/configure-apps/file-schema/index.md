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
ms.openlocfilehash: 35ed53fc480e218df595794f80af2458f3ecec38
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039156"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="9d91d-102">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d91d-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="9d91d-103">Pliki konfiguracji to standardowe pliki XML, których można użyć do zmiany ustawień i ustawienia zasad dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d91d-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="9d91d-104">Schemat konfiguracji .NET Framework składa się z elementów, których można użyć w plikach konfiguracji w celu sterowania zachowaniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d91d-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="9d91d-105">Spis treści tej sekcji odzwierciedla hierarchię schematu dla uruchamiania, środowiska uruchomieniowego, sieci i innych typów ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d91d-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="9d91d-106">Aby uzyskać informacje o typach, formacie i lokalizacji plików konfiguracji, zobacz [Konfigurowanie aplikacji](../index.md).</span><span class="sxs-lookup"><span data-stu-id="9d91d-106">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="9d91d-107">Zapoznaj się z plikiem XML, jeśli chcesz bezpośrednio edytować pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d91d-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d91d-108">W przypadku tagów i atrybutów XML w plikach konfiguracji rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="9d91d-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9d91d-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9d91d-109">In this section</span></span>

<span data-ttu-id="9d91d-110">[ **\<> elementu konfiguracji** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-110">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="9d91d-111">Element najwyższego poziomu dla wszystkich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d91d-111">The top-level element for all configuration files.</span></span>

<span data-ttu-id="9d91d-112">[Element **\<assemblybinding >** ](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="9d91d-113">Określa zasady powiązań zestawów na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d91d-113">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="9d91d-114">[ **\<element > linkedConfiguration** ](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="9d91d-115">Określa plik konfiguracji, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="9d91d-115">Specifies a configuration file to include.</span></span>

<span data-ttu-id="9d91d-116">\ [schematu ustawień uruchamiania](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-116">[Startup Settings Schema](./startup/index.md)\</span></span>
<span data-ttu-id="9d91d-117">Elementy określające wersję środowiska uruchomieniowego języka wspólnego do użycia.</span><span class="sxs-lookup"><span data-stu-id="9d91d-117">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="9d91d-118">[Schemat ustawień środowiska uruchomieniowego](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-118">[Runtime Settings Schema](./runtime/index.md)</span></span>\
<span data-ttu-id="9d91d-119">Elementy, które konfigurują powiązanie zestawu i zachowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9d91d-119">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="9d91d-120">[Schemat ustawień sieciowych](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-120">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="9d91d-121">Elementy, które określają, w jaki sposób .NET Framework nawiązuje połączenie z Internetem.</span><span class="sxs-lookup"><span data-stu-id="9d91d-121">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="9d91d-122">\ [schematu ustawień kryptografii](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-122">[Cryptography Settings Schema](./cryptography/index.md)\</span></span>
<span data-ttu-id="9d91d-123">Elementy, które mapują przyjazne nazwy algorytmów na klasy implementujące algorytmy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="9d91d-123">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="9d91d-124">\ [schematu sekcji konfiguracyjnych](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-124">[Configuration Sections Schema](configuration-sections-schema.md)\</span></span>
<span data-ttu-id="9d91d-125">Elementy służące do tworzenia i używania sekcji konfiguracyjnych ustawień niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="9d91d-125">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="9d91d-126">[Ustawienia śledzenia i debugowania schematu](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-126">[Trace and Debug Settings Schema](./trace-debug/index.md)</span></span>\
<span data-ttu-id="9d91d-127">Elementy, które określają przełączniki śledzenia i odbiorniki.</span><span class="sxs-lookup"><span data-stu-id="9d91d-127">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="9d91d-128">[Schemat ustawień kompilatora i dostawcy języka](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-128">[Compiler and Language Provider Settings Schema](./compiler/index.md)</span></span>\
<span data-ttu-id="9d91d-129">Elementy, które określają konfigurację kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="9d91d-129">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="9d91d-130">\ [schematu ustawień aplikacji](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-130">[Application Settings Schema](application-settings-schema.md)\</span></span>
<span data-ttu-id="9d91d-131">Elementy, które umożliwiają aplikacji Windows Forms lub ASP.NET przechowywanie i pobieranie ustawień zakresu aplikacji i zakresu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9d91d-131">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="9d91d-132">\ [schematu ustawień aplikacji](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-132">[App Settings Schema](./appsettings/index.md)\</span></span>
<span data-ttu-id="9d91d-133">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d91d-133">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="9d91d-134">\ [schematu ustawień sieci Web](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-134">[Web Settings Schema](./web/index.md)\</span></span>
<span data-ttu-id="9d91d-135">Elementy służące do konfigurowania sposobu działania ASP.NET z aplikacją hosta, taką jak usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="9d91d-135">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="9d91d-136">Używany w plikach *ASPNET. config* .</span><span class="sxs-lookup"><span data-stu-id="9d91d-136">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="9d91d-137">\ [schematu konfiguracji Windows Forms](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-137">[Windows Forms Configuration Schema](winforms/index.md)\</span></span>
<span data-ttu-id="9d91d-138">Wszystkie elementy w sekcji Konfiguracja aplikacji Windows Forms, w tym takie, jak takie dostosowania, jak obsługa wielomonitorów i wysokiej rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="9d91d-138">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="9d91d-139">\ [schematu konfiguracji WCF](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-139">[WCF Configuration Schema](./wcf/index.md)\</span></span>
<span data-ttu-id="9d91d-140">Wszystkie elementy, które umożliwiają skonfigurowanie usługi WCF i aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="9d91d-140">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="9d91d-141">[Składnia dyrektywy WCF](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-141">[WCF Directive Syntax](./wcf-directive/index.md)</span></span>\
<span data-ttu-id="9d91d-142">Opisuje dyrektywę `@ServiceHost`, która definiuje atrybuty specyficzne dla strony używane przez kompilator SVC.</span><span class="sxs-lookup"><span data-stu-id="9d91d-142">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="9d91d-143">\ [schematu konfiguracji WIF](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d91d-143">[WIF Configuration Schema](windows-identity-foundation/index.md)\</span></span>
<span data-ttu-id="9d91d-144">Wszystkie elementy schematu konfiguracji Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="9d91d-144">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="9d91d-145">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9d91d-145">Related sections</span></span>

<span data-ttu-id="9d91d-146">\ [schematu ustawień usług zdalnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9d91d-146">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))\</span></span>
<span data-ttu-id="9d91d-147">Opisuje elementy, które konfigurują aplikacje klienta i serwera, które implementują komunikację zdalną.</span><span class="sxs-lookup"><span data-stu-id="9d91d-147">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="9d91d-148">\ [schematu ustawień ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9d91d-148">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))\</span></span>
<span data-ttu-id="9d91d-149">Opisuje elementy kontrolujące zachowanie aplikacji sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9d91d-149">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="9d91d-150">\ [schematu ustawień usług sieci Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9d91d-150">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))\</span></span>
<span data-ttu-id="9d91d-151">Opisuje elementy kontrolujące zachowanie usług sieci Web ASP.NET i ich klientów.</span><span class="sxs-lookup"><span data-stu-id="9d91d-151">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="9d91d-152">[Konfigurowanie aplikacji .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9d91d-152">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="9d91d-153">Opisuje sposób konfigurowania zabezpieczeń, powiązań zestawów i komunikacji zdalnej w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d91d-153">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
