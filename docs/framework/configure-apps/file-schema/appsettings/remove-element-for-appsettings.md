---
title: <remove>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0695d5638589d1afe48553fe32b8d070e3938353
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119200"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="a0a9a-102">\<usunąć > elementu \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="a0a9a-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="a0a9a-103">Usuwa niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0a9a-103">Removes custom application settings.</span></span>

<span data-ttu-id="a0a9a-104">[ **\<> konfiguracji**](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a0a9a-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="a0a9a-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a0a9a-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="a0a9a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<usuń >**</span><span class="sxs-lookup"><span data-stu-id="a0a9a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a0a9a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0a9a-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="a0a9a-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a0a9a-108">Attribute</span></span>

|         | <span data-ttu-id="a0a9a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a0a9a-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="a0a9a-110">**głównych**</span><span class="sxs-lookup"><span data-stu-id="a0a9a-110">**key**</span></span> | <span data-ttu-id="a0a9a-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a0a9a-111">Required attribute.</span></span><br><br><span data-ttu-id="a0a9a-112">Określa nazwę klucza do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="a0a9a-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="a0a9a-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="a0a9a-113">Parent element</span></span>

|     | <span data-ttu-id="a0a9a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a0a9a-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a0a9a-115"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="a0a9a-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="a0a9a-116">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0a9a-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a0a9a-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a0a9a-117">Child elements</span></span>

<span data-ttu-id="a0a9a-118">Brak</span><span class="sxs-lookup"><span data-stu-id="a0a9a-118">None</span></span>

## <a name="example"></a><span data-ttu-id="a0a9a-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0a9a-119">Example</span></span>

<span data-ttu-id="a0a9a-120">Poniższy przykład przedstawia sposób usuwania niestandardowego ustawienia konfiguracji dla `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="a0a9a-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="a0a9a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0a9a-121">See also</span></span>

- [<span data-ttu-id="a0a9a-122">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a0a9a-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
