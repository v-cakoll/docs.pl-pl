---
title: <clear>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d321f3169344e9aa40d65b1722a533549de5315a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088738"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="1b692-102">\<Wyczyść > elementu \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="1b692-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="1b692-103">Czyści niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b692-103">Clears custom application settings.</span></span>

<span data-ttu-id="1b692-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1b692-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1b692-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="1b692-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="1b692-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="1b692-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1b692-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b692-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="1b692-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1b692-108">Attributes</span></span>

<span data-ttu-id="1b692-109">Brak</span><span class="sxs-lookup"><span data-stu-id="1b692-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="1b692-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="1b692-110">Parent element</span></span>

|     | <span data-ttu-id="1b692-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1b692-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1b692-112"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="1b692-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="1b692-113">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b692-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="1b692-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1b692-114">Child elements</span></span>

<span data-ttu-id="1b692-115">Brak</span><span class="sxs-lookup"><span data-stu-id="1b692-115">None</span></span>

## <a name="example"></a><span data-ttu-id="1b692-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b692-116">Example</span></span>

<span data-ttu-id="1b692-117">Poniższy przykład pokazuje, jak wyczyścić niestandardowe ustawienia konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="1b692-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="1b692-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b692-118">See also</span></span>

- [<span data-ttu-id="1b692-119">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1b692-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
