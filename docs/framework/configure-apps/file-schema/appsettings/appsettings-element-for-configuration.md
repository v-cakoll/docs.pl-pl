---
title: '&lt;appSettings&gt; elementu &lt;konfiguracji&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cb59120d88816ea193bd8588b152d6b848b682d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="62ff8-102">\<appSettings > elementu \<configuration ></span><span class="sxs-lookup"><span data-stu-id="62ff8-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="62ff8-103">Zawiera ustawienia aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="62ff8-103">Contains custom application settings.</span></span> <span data-ttu-id="62ff8-104">Jest to sekcję konfiguracji wstępnie zdefiniowanych dostarczane przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62ff8-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="62ff8-105">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="62ff8-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="62ff8-106">&nbsp;&nbsp;**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="62ff8-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="62ff8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="62ff8-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="62ff8-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="62ff8-108">Attribute</span></span>

|           | <span data-ttu-id="62ff8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="62ff8-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="62ff8-110">**plik**</span><span class="sxs-lookup"><span data-stu-id="62ff8-110">**file**</span></span>  | <span data-ttu-id="62ff8-111">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="62ff8-111">Optional attribute.</span></span><br><br><span data-ttu-id="62ff8-112">Określa ścieżkę względną do zewnętrznego pliku zawierającego ustawienia konfiguracji aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="62ff8-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="62ff8-113">Określony plik zawiera ten sam rodzaj ustawień, które są określone w  **\<Dodaj >**,  **\<Usuń >**, i  **\<Wyczyść >** elementów i używa tej samej pary klucz wartość w formacie tych elementów.</span><span class="sxs-lookup"><span data-stu-id="62ff8-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="62ff8-114">Określona ścieżka jest względną do pliku konfiguracji głównego.</span><span class="sxs-lookup"><span data-stu-id="62ff8-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="62ff8-115">Dla aplikacji formularzy systemu Windows, jest to folder binarne (takie jak */bin/debug*), nie lokalizację pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="62ff8-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="62ff8-116">Dla aplikacji formularzy sieci Web, ścieżka jest względem katalogu głównego aplikacji, których *web.config* znajduje się plik.</span><span class="sxs-lookup"><span data-stu-id="62ff8-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="62ff8-117">Należy pamiętać, środowisko uruchomieniowe ignoruje atrybut, jeśli nie można odnaleźć określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="62ff8-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="62ff8-118">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="62ff8-118">Parent element</span></span>

|     | <span data-ttu-id="62ff8-119">Opis</span><span class="sxs-lookup"><span data-stu-id="62ff8-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="62ff8-120">**\<Konfiguracja >** — Element</span><span class="sxs-lookup"><span data-stu-id="62ff8-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="62ff8-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62ff8-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="62ff8-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="62ff8-122">Child elements</span></span>

|     | <span data-ttu-id="62ff8-123">Opis</span><span class="sxs-lookup"><span data-stu-id="62ff8-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="62ff8-124">**\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="62ff8-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="62ff8-125">Dodaje ustawienia aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="62ff8-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="62ff8-126">**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="62ff8-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="62ff8-127">Czyści wszystkie ustawienia zdefiniowane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="62ff8-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="62ff8-128">**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="62ff8-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="62ff8-129">Usuwa ustawienie wcześniej określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="62ff8-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="62ff8-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62ff8-130">Remarks</span></span>

<span data-ttu-id="62ff8-131">**\<AppSettings >** element przechowuje informacje o konfiguracji niestandardowej aplikacji, takich jak parametry połączenia bazy danych, ścieżki do pliku, adresy URL usługi XML sieci Web lub innych informacji konfiguracji niestandardowej dla aplikacja.</span><span class="sxs-lookup"><span data-stu-id="62ff8-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="62ff8-132">Pary klucz wartość określona w  **\<appSettings >** elementu są dostępne w kodu za pomocą <xref:System.Configuration.ConfigurationSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="62ff8-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="62ff8-133">Można użyć **pliku** atrybutu w  **\<appSettings >** elementu *Web.config* i pliki konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="62ff8-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="62ff8-134">Ten atrybut określa plik konfiguracji, który udostępnia dodatkowe ustawienia lub zastępuje ustawienia określone w  **\<appSettings >** elementu.</span><span class="sxs-lookup"><span data-stu-id="62ff8-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="62ff8-135">**Pliku** atrybut może być używany w źródła formantu zespołu scenariusze programowania, np. gdy użytkownik chce, aby zastąpić ustawienia projektu określony w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="62ff8-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="62ff8-136">Pliki konfiguracji określone przez **pliku** atrybut musi mieć węzeł główny  **\<appSettings >** zamiast  **\<konfiguracji >**.</span><span class="sxs-lookup"><span data-stu-id="62ff8-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="62ff8-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="62ff8-137">Example</span></span>

<span data-ttu-id="62ff8-138">W poniższym przykładzie przedstawiono plik ustawień zewnętrznej aplikacji (*custom.config*) definiuje ustawienia aplikacji niestandardowej:</span><span class="sxs-lookup"><span data-stu-id="62ff8-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="62ff8-139">W poniższym przykładzie przedstawiono plik konfiguracji aplikacji, który wykorzystuje ustawienia w pliku ustawień zewnętrznych, a następnie ustawia ustawienie aplikacji z własnych:</span><span class="sxs-lookup"><span data-stu-id="62ff8-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="62ff8-140">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="62ff8-140">Configuration file</span></span>

<span data-ttu-id="62ff8-141">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="62ff8-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="62ff8-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62ff8-142">See also</span></span>

[<span data-ttu-id="62ff8-143">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="62ff8-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
