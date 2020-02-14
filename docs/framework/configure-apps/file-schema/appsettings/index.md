---
title: Schemat ustawień aplikacji
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215428"
---
# <a name="app-settings-schema"></a><span data-ttu-id="67f95-102">Schemat ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="67f95-102">App Settings schema</span></span>

<span data-ttu-id="67f95-103">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67f95-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="67f95-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="67f95-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="67f95-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="67f95-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="67f95-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dodaj >** ](add-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="67f95-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)</span></span>\
<span data-ttu-id="67f95-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wyczyść >** ](clear-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="67f95-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)</span></span>\
<span data-ttu-id="67f95-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Usuń >** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="67f95-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="67f95-109">Element</span><span class="sxs-lookup"><span data-stu-id="67f95-109">Element</span></span> | <span data-ttu-id="67f95-110">Opis</span><span class="sxs-lookup"><span data-stu-id="67f95-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="67f95-111"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="67f95-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="67f95-112">Zawiera **\<dodaj >** , **\<wyczyść >** i **\<Usuń Tagi >** w celu kontrolowania ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67f95-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="67f95-113">Ma opcjonalny atrybut **pliku** .</span><span class="sxs-lookup"><span data-stu-id="67f95-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="67f95-114"> **\<Dodaj >** </span><span class="sxs-lookup"><span data-stu-id="67f95-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="67f95-115">Definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="67f95-115">Defines a setting.</span></span> <span data-ttu-id="67f95-116">Element podrzędny **>\<AppSettings**.</span><span class="sxs-lookup"><span data-stu-id="67f95-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="67f95-117">Wymaga atrybutów **klucza** i **wartości** .</span><span class="sxs-lookup"><span data-stu-id="67f95-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="67f95-118"> **\<Wyczyść >** </span><span class="sxs-lookup"><span data-stu-id="67f95-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="67f95-119">Czyści wszystkie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="67f95-119">Clears all settings.</span></span> <span data-ttu-id="67f95-120">Element podrzędny **>\<AppSettings**.</span><span class="sxs-lookup"><span data-stu-id="67f95-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="67f95-121">Nie ma atrybutów.</span><span class="sxs-lookup"><span data-stu-id="67f95-121">Has no attributes.</span></span> |
| [<span data-ttu-id="67f95-122"> **\<Usuń >** </span><span class="sxs-lookup"><span data-stu-id="67f95-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="67f95-123">Usuwa ustawienie.</span><span class="sxs-lookup"><span data-stu-id="67f95-123">Removes a setting.</span></span> <span data-ttu-id="67f95-124">Element podrzędny **>\<AppSettings**.</span><span class="sxs-lookup"><span data-stu-id="67f95-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="67f95-125">Wymaga atrybutu **klucza** .</span><span class="sxs-lookup"><span data-stu-id="67f95-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="67f95-126">\<appSettings > element</span><span class="sxs-lookup"><span data-stu-id="67f95-126">\<appSettings> element</span></span>

<span data-ttu-id="67f95-127">Ten element zawiera **\<dodaj >** , **\<wyczyść >** i **\<Usuń Tagi >** w celu kontrolowania ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67f95-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="67f95-128">Definiuje opcjonalny atrybut dla **pliku**.</span><span class="sxs-lookup"><span data-stu-id="67f95-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="67f95-129">\<dodać elementu ></span><span class="sxs-lookup"><span data-stu-id="67f95-129">\<add> element</span></span>

<span data-ttu-id="67f95-130">Dodaje niestandardowe ustawienie aplikacji jako parę nazwa/wartość do kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67f95-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="67f95-131">Definiuje atrybuty **klucza** i **wartości**.</span><span class="sxs-lookup"><span data-stu-id="67f95-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="67f95-132">\<Wyczyść > elementu</span><span class="sxs-lookup"><span data-stu-id="67f95-132">\<clear> element</span></span>

<span data-ttu-id="67f95-133">Usuwa wszystkie odwołania do dziedziczonych ustawień aplikacji niestandardowych i zezwala tylko na odwołania, które są dodawane przez **\<dodaj >** elementy po **\<Wyczyść >** elementu.</span><span class="sxs-lookup"><span data-stu-id="67f95-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="67f95-134">Nie definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="67f95-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="67f95-135">\<usunąć elementu ></span><span class="sxs-lookup"><span data-stu-id="67f95-135">\<remove> element</span></span>

<span data-ttu-id="67f95-136">Usuwa odwołanie do dziedziczonego ustawienia aplikacji niestandardowej z kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67f95-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="67f95-137">Definiuje atrybut dla **klucza**.</span><span class="sxs-lookup"><span data-stu-id="67f95-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="67f95-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="67f95-138">Example</span></span>

<span data-ttu-id="67f95-139">W poniższym przykładzie przedstawiono zewnętrzny plik ustawień aplikacji (*Custom. config*) definiujący niestandardowe ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="67f95-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="67f95-140">Poniższy przykład przedstawia plik konfiguracji aplikacji, który używa ustawienia w pliku ustawień zewnętrznych i ustawia własne ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="67f95-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="67f95-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67f95-141">See also</span></span>

- [<span data-ttu-id="67f95-142">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="67f95-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="67f95-143">Architektura ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="67f95-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
