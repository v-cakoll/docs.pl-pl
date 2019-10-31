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
ms.openlocfilehash: 3b931b76aa09b3f62fbd799990975268af4f7293
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119217"
---
# <a name="app-settings-schema"></a><span data-ttu-id="5033d-102">Schemat ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="5033d-102">App Settings schema</span></span>

<span data-ttu-id="5033d-103">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5033d-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="5033d-104">[ **\<> konfiguracji**](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5033d-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="5033d-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5033d-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="5033d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dodaj >** ](add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="5033d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="5033d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wyczyść >** ](clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="5033d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="5033d-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Usuń >** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="5033d-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="5033d-109">Element</span><span class="sxs-lookup"><span data-stu-id="5033d-109">Element</span></span> | <span data-ttu-id="5033d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5033d-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="5033d-111"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="5033d-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="5033d-112">Zawiera **\<dodaj >** , **\<wyczyść >** i **\<Usuń Tagi >** w celu kontrolowania ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5033d-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="5033d-113">Ma opcjonalny atrybut **pliku** .</span><span class="sxs-lookup"><span data-stu-id="5033d-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="5033d-114"> **\<Dodaj >** </span><span class="sxs-lookup"><span data-stu-id="5033d-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="5033d-115">Definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="5033d-115">Defines a setting.</span></span> <span data-ttu-id="5033d-116">Element podrzędny **\<AppSettings**.</span><span class="sxs-lookup"><span data-stu-id="5033d-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="5033d-117">Wymaga atrybutów **klucza** i **wartości** .</span><span class="sxs-lookup"><span data-stu-id="5033d-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="5033d-118"> **\<Wyczyść >** </span><span class="sxs-lookup"><span data-stu-id="5033d-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="5033d-119">Czyści wszystkie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5033d-119">Clears all settings.</span></span> <span data-ttu-id="5033d-120">Element podrzędny **\<AppSettings**.</span><span class="sxs-lookup"><span data-stu-id="5033d-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="5033d-121">Nie ma atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5033d-121">Has no attributes.</span></span> |
| [<span data-ttu-id="5033d-122"> **\<Usuń >** </span><span class="sxs-lookup"><span data-stu-id="5033d-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="5033d-123">Usuwa ustawienie.</span><span class="sxs-lookup"><span data-stu-id="5033d-123">Removes a setting.</span></span> <span data-ttu-id="5033d-124">Element podrzędny **\<AppSettings**.</span><span class="sxs-lookup"><span data-stu-id="5033d-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="5033d-125">Wymaga atrybutu **klucza** .</span><span class="sxs-lookup"><span data-stu-id="5033d-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="5033d-126">\<appSettings > element</span><span class="sxs-lookup"><span data-stu-id="5033d-126">\<appSettings> element</span></span>

<span data-ttu-id="5033d-127">Ten element zawiera **\<dodaj >** , **\<wyczyść >** i **\<Usuń Tagi >** w celu kontrolowania ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5033d-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="5033d-128">Definiuje opcjonalny atrybut dla **pliku**.</span><span class="sxs-lookup"><span data-stu-id="5033d-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="5033d-129">\<dodać elementu ></span><span class="sxs-lookup"><span data-stu-id="5033d-129">\<add> element</span></span>

<span data-ttu-id="5033d-130">Dodaje niestandardowe ustawienie aplikacji jako parę nazwa/wartość do kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5033d-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="5033d-131">Definiuje atrybuty **klucza** i **wartości**.</span><span class="sxs-lookup"><span data-stu-id="5033d-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="5033d-132">\<Wyczyść > elementu</span><span class="sxs-lookup"><span data-stu-id="5033d-132">\<clear> element</span></span>

<span data-ttu-id="5033d-133">Usuwa wszystkie odwołania do dziedziczonych ustawień aplikacji niestandardowych i zezwala tylko na odwołania, które są dodawane przez **\<dodaj >** elementy po **\<Wyczyść >** elementu.</span><span class="sxs-lookup"><span data-stu-id="5033d-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="5033d-134">Nie definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5033d-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="5033d-135">\<usunąć elementu ></span><span class="sxs-lookup"><span data-stu-id="5033d-135">\<remove> element</span></span>

<span data-ttu-id="5033d-136">Usuwa odwołanie do dziedziczonego ustawienia aplikacji niestandardowej z kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5033d-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="5033d-137">Definiuje atrybut dla **klucza**.</span><span class="sxs-lookup"><span data-stu-id="5033d-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="5033d-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="5033d-138">Example</span></span>

<span data-ttu-id="5033d-139">W poniższym przykładzie przedstawiono zewnętrzny plik ustawień aplikacji (*Custom. config*) definiujący niestandardowe ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="5033d-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="5033d-140">Poniższy przykład przedstawia plik konfiguracji aplikacji, który używa ustawienia w pliku ustawień zewnętrznych i ustawia własne ustawienie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="5033d-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5033d-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5033d-141">See also</span></span>

- [<span data-ttu-id="5033d-142">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="5033d-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="5033d-143">Architektura ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="5033d-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
