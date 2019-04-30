---
title: <add>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dde773dc722cf75da9d922ccf28af4bf4a09636c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674873"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="9071c-102">\<Dodaj >, element dla \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="9071c-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="9071c-103">Dodaje ustawienia aplikacji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="9071c-103">Adds a custom application setting.</span></span>

<span data-ttu-id="9071c-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9071c-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="9071c-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="9071c-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="9071c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span><span class="sxs-lookup"><span data-stu-id="9071c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9071c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9071c-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="9071c-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9071c-108">Attributes</span></span>

|           | <span data-ttu-id="9071c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9071c-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="9071c-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="9071c-110">**key**</span></span>   | <span data-ttu-id="9071c-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9071c-111">Required attribute.</span></span><br><br><span data-ttu-id="9071c-112">Określa nazwę klucz do dodania.</span><span class="sxs-lookup"><span data-stu-id="9071c-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="9071c-113">**value**</span><span class="sxs-lookup"><span data-stu-id="9071c-113">**value**</span></span> | <span data-ttu-id="9071c-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9071c-114">Required attribute.</span></span><br><br><span data-ttu-id="9071c-115">Określa wartość klucz do dodania.</span><span class="sxs-lookup"><span data-stu-id="9071c-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="9071c-116">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="9071c-116">Parent element</span></span>

|     | <span data-ttu-id="9071c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9071c-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9071c-118">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="9071c-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="9071c-119">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9071c-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9071c-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9071c-120">Child elements</span></span>

<span data-ttu-id="9071c-121">Brak</span><span class="sxs-lookup"><span data-stu-id="9071c-121">None</span></span>

## <a name="example"></a><span data-ttu-id="9071c-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="9071c-122">Example</span></span>

<span data-ttu-id="9071c-123">Poniższy przykład pokazuje, jak dodać ustawienie Konfiguracja niestandardowa nazwa aplikacji:</span><span class="sxs-lookup"><span data-stu-id="9071c-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="9071c-124">W poniższym przykładzie użyto `<add>` elementu, aby zdefiniować dwa ustawienia zgodności w aplikacji ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="9071c-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="9071c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9071c-125">See also</span></span>

- [<span data-ttu-id="9071c-126">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9071c-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
