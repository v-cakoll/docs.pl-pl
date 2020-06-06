---
title: <remove>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215494"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="6f941-102">\<remove>, element dla \<appSettings></span><span class="sxs-lookup"><span data-stu-id="6f941-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="6f941-103">Usuwa niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f941-103">Removes custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="6f941-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f941-104">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="6f941-105">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6f941-105">Attribute</span></span>

|         | <span data-ttu-id="6f941-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6f941-106">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="6f941-107">**głównych**</span><span class="sxs-lookup"><span data-stu-id="6f941-107">**key**</span></span> | <span data-ttu-id="6f941-108">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6f941-108">Required attribute.</span></span><br><br><span data-ttu-id="6f941-109">Określa nazwę klucza do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="6f941-109">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="6f941-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="6f941-110">Parent element</span></span>

|     | <span data-ttu-id="6f941-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6f941-111">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="6f941-112">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f941-112">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6f941-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6f941-113">Child elements</span></span>

<span data-ttu-id="6f941-114">Brak</span><span class="sxs-lookup"><span data-stu-id="6f941-114">None</span></span>

## <a name="example"></a><span data-ttu-id="6f941-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f941-115">Example</span></span>

<span data-ttu-id="6f941-116">Poniższy przykład pokazuje, jak usunąć niestandardowe ustawienie konfiguracji dla `ApplicationName` :</span><span class="sxs-lookup"><span data-stu-id="6f941-116">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="6f941-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f941-117">See also</span></span>

- [<span data-ttu-id="6f941-118">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f941-118">Configuration file schema for the .NET Framework</span></span>](../index.md)
