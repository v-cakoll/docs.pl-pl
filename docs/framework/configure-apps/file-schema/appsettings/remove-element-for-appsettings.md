---
title: "&lt;Usuń&gt; elementu &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e803561ef20bb17ed7c637eb487027466b65077
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="046d6-102">\<Usuń > elementu \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="046d6-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="046d6-103">Usuwa ustawień niestandardowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="046d6-103">Removes custom application settings.</span></span>

<span data-ttu-id="046d6-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="046d6-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="046d6-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="046d6-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="046d6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="046d6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="046d6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="046d6-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="046d6-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="046d6-108">Attribute</span></span>

|         | <span data-ttu-id="046d6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="046d6-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="046d6-110">**klucz**</span><span class="sxs-lookup"><span data-stu-id="046d6-110">**key**</span></span> | <span data-ttu-id="046d6-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="046d6-111">Required attribute.</span></span><br><br><span data-ttu-id="046d6-112">Określa nazwę klucz do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="046d6-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="046d6-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="046d6-113">Parent element</span></span>

|     | <span data-ttu-id="046d6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="046d6-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="046d6-115">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="046d6-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="046d6-116">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki plików, adresy URL usługi XML sieci Web lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="046d6-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="046d6-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="046d6-117">Child elements</span></span>

<span data-ttu-id="046d6-118">Brak</span><span class="sxs-lookup"><span data-stu-id="046d6-118">None</span></span>

## <a name="example"></a><span data-ttu-id="046d6-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="046d6-119">Example</span></span>

<span data-ttu-id="046d6-120">Poniższy przykład przedstawia sposób usuwania ustawienia konfiguracji niestandardowej dla `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="046d6-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="046d6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="046d6-121">See also</span></span>

[<span data-ttu-id="046d6-122">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="046d6-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
