---
title: <clear>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 5d5da531bff3a0e9e198ba9b5ab6cf2b52bf36b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921317"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="0ef21-102">\<Wyczyść > element dla \<AppSettings ></span><span class="sxs-lookup"><span data-stu-id="0ef21-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="0ef21-103">Czyści niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ef21-103">Clears custom application settings.</span></span>

<span data-ttu-id="0ef21-104">[ **\<> konfiguracji**](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0ef21-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="0ef21-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="0ef21-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="0ef21-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="0ef21-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0ef21-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ef21-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="0ef21-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0ef21-108">Attributes</span></span>

<span data-ttu-id="0ef21-109">Brak</span><span class="sxs-lookup"><span data-stu-id="0ef21-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="0ef21-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="0ef21-110">Parent element</span></span>

|     | <span data-ttu-id="0ef21-111">Opis</span><span class="sxs-lookup"><span data-stu-id="0ef21-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0ef21-112"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="0ef21-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="0ef21-113">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ef21-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0ef21-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0ef21-114">Child elements</span></span>

<span data-ttu-id="0ef21-115">Brak</span><span class="sxs-lookup"><span data-stu-id="0ef21-115">None</span></span>

## <a name="example"></a><span data-ttu-id="0ef21-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ef21-116">Example</span></span>

<span data-ttu-id="0ef21-117">Poniższy przykład pokazuje, jak wyczyścić niestandardowe ustawienia konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="0ef21-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="0ef21-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ef21-118">See also</span></span>

- [<span data-ttu-id="0ef21-119">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0ef21-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
