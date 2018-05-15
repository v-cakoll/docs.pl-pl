---
title: '&lt;Usuń&gt; elementu &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 21fedf064596979dbfb4190d9956da616295af3c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="65ec3-102">\<Usuń > elementu \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="65ec3-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="65ec3-103">Usuwa ustawień niestandardowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65ec3-103">Removes custom application settings.</span></span>

<span data-ttu-id="65ec3-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="65ec3-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="65ec3-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="65ec3-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="65ec3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="65ec3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="65ec3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="65ec3-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="65ec3-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="65ec3-108">Attribute</span></span>

|         | <span data-ttu-id="65ec3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="65ec3-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="65ec3-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="65ec3-110">**key**</span></span> | <span data-ttu-id="65ec3-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="65ec3-111">Required attribute.</span></span><br><br><span data-ttu-id="65ec3-112">Określa nazwę klucz do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="65ec3-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="65ec3-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="65ec3-113">Parent element</span></span>

|     | <span data-ttu-id="65ec3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="65ec3-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="65ec3-115">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="65ec3-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="65ec3-116">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki plików, adresy URL usługi XML sieci Web lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65ec3-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="65ec3-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="65ec3-117">Child elements</span></span>

<span data-ttu-id="65ec3-118">Brak</span><span class="sxs-lookup"><span data-stu-id="65ec3-118">None</span></span>

## <a name="example"></a><span data-ttu-id="65ec3-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="65ec3-119">Example</span></span>

<span data-ttu-id="65ec3-120">Poniższy przykład przedstawia sposób usuwania ustawienia konfiguracji niestandardowej dla `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="65ec3-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="65ec3-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65ec3-121">See also</span></span>

[<span data-ttu-id="65ec3-122">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="65ec3-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
