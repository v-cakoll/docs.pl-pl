---
title: <remove> — element do <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: cf9a34e47b70aaff12b29b9c5cf944d5bb15fee9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258724"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="749b8-102">\<remove> element for \<appSettings></span><span class="sxs-lookup"><span data-stu-id="749b8-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="749b8-103">Usunięcie ustawień aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="749b8-103">Removes custom application settings.</span></span>

<span data-ttu-id="749b8-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="749b8-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="749b8-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="749b8-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="749b8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="749b8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="749b8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="749b8-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="749b8-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="749b8-108">Attribute</span></span>

|         | <span data-ttu-id="749b8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="749b8-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="749b8-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="749b8-110">**key**</span></span> | <span data-ttu-id="749b8-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="749b8-111">Required attribute.</span></span><br><br><span data-ttu-id="749b8-112">Określa nazwę klucza do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="749b8-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="749b8-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="749b8-113">Parent element</span></span>

|     | <span data-ttu-id="749b8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="749b8-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="749b8-115">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="749b8-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="749b8-116">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="749b8-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="749b8-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="749b8-117">Child elements</span></span>

<span data-ttu-id="749b8-118">Brak</span><span class="sxs-lookup"><span data-stu-id="749b8-118">None</span></span>

## <a name="example"></a><span data-ttu-id="749b8-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="749b8-119">Example</span></span>

<span data-ttu-id="749b8-120">Poniższy przykład pokazuje, jak usunąć ustawienia konfiguracji niestandardowej dla `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="749b8-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="749b8-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="749b8-121">See also</span></span>

- [<span data-ttu-id="749b8-122">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="749b8-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
