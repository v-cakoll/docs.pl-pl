---
title: <remove>, element dla <appSettings>
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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705392"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="0a7f5-102">\<remove> element for \<appSettings></span><span class="sxs-lookup"><span data-stu-id="0a7f5-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="0a7f5-103">Usunięcie ustawień aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="0a7f5-103">Removes custom application settings.</span></span>

<span data-ttu-id="0a7f5-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0a7f5-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="0a7f5-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="0a7f5-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="0a7f5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="0a7f5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0a7f5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a7f5-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="0a7f5-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0a7f5-108">Attribute</span></span>

|         | <span data-ttu-id="0a7f5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0a7f5-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="0a7f5-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="0a7f5-110">**key**</span></span> | <span data-ttu-id="0a7f5-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0a7f5-111">Required attribute.</span></span><br><br><span data-ttu-id="0a7f5-112">Określa nazwę klucza do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="0a7f5-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="0a7f5-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="0a7f5-113">Parent element</span></span>

|     | <span data-ttu-id="0a7f5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0a7f5-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0a7f5-115">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="0a7f5-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="0a7f5-116">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a7f5-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0a7f5-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0a7f5-117">Child elements</span></span>

<span data-ttu-id="0a7f5-118">Brak</span><span class="sxs-lookup"><span data-stu-id="0a7f5-118">None</span></span>

## <a name="example"></a><span data-ttu-id="0a7f5-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a7f5-119">Example</span></span>

<span data-ttu-id="0a7f5-120">Poniższy przykład pokazuje, jak usunąć ustawienia konfiguracji niestandardowej dla `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="0a7f5-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="0a7f5-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a7f5-121">See also</span></span>

- [<span data-ttu-id="0a7f5-122">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0a7f5-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
