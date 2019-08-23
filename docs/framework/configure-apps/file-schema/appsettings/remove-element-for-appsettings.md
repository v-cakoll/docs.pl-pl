---
title: <remove>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 121b1c4b124ba07ff3bd312fd3832d3da592f486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921279"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="39e65-102">\<Usuń element > dla \<AppSettings ></span><span class="sxs-lookup"><span data-stu-id="39e65-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="39e65-103">Usuwa niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="39e65-103">Removes custom application settings.</span></span>

<span data-ttu-id="39e65-104">[ **\<> konfiguracji**](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="39e65-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="39e65-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="39e65-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="39e65-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="39e65-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="39e65-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="39e65-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="39e65-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="39e65-108">Attribute</span></span>

|         | <span data-ttu-id="39e65-109">Opis</span><span class="sxs-lookup"><span data-stu-id="39e65-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="39e65-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="39e65-110">**key**</span></span> | <span data-ttu-id="39e65-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="39e65-111">Required attribute.</span></span><br><br><span data-ttu-id="39e65-112">Określa nazwę klucza do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="39e65-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="39e65-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="39e65-113">Parent element</span></span>

|     | <span data-ttu-id="39e65-114">Opis</span><span class="sxs-lookup"><span data-stu-id="39e65-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="39e65-115"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="39e65-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="39e65-116">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="39e65-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="39e65-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39e65-117">Child elements</span></span>

<span data-ttu-id="39e65-118">Brak</span><span class="sxs-lookup"><span data-stu-id="39e65-118">None</span></span>

## <a name="example"></a><span data-ttu-id="39e65-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="39e65-119">Example</span></span>

<span data-ttu-id="39e65-120">Poniższy przykład pokazuje, jak usunąć niestandardowe ustawienie konfiguracji dla `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="39e65-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="39e65-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39e65-121">See also</span></span>

- [<span data-ttu-id="39e65-122">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="39e65-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
