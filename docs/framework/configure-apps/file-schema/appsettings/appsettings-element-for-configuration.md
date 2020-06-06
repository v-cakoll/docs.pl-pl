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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155534"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="a2cc3-102">\<appSettings>, element dla \<configuration></span><span class="sxs-lookup"><span data-stu-id="a2cc3-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="a2cc3-103">Zawiera niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-103">Contains custom application settings.</span></span> <span data-ttu-id="a2cc3-104">Jest to wstępnie zdefiniowana sekcja konfiguracji udostępniona przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="a2cc3-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="a2cc3-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a2cc3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2cc3-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="a2cc3-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a2cc3-107">Attribute</span></span>

|           | <span data-ttu-id="a2cc3-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a2cc3-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a2cc3-109">**rozszerzeniem**</span><span class="sxs-lookup"><span data-stu-id="a2cc3-109">**file**</span></span>  | <span data-ttu-id="a2cc3-110">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-110">Optional attribute.</span></span><br><br><span data-ttu-id="a2cc3-111">Określa ścieżkę względną do pliku zewnętrznego zawierającego niestandardowe ustawienia konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="a2cc3-112">Określony plik zawiera ten sam rodzaj ustawień, które są określone w **\<add>** , **\<remove>** , i **\<clear>** i używa tego samego formatu pary klucz/wartość, co te elementy.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="a2cc3-113">Określona ścieżka jest względna w stosunku do głównego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="a2cc3-114">W przypadku aplikacji Windows Forms jest to folder binarny (na przykład */bin/debug*), a nie lokalizacja pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="a2cc3-115">W przypadku aplikacji formularzy sieci Web ścieżka jest określana względem katalogu głównego aplikacji, w którym znajduje się plik *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="a2cc3-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="a2cc3-116">Środowisko uruchomieniowe ignoruje atrybut, jeśli nie można znaleźć określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a2cc3-117">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="a2cc3-117">Parent element</span></span>

|     | <span data-ttu-id="a2cc3-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a2cc3-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a2cc3-119">**\<configuration>** Postaci</span><span class="sxs-lookup"><span data-stu-id="a2cc3-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="a2cc3-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a2cc3-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a2cc3-121">Child elements</span></span>

|     | <span data-ttu-id="a2cc3-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a2cc3-122">Description</span></span> |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="a2cc3-123">Dodaje niestandardowe ustawienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-123">Adds a custom application setting.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="a2cc3-124">Czyści wszystkie wcześniej zdefiniowane ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-124">Clears all previously defined application settings.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="a2cc3-125">Usuwa poprzednio zdefiniowane ustawienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-125">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a2cc3-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2cc3-126">Remarks</span></span>

<span data-ttu-id="a2cc3-127">**\<appSettings>** Element przechowuje niestandardowe informacje o konfiguracji aplikacji, takie jak parametry połączenia bazy danych, ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-127">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="a2cc3-128">Pary klucz/wartość określone w **\<appSettings>** elemencie są dostępne w kodzie przy użyciu <xref:System.Configuration.ConfigurationSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-128">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="a2cc3-129">Możesz użyć atrybutu **pliku** w elemencie w pliku **\<appSettings>** *Web. config* i plikach konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-129">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="a2cc3-130">Ten atrybut określa plik konfiguracji, który zawiera dodatkowe ustawienia lub zastępuje ustawienia określone w **\<appSettings>** elemencie.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-130">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="a2cc3-131">Atrybut **pliku** może być używany w scenariuszach tworzenia zespołu kontroli źródła, na przykład gdy użytkownik chce zastąpić ustawienia projektu określone w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-131">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="a2cc3-132">Pliki konfiguracyjne określone przez atrybut **pliku** muszą mieć węzeł główny, **\<appSettings>** a nie **\<configuration>** .</span><span class="sxs-lookup"><span data-stu-id="a2cc3-132">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="a2cc3-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2cc3-133">Example</span></span>

<span data-ttu-id="a2cc3-134">W poniższym przykładzie przedstawiono zewnętrzny plik ustawień aplikacji (*Custom. config*) definiujący niestandardowe ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="a2cc3-134">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="a2cc3-135">Poniższy przykład przedstawia plik konfiguracji aplikacji, który używa ustawienia w pliku ustawień zewnętrznych i ustawia własne ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="a2cc3-135">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="a2cc3-136">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a2cc3-136">Configuration file</span></span>

<span data-ttu-id="a2cc3-137">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2cc3-137">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2cc3-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2cc3-138">See also</span></span>

- [<span data-ttu-id="a2cc3-139">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2cc3-139">Configuration file schema for the .NET Framework</span></span>](../index.md)
