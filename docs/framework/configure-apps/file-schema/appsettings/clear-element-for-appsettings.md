---
title: '&lt;Wyczyść&gt; elementu &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bc52e3149c213925ea64a8421ee65befeea4161e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184221"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="94982-102">\<Wyczyść >, element dla \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="94982-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="94982-103">Czyści ustawień aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="94982-103">Clears custom application settings.</span></span>

<span data-ttu-id="94982-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="94982-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="94982-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="94982-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="94982-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="94982-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="94982-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="94982-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="94982-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="94982-108">Attributes</span></span>

<span data-ttu-id="94982-109">Brak</span><span class="sxs-lookup"><span data-stu-id="94982-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="94982-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="94982-110">Parent element</span></span>

|     | <span data-ttu-id="94982-111">Opis</span><span class="sxs-lookup"><span data-stu-id="94982-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="94982-112">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="94982-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="94982-113">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracyjne aplikacji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="94982-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="94982-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="94982-114">Child elements</span></span>

<span data-ttu-id="94982-115">Brak</span><span class="sxs-lookup"><span data-stu-id="94982-115">None</span></span>

## <a name="example"></a><span data-ttu-id="94982-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="94982-116">Example</span></span>

<span data-ttu-id="94982-117">Jak wyczyścić niestandardowe ustawienia konfiguracji można znaleźć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="94982-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="94982-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94982-118">See also</span></span>

- [<span data-ttu-id="94982-119">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="94982-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
