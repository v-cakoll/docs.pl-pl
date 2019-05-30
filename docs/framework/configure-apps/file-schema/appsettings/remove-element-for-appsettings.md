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
ms.openlocfilehash: 62913face910ae9500aa5e6f2f443db67ffd4240
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301280"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="3ff57-102">\<remove> element for \<appSettings></span><span class="sxs-lookup"><span data-stu-id="3ff57-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="3ff57-103">Usunięcie ustawień aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="3ff57-103">Removes custom application settings.</span></span>

<span data-ttu-id="3ff57-104">[ **\<Konfiguracja >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3ff57-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="3ff57-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3ff57-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="3ff57-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="3ff57-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3ff57-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ff57-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="3ff57-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3ff57-108">Attribute</span></span>

|         | <span data-ttu-id="3ff57-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3ff57-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="3ff57-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="3ff57-110">**key**</span></span> | <span data-ttu-id="3ff57-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3ff57-111">Required attribute.</span></span><br><br><span data-ttu-id="3ff57-112">Określa nazwę klucza do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="3ff57-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="3ff57-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="3ff57-113">Parent element</span></span>

|     | <span data-ttu-id="3ff57-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3ff57-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3ff57-115"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="3ff57-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="3ff57-116">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3ff57-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3ff57-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ff57-117">Child elements</span></span>

<span data-ttu-id="3ff57-118">Brak</span><span class="sxs-lookup"><span data-stu-id="3ff57-118">None</span></span>

## <a name="example"></a><span data-ttu-id="3ff57-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ff57-119">Example</span></span>

<span data-ttu-id="3ff57-120">Poniższy przykład pokazuje, jak usunąć ustawienia konfiguracji niestandardowej dla `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="3ff57-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="3ff57-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ff57-121">See also</span></span>

- [<span data-ttu-id="3ff57-122">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ff57-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
