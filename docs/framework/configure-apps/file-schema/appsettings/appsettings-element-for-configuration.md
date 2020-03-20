---
title: <appSettings>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155534"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="85440-102">\<appSettings> elementem \<> konfiguracyjnym</span><span class="sxs-lookup"><span data-stu-id="85440-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="85440-103">Zawiera niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85440-103">Contains custom application settings.</span></span> <span data-ttu-id="85440-104">Jest to wstępnie zdefiniowana sekcja konfiguracji dostarczona przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85440-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="85440-105">&nbsp;konfiguracji appSettings>[\*\* \<\*\*](../configuration-element.md) &nbsp; \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="85440-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="85440-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="85440-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="85440-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="85440-107">Attribute</span></span>

|           | <span data-ttu-id="85440-108">Opis</span><span class="sxs-lookup"><span data-stu-id="85440-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="85440-109">**Plik**</span><span class="sxs-lookup"><span data-stu-id="85440-109">**file**</span></span>  | <span data-ttu-id="85440-110">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="85440-110">Optional attribute.</span></span><br><br><span data-ttu-id="85440-111">Określa względną ścieżkę do pliku zewnętrznego zawierającego niestandardowe ustawienia konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85440-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="85440-112">Określony plik zawiera ten sam rodzaj ustawień, które są określone \*\* \< \*\*w \*\* \<>dodawania **, usuń>i \*\* \<wyczyść>** elementy i używa tego samego formatu pary klucz/wartość co te elementy.</span><span class="sxs-lookup"><span data-stu-id="85440-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="85440-113">Określona ścieżka jest względem głównego pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="85440-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="85440-114">W przypadku aplikacji Windows Forms jest to folder binarny (na przykład */bin/debug*), a nie lokalizacja pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85440-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="85440-115">W przypadku aplikacji formularzy sieci Web ścieżka jest względem katalogu głównego aplikacji, w którym znajduje się plik *web.config.*</span><span class="sxs-lookup"><span data-stu-id="85440-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="85440-116">Środowisko wykonawcze ignoruje atrybut, jeśli nie można odnaleźć określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="85440-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="85440-117">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="85440-117">Parent element</span></span>

|     | <span data-ttu-id="85440-118">Opis</span><span class="sxs-lookup"><span data-stu-id="85440-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="85440-119">\*\* \<>konfiguracyjne\*\* Element</span><span class="sxs-lookup"><span data-stu-id="85440-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="85440-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85440-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="85440-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="85440-121">Child elements</span></span>

|     | <span data-ttu-id="85440-122">Opis</span><span class="sxs-lookup"><span data-stu-id="85440-122">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="85440-123">**\<dodaj>**</span><span class="sxs-lookup"><span data-stu-id="85440-123">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="85440-124">Dodaje niestandardowe ustawienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85440-124">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="85440-125">**\<wyraźne>**</span><span class="sxs-lookup"><span data-stu-id="85440-125">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="85440-126">Czyści wszystkie wcześniej zdefiniowane ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85440-126">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="85440-127">**\<usuń>**</span><span class="sxs-lookup"><span data-stu-id="85440-127">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="85440-128">Usuwa uprzednio zdefiniowane ustawienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85440-128">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="85440-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85440-129">Remarks</span></span>

<span data-ttu-id="85440-130">\*\* \<AppSettings>\*\* element przechowuje informacje o konfiguracji aplikacji niestandardowych, takie jak parametry połączenia bazy danych, ścieżki plików, adresy URL usługi sieci Web XML lub inne niestandardowe informacje konfiguracyjne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85440-130">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="85440-131">Pary klucz/wartość określone w \*\* \<appSettings>\*\* element są dostępne w <xref:System.Configuration.ConfigurationSettings> kodzie przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="85440-131">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="85440-132">Atrybutu **pliku** można użyć w \*\* \<appSettings>\*\* element *web.config* i pliki konfiguracyjne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85440-132">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="85440-133">Ten atrybut określa plik konfiguracji, który zawiera dodatkowe ustawienia lub zastępuje ustawienia określone w \*\* \<appSettings>\*\* element.</span><span class="sxs-lookup"><span data-stu-id="85440-133">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="85440-134">Atrybut **pliku** może służyć w scenariuszach tworzenia zespołu kontroli źródła, takich jak gdy użytkownik chce zastąpić ustawienia projektu określone w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85440-134">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="85440-135">Pliki konfiguracyjne określone przez atrybut **pliku** muszą mieć węzeł główny \*\* \<appSettings>,\*\* a nie \*\* \<>konfiguracji \*\*.</span><span class="sxs-lookup"><span data-stu-id="85440-135">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="85440-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="85440-136">Example</span></span>

<span data-ttu-id="85440-137">W poniższym przykładzie pokazano plik ustawień aplikacji zewnętrznej *(custom.config),* który definiuje niestandardowe ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="85440-137">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="85440-138">W poniższym przykładzie pokazano plik konfiguracji aplikacji, który zużywa ustawienie w pliku ustawień zewnętrznych i ustawia własne ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="85440-138">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="85440-139">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="85440-139">Configuration file</span></span>

<span data-ttu-id="85440-140">Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85440-140">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="85440-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85440-141">See also</span></span>

- [<span data-ttu-id="85440-142">Schemat pliku konfiguracyjnego programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="85440-142">Configuration file schema for the .NET Framework</span></span>](../index.md)
