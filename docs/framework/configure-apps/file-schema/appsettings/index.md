---
title: Schemat ustawień aplikacji
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 609ddba9cd4d58f9c388cf669039ee128e87efd0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088077"
---
# <a name="app-settings-schema"></a><span data-ttu-id="f05b4-102">Schemat ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="f05b4-102">App Settings schema</span></span>

<span data-ttu-id="f05b4-103">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f05b4-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="f05b4-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f05b4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f05b4-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="f05b4-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="f05b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dodaj >** ](add-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="f05b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)</span></span>\
<span data-ttu-id="f05b4-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wyczyść >** ](clear-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="f05b4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)</span></span>\
<span data-ttu-id="f05b4-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Usuń >** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="f05b4-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="f05b4-109">Element</span><span class="sxs-lookup"><span data-stu-id="f05b4-109">Element</span></span> | <span data-ttu-id="f05b4-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f05b4-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="f05b4-111"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="f05b4-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="f05b4-112">Zawiera **\<dodaj >** , **\<wyczyść >** i **\<Usuń Tagi >** w celu kontrolowania ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f05b4-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f05b4-113">Ma opcjonalny atrybut **pliku** .</span><span class="sxs-lookup"><span data-stu-id="f05b4-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="f05b4-114"> **\<Dodaj >** </span><span class="sxs-lookup"><span data-stu-id="f05b4-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="f05b4-115">Definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="f05b4-115">Defines a setting.</span></span> <span data-ttu-id="f05b4-116">Element podrzędny **\<AppSettings**.</span><span class="sxs-lookup"><span data-stu-id="f05b4-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f05b4-117">Wymaga atrybutów **klucza** i **wartości** .</span><span class="sxs-lookup"><span data-stu-id="f05b4-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="f05b4-118"> **\<Wyczyść >** </span><span class="sxs-lookup"><span data-stu-id="f05b4-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="f05b4-119">Czyści wszystkie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="f05b4-119">Clears all settings.</span></span> <span data-ttu-id="f05b4-120">Element podrzędny **\<AppSettings**.</span><span class="sxs-lookup"><span data-stu-id="f05b4-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f05b4-121">Nie ma atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f05b4-121">Has no attributes.</span></span> |
| [<span data-ttu-id="f05b4-122"> **\<Usuń >** </span><span class="sxs-lookup"><span data-stu-id="f05b4-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="f05b4-123">Usuwa ustawienie.</span><span class="sxs-lookup"><span data-stu-id="f05b4-123">Removes a setting.</span></span> <span data-ttu-id="f05b4-124">Element podrzędny **\<AppSettings**.</span><span class="sxs-lookup"><span data-stu-id="f05b4-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f05b4-125">Wymaga atrybutu **klucza** .</span><span class="sxs-lookup"><span data-stu-id="f05b4-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="f05b4-126">\<appSettings > element</span><span class="sxs-lookup"><span data-stu-id="f05b4-126">\<appSettings> element</span></span>

<span data-ttu-id="f05b4-127">Ten element zawiera **\<dodaj >** , **\<wyczyść >** i **\<Usuń Tagi >** w celu kontrolowania ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f05b4-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f05b4-128">Definiuje opcjonalny atrybut dla **pliku**.</span><span class="sxs-lookup"><span data-stu-id="f05b4-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="f05b4-129">\<dodać elementu ></span><span class="sxs-lookup"><span data-stu-id="f05b4-129">\<add> element</span></span>

<span data-ttu-id="f05b4-130">Dodaje niestandardowe ustawienie aplikacji jako parę nazwa/wartość do kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f05b4-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="f05b4-131">Definiuje atrybuty **klucza** i **wartości**.</span><span class="sxs-lookup"><span data-stu-id="f05b4-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="f05b4-132">\<Wyczyść > elementu</span><span class="sxs-lookup"><span data-stu-id="f05b4-132">\<clear> element</span></span>

<span data-ttu-id="f05b4-133">Usuwa wszystkie odwołania do dziedziczonych ustawień aplikacji niestandardowych i zezwala tylko na odwołania, które są dodawane przez **\<dodaj >** elementy po **\<Wyczyść >** elementu.</span><span class="sxs-lookup"><span data-stu-id="f05b4-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="f05b4-134">Nie definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f05b4-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="f05b4-135">\<usunąć elementu ></span><span class="sxs-lookup"><span data-stu-id="f05b4-135">\<remove> element</span></span>

<span data-ttu-id="f05b4-136">Usuwa odwołanie do dziedziczonego ustawienia aplikacji niestandardowej z kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f05b4-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="f05b4-137">Definiuje atrybut dla **klucza**.</span><span class="sxs-lookup"><span data-stu-id="f05b4-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="f05b4-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="f05b4-138">Example</span></span>

<span data-ttu-id="f05b4-139">W poniższym przykładzie przedstawiono zewnętrzny plik ustawień aplikacji (*Custom. config*) definiujący niestandardowe ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="f05b4-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="f05b4-140">Poniższy przykład przedstawia plik konfiguracji aplikacji, który używa ustawienia w pliku ustawień zewnętrznych i ustawia własne ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="f05b4-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f05b4-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f05b4-141">See also</span></span>

- [<span data-ttu-id="f05b4-142">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="f05b4-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="f05b4-143">Architektura ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="f05b4-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
