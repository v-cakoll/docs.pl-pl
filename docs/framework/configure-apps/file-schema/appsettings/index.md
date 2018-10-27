---
title: Schemat ustawień aplikacji
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9bf2568c8c18f8f6d18c445e802cc72df18fb8c4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191151"
---
# <a name="app-settings-schema"></a><span data-ttu-id="e2aef-102">Schemat ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="e2aef-102">App Settings schema</span></span>

<span data-ttu-id="e2aef-103">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2aef-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="e2aef-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e2aef-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="e2aef-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="e2aef-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="e2aef-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Dodaj >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="e2aef-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="e2aef-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Wyczyść >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="e2aef-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="e2aef-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Usuń >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="e2aef-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="e2aef-109">Element</span><span class="sxs-lookup"><span data-stu-id="e2aef-109">Element</span></span> | <span data-ttu-id="e2aef-110">Opis</span><span class="sxs-lookup"><span data-stu-id="e2aef-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="e2aef-111">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="e2aef-111">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="e2aef-112">Zawiera  **\<Dodaj >**,  **\<Wyczyść >**, i  **\<Usuń >** tagów, aby kontrolować ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2aef-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="e2aef-113">Ma opcjonalny **pliku** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e2aef-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="e2aef-114">**\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="e2aef-114">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="e2aef-115">Definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="e2aef-115">Defines a setting.</span></span> <span data-ttu-id="e2aef-116">Element podrzędny elementu  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="e2aef-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="e2aef-117">Wymaga **klucz** i **wartość** atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e2aef-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="e2aef-118">**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="e2aef-118">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="e2aef-119">Czyści wszystkie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e2aef-119">Clears all settings.</span></span> <span data-ttu-id="e2aef-120">Element podrzędny elementu  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="e2aef-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="e2aef-121">nie ma żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e2aef-121">Has no attributes.</span></span> |
| [<span data-ttu-id="e2aef-122">**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="e2aef-122">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="e2aef-123">Usuwa ustawienie.</span><span class="sxs-lookup"><span data-stu-id="e2aef-123">Removes a setting.</span></span> <span data-ttu-id="e2aef-124">Element podrzędny elementu  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="e2aef-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="e2aef-125">Wymaga **klucz** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e2aef-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="e2aef-126">\<appSettings > element</span><span class="sxs-lookup"><span data-stu-id="e2aef-126">\<appSettings> element</span></span>

<span data-ttu-id="e2aef-127">Ten element zawiera  **\<Dodaj >**,  **\<Wyczyść >**, i  **\<Usuń >** tagów, aby kontrolować ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2aef-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="e2aef-128">Definiuje on opcjonalny atrybut **pliku**.</span><span class="sxs-lookup"><span data-stu-id="e2aef-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="e2aef-129">\<Dodaj > element</span><span class="sxs-lookup"><span data-stu-id="e2aef-129">\<add> element</span></span>

<span data-ttu-id="e2aef-130">Ustawienia niestandardowych aplikacji jako pary nazwa/wartość są dodawane do kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2aef-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="e2aef-131">Definiuje atrybuty **klucz** i **wartość**.</span><span class="sxs-lookup"><span data-stu-id="e2aef-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="e2aef-132">\<Wyczyść > element</span><span class="sxs-lookup"><span data-stu-id="e2aef-132">\<clear> element</span></span>

<span data-ttu-id="e2aef-133">Usuwa wszystkie odwołania do ustawień dziedziczonych niestandardowych aplikacji i umożliwia tylko odwołań, które są dodawane przez  **\<Dodaj >** elementy następujące  **\<Wyczyść >** element.</span><span class="sxs-lookup"><span data-stu-id="e2aef-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="e2aef-134">Definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e2aef-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="e2aef-135">\<Usuń > element</span><span class="sxs-lookup"><span data-stu-id="e2aef-135">\<remove> element</span></span>

<span data-ttu-id="e2aef-136">Usuwa odwołanie do ustawienia dziedziczone niestandardową aplikację z kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2aef-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="e2aef-137">Definiuje atrybut **klucz**.</span><span class="sxs-lookup"><span data-stu-id="e2aef-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="e2aef-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2aef-138">Example</span></span>

<span data-ttu-id="e2aef-139">Poniższy przykład pokazuje plik ustawień aplikacji zewnętrznej (*custom.config*) definiuje ustawienia aplikacji niestandardowej:</span><span class="sxs-lookup"><span data-stu-id="e2aef-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="e2aef-140">Poniższy przykład przedstawia plik konfiguracji aplikacji, który wykorzystuje ustawienie w pliku ustawień zewnętrznych, a następnie ustawia ustawienie aplikacji własnych:</span><span class="sxs-lookup"><span data-stu-id="e2aef-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e2aef-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2aef-141">See also</span></span>

- [<span data-ttu-id="e2aef-142">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="e2aef-142">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)   
- [<span data-ttu-id="e2aef-143">Architektura ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="e2aef-143">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
