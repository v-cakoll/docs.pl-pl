---
title: <appSettings>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6112d87afcca8b2f54508d03d3ea4c0781d7e475
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119268"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="c244a-102">\<appSettings > elementu \<Configuration ></span><span class="sxs-lookup"><span data-stu-id="c244a-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="c244a-103">Zawiera niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c244a-103">Contains custom application settings.</span></span> <span data-ttu-id="c244a-104">Jest to wstępnie zdefiniowana sekcja konfiguracji udostępniona przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c244a-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="c244a-105">[ **\<> konfiguracji**](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c244a-105">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="c244a-106">&nbsp;&nbsp; **\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="c244a-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c244a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c244a-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="c244a-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c244a-108">Attribute</span></span>

|           | <span data-ttu-id="c244a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c244a-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c244a-110">**rozszerzeniem**</span><span class="sxs-lookup"><span data-stu-id="c244a-110">**file**</span></span>  | <span data-ttu-id="c244a-111">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c244a-111">Optional attribute.</span></span><br><br><span data-ttu-id="c244a-112">Określa ścieżkę względną do pliku zewnętrznego zawierającego niestandardowe ustawienia konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c244a-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="c244a-113">Określony plik zawiera ten sam rodzaj ustawień, które są określone w **\<dodaj >** , **\<usuń >** i **\<Wyczyść elementy >** i używa tego samego formatu pary klucz/wartość, co te elementy.</span><span class="sxs-lookup"><span data-stu-id="c244a-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="c244a-114">Określona ścieżka jest względna w stosunku do głównego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c244a-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="c244a-115">W przypadku aplikacji Windows Forms jest to folder binarny (na przykład */bin/debug*), a nie lokalizacja pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c244a-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="c244a-116">W przypadku aplikacji formularzy sieci Web ścieżka jest określana względem katalogu głównego aplikacji, w którym znajduje się plik *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="c244a-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="c244a-117">Należy pamiętać, że środowisko uruchomieniowe ignoruje atrybut, jeśli nie można znaleźć określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="c244a-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c244a-118">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="c244a-118">Parent element</span></span>

|     | <span data-ttu-id="c244a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c244a-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c244a-120"> **> konfiguracji\<** Postaci</span><span class="sxs-lookup"><span data-stu-id="c244a-120">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="c244a-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c244a-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c244a-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c244a-122">Child elements</span></span>

|     | <span data-ttu-id="c244a-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c244a-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c244a-124"> **\<add>** </span><span class="sxs-lookup"><span data-stu-id="c244a-124">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="c244a-125">Dodaje niestandardowe ustawienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c244a-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="c244a-126"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="c244a-126">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="c244a-127">Czyści wszystkie wcześniej zdefiniowane ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c244a-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="c244a-128"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="c244a-128">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="c244a-129">Usuwa poprzednio zdefiniowane ustawienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c244a-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c244a-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c244a-130">Remarks</span></span>

<span data-ttu-id="c244a-131">**\<appSettings >** element przechowuje niestandardowe informacje o konfiguracji aplikacji, takie jak parametry połączenia bazy danych, ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c244a-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="c244a-132">Pary klucz/wartość określone w **\<AppSettings elementu >** są dostępne w kodzie przy użyciu klasy <xref:System.Configuration.ConfigurationSettings>.</span><span class="sxs-lookup"><span data-stu-id="c244a-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="c244a-133">Można użyć atrybutu **pliku** w **\<AppSettings >** elementu pliku *Web. config* i plików konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c244a-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="c244a-134">Ten atrybut określa plik konfiguracji, który zawiera dodatkowe ustawienia lub zastępuje ustawienia określone w **\<appSettings >** elementu.</span><span class="sxs-lookup"><span data-stu-id="c244a-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="c244a-135">Atrybut **pliku** może być używany w scenariuszach tworzenia zespołu kontroli źródła, na przykład gdy użytkownik chce zastąpić ustawienia projektu określone w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c244a-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="c244a-136">Pliki konfiguracyjne określone przez atrybut **pliku** muszą mieć węzeł główny **\<appSettings >** zamiast **\<> konfiguracji**.</span><span class="sxs-lookup"><span data-stu-id="c244a-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="c244a-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="c244a-137">Example</span></span>

<span data-ttu-id="c244a-138">W poniższym przykładzie przedstawiono zewnętrzny plik ustawień aplikacji (*Custom. config*) definiujący niestandardowe ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="c244a-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="c244a-139">Poniższy przykład przedstawia plik konfiguracji aplikacji, który używa ustawienia w pliku ustawień zewnętrznych i ustawia własne ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="c244a-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="c244a-140">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c244a-140">Configuration file</span></span>

<span data-ttu-id="c244a-141">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c244a-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c244a-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c244a-142">See also</span></span>

- [<span data-ttu-id="c244a-143">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c244a-143">Configuration file schema for the .NET Framework</span></span>](../index.md)
