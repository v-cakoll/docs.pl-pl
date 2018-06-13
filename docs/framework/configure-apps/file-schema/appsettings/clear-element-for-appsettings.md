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
ms.openlocfilehash: 525818309ddc142fdb3ad65ce841ea58c1d635a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350669"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="6c967-102">\<Wyczyść > elementu \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="6c967-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="6c967-103">Czyści ustawień niestandardowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6c967-103">Clears custom application settings.</span></span>

<span data-ttu-id="6c967-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6c967-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="6c967-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="6c967-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="6c967-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="6c967-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6c967-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c967-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="6c967-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6c967-108">Attributes</span></span>

<span data-ttu-id="6c967-109">Brak</span><span class="sxs-lookup"><span data-stu-id="6c967-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="6c967-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="6c967-110">Parent element</span></span>

|     | <span data-ttu-id="6c967-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6c967-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6c967-112">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="6c967-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="6c967-113">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki plików, adresy URL usługi XML sieci Web lub inne informacje konfiguracyjne aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="6c967-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6c967-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6c967-114">Child elements</span></span>

<span data-ttu-id="6c967-115">Brak</span><span class="sxs-lookup"><span data-stu-id="6c967-115">None</span></span>

## <a name="example"></a><span data-ttu-id="6c967-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c967-116">Example</span></span>

<span data-ttu-id="6c967-117">Poniższy przykład przedstawia sposób wyczyść niestandardowych ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="6c967-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="6c967-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c967-118">See also</span></span>

[<span data-ttu-id="6c967-119">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6c967-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
