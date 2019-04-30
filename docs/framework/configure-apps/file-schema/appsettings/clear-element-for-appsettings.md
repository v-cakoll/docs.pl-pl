---
title: <clear>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 0b6a48d1fdab3cbccf40aaa77731a658f533eeba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705405"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="9f0c7-102">\<clear> element for \<appSettings></span><span class="sxs-lookup"><span data-stu-id="9f0c7-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="9f0c7-103">Czyści ustawień aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="9f0c7-103">Clears custom application settings.</span></span>

<span data-ttu-id="9f0c7-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9f0c7-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="9f0c7-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="9f0c7-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="9f0c7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="9f0c7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9f0c7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f0c7-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="9f0c7-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9f0c7-108">Attributes</span></span>

<span data-ttu-id="9f0c7-109">Brak</span><span class="sxs-lookup"><span data-stu-id="9f0c7-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="9f0c7-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="9f0c7-110">Parent element</span></span>

|     | <span data-ttu-id="9f0c7-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9f0c7-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9f0c7-112">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="9f0c7-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="9f0c7-113">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracyjne aplikacji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="9f0c7-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9f0c7-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9f0c7-114">Child elements</span></span>

<span data-ttu-id="9f0c7-115">Brak</span><span class="sxs-lookup"><span data-stu-id="9f0c7-115">None</span></span>

## <a name="example"></a><span data-ttu-id="9f0c7-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f0c7-116">Example</span></span>

<span data-ttu-id="9f0c7-117">Jak wyczyścić niestandardowe ustawienia konfiguracji można znaleźć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9f0c7-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="9f0c7-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f0c7-118">See also</span></span>

- [<span data-ttu-id="9f0c7-119">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9f0c7-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
