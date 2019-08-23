---
title: Schemat ustawień aplikacji
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d02f9f952c0ca7651d27571111a2d29f3d1130fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921299"
---
# <a name="app-settings-schema"></a><span data-ttu-id="b6b3c-102">Schemat ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="b6b3c-102">App Settings schema</span></span>

<span data-ttu-id="b6b3c-103">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="b6b3c-104">[ **\<> konfiguracji**](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b6b3c-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="b6b3c-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="b6b3c-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="b6b3c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add>** ](add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="b6b3c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="b6b3c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear>** ](clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="b6b3c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="b6b3c-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<remove>** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="b6b3c-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="b6b3c-109">Element</span><span class="sxs-lookup"><span data-stu-id="b6b3c-109">Element</span></span> | <span data-ttu-id="b6b3c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b6b3c-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="b6b3c-111"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="b6b3c-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="b6b3c-112">**Zawiera\<Dodaj >** ,  **\<Wyczyść >** i  **\<Usuń Tagi >** w celu kontrolowania ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="b6b3c-113">Ma opcjonalny atrybut **pliku** .</span><span class="sxs-lookup"><span data-stu-id="b6b3c-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="b6b3c-114"> **\<add>** </span><span class="sxs-lookup"><span data-stu-id="b6b3c-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="b6b3c-115">Definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-115">Defines a setting.</span></span> <span data-ttu-id="b6b3c-116">Element podrzędny **> appSettings.\<**</span><span class="sxs-lookup"><span data-stu-id="b6b3c-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="b6b3c-117">Wymaga atrybutów **klucza** i **wartości** .</span><span class="sxs-lookup"><span data-stu-id="b6b3c-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="b6b3c-118"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="b6b3c-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="b6b3c-119">Czyści wszystkie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-119">Clears all settings.</span></span> <span data-ttu-id="b6b3c-120">Element podrzędny **> appSettings.\<**</span><span class="sxs-lookup"><span data-stu-id="b6b3c-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="b6b3c-121">Nie ma atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-121">Has no attributes.</span></span> |
| [<span data-ttu-id="b6b3c-122"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="b6b3c-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="b6b3c-123">Usuwa ustawienie.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-123">Removes a setting.</span></span> <span data-ttu-id="b6b3c-124">Element podrzędny **> appSettings.\<**</span><span class="sxs-lookup"><span data-stu-id="b6b3c-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="b6b3c-125">Wymaga atrybutu **klucza** .</span><span class="sxs-lookup"><span data-stu-id="b6b3c-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="b6b3c-126">\<appSettings, > element</span><span class="sxs-lookup"><span data-stu-id="b6b3c-126">\<appSettings> element</span></span>

<span data-ttu-id="b6b3c-127">Ten element zawiera  **\<Dodawanie >** ,  **\<czyszczenie >** i  **\<Usuwanie tagów >** w celu kontrolowania ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="b6b3c-128">Definiuje opcjonalny atrybut dla **pliku**.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="b6b3c-129">\<Dodaj element ></span><span class="sxs-lookup"><span data-stu-id="b6b3c-129">\<add> element</span></span>

<span data-ttu-id="b6b3c-130">Dodaje niestandardowe ustawienie aplikacji jako parę nazwa/wartość do kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="b6b3c-131">Definiuje atrybuty **klucza** i **wartości**.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="b6b3c-132">\<Wyczyść element ></span><span class="sxs-lookup"><span data-stu-id="b6b3c-132">\<clear> element</span></span>

<span data-ttu-id="b6b3c-133">Usuwa wszystkie odwołania do dziedziczonych ustawień aplikacji niestandardowych i zezwala tylko na odwołania, które są dodawane przez  **\<Dodawanie >** elementów po  **\<elemencie Clear >** .</span><span class="sxs-lookup"><span data-stu-id="b6b3c-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="b6b3c-134">Nie definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="b6b3c-135">\<Usuń element ></span><span class="sxs-lookup"><span data-stu-id="b6b3c-135">\<remove> element</span></span>

<span data-ttu-id="b6b3c-136">Usuwa odwołanie do dziedziczonego ustawienia aplikacji niestandardowej z kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="b6b3c-137">Definiuje atrybut dla **klucza**.</span><span class="sxs-lookup"><span data-stu-id="b6b3c-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="b6b3c-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6b3c-138">Example</span></span>

<span data-ttu-id="b6b3c-139">W poniższym przykładzie przedstawiono zewnętrzny plik ustawień aplikacji (*Custom. config*) definiujący niestandardowe ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b6b3c-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="b6b3c-140">Poniższy przykład przedstawia plik konfiguracji aplikacji, który używa ustawienia w pliku ustawień zewnętrznych i ustawia własne ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b6b3c-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b6b3c-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6b3c-141">See also</span></span>

- [<span data-ttu-id="b6b3c-142">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="b6b3c-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="b6b3c-143">Architektura ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="b6b3c-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
