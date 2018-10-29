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
ms.openlocfilehash: e9b79a8319b320289f43adac5a82ef22fa5e32b0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199698"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="cfc90-102">\<Usuń >, element dla \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="cfc90-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="cfc90-103">Usunięcie ustawień aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="cfc90-103">Removes custom application settings.</span></span>

<span data-ttu-id="cfc90-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="cfc90-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="cfc90-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="cfc90-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="cfc90-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="cfc90-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cfc90-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfc90-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="cfc90-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cfc90-108">Attribute</span></span>

|         | <span data-ttu-id="cfc90-109">Opis</span><span class="sxs-lookup"><span data-stu-id="cfc90-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="cfc90-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="cfc90-110">**key**</span></span> | <span data-ttu-id="cfc90-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="cfc90-111">Required attribute.</span></span><br><br><span data-ttu-id="cfc90-112">Określa nazwę klucza do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="cfc90-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="cfc90-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="cfc90-113">Parent element</span></span>

|     | <span data-ttu-id="cfc90-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cfc90-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cfc90-115">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="cfc90-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="cfc90-116">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfc90-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="cfc90-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cfc90-117">Child elements</span></span>

<span data-ttu-id="cfc90-118">Brak</span><span class="sxs-lookup"><span data-stu-id="cfc90-118">None</span></span>

## <a name="example"></a><span data-ttu-id="cfc90-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfc90-119">Example</span></span>

<span data-ttu-id="cfc90-120">Poniższy przykład pokazuje, jak usunąć ustawienia konfiguracji niestandardowej dla `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="cfc90-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="cfc90-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfc90-121">See also</span></span>

- [<span data-ttu-id="cfc90-122">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cfc90-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
