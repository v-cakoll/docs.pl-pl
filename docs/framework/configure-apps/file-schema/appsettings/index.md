---
title: "Schemat ustawień aplikacji"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d51d06895e61be60bbe9153eacb2028cb32a1fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="app-settings-schema"></a><span data-ttu-id="f7cb8-102">Schemat ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="f7cb8-102">App Settings schema</span></span>

<span data-ttu-id="f7cb8-103">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki plików, adresy URL usługi XML sieci Web lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="f7cb8-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f7cb8-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="f7cb8-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f7cb8-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="f7cb8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Dodaj >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="f7cb8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="f7cb8-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Wyczyść >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="f7cb8-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="f7cb8-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Usuń >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="f7cb8-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="f7cb8-109">Element</span><span class="sxs-lookup"><span data-stu-id="f7cb8-109">Element</span></span> | <span data-ttu-id="f7cb8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f7cb8-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="f7cb8-111">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="f7cb8-111">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="f7cb8-112">Zawiera  **\<Dodaj >**,  **\<Wyczyść >**, i  **\<Usuń >** znaczniki, aby kontrolować ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f7cb8-113">Ma opcjonalny **pliku** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="f7cb8-114">**\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="f7cb8-114">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="f7cb8-115">Definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-115">Defines a setting.</span></span> <span data-ttu-id="f7cb8-116">Element podrzędny  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f7cb8-117">Wymaga **klucza** i **wartość** atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="f7cb8-118">**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="f7cb8-118">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="f7cb8-119">Czyści wszystkie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-119">Clears all settings.</span></span> <span data-ttu-id="f7cb8-120">Element podrzędny  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f7cb8-121">Nie ma żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-121">Has no attributes.</span></span> |
| [<span data-ttu-id="f7cb8-122">**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="f7cb8-122">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="f7cb8-123">Usuwa ustawienie.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-123">Removes a setting.</span></span> <span data-ttu-id="f7cb8-124">Element podrzędny  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f7cb8-125">Wymaga **klucza** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="f7cb8-126">\<appSettings > — element</span><span class="sxs-lookup"><span data-stu-id="f7cb8-126">\<appSettings> element</span></span>

<span data-ttu-id="f7cb8-127">Ten element zawiera  **\<Dodaj >**,  **\<Wyczyść >**, i  **\<Usuń >** znaczniki, aby kontrolować ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f7cb8-128">Definiuje atrybut opcjonalny **pliku**.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="f7cb8-129">\<Dodaj > — element</span><span class="sxs-lookup"><span data-stu-id="f7cb8-129">\<add> element</span></span>

<span data-ttu-id="f7cb8-130">Dodaje ustawienie niestandardowej aplikacji jako pary nazwa/wartość w kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="f7cb8-131">Definiuje atrybuty **klucza** i **wartość**.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="f7cb8-132">\<Wyczyść > — element</span><span class="sxs-lookup"><span data-stu-id="f7cb8-132">\<clear> element</span></span>

<span data-ttu-id="f7cb8-133">Usuwa wszystkie odwołania do ustawienia dziedziczony niestandardową aplikację i umożliwia odwołań, które są dodawane przez  **\<Dodaj >** elementy następujące  **\<Wyczyść >** element.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="f7cb8-134">Definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="f7cb8-135">\<Usuń > — element</span><span class="sxs-lookup"><span data-stu-id="f7cb8-135">\<remove> element</span></span>

<span data-ttu-id="f7cb8-136">Usuwa odwołanie do ustawienia dziedziczony niestandardową aplikację z kolekcji ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="f7cb8-137">Definiuje atrybut **klucza**.</span><span class="sxs-lookup"><span data-stu-id="f7cb8-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="f7cb8-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7cb8-138">Example</span></span>

<span data-ttu-id="f7cb8-139">W poniższym przykładzie przedstawiono plik ustawień zewnętrznej aplikacji (*custom.config*) definiuje ustawienia aplikacji niestandardowej:</span><span class="sxs-lookup"><span data-stu-id="f7cb8-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="f7cb8-140">W poniższym przykładzie przedstawiono plik konfiguracji aplikacji, który wykorzystuje ustawienia w pliku ustawień zewnętrznych, a następnie ustawia ustawienie aplikacji z własnych:</span><span class="sxs-lookup"><span data-stu-id="f7cb8-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f7cb8-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7cb8-141">See also</span></span>

<span data-ttu-id="f7cb8-142">[Przegląd ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="f7cb8-142">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="f7cb8-143">Architektura ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="f7cb8-143">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
