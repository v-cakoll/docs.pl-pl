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
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215494"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="c412b-102">\<usunąć > elementu \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="c412b-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="c412b-103">Usuwa niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c412b-103">Removes custom application settings.</span></span>

<span data-ttu-id="c412b-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c412b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c412b-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="c412b-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="c412b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<usuń >**</span><span class="sxs-lookup"><span data-stu-id="c412b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c412b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c412b-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="c412b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c412b-108">Attribute</span></span>

|         | <span data-ttu-id="c412b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c412b-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="c412b-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="c412b-110">**key**</span></span> | <span data-ttu-id="c412b-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c412b-111">Required attribute.</span></span><br><br><span data-ttu-id="c412b-112">Określa nazwę klucza do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="c412b-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="c412b-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="c412b-113">Parent element</span></span>

|     | <span data-ttu-id="c412b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c412b-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c412b-115"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="c412b-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="c412b-116">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c412b-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c412b-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c412b-117">Child elements</span></span>

<span data-ttu-id="c412b-118">None</span><span class="sxs-lookup"><span data-stu-id="c412b-118">None</span></span>

## <a name="example"></a><span data-ttu-id="c412b-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="c412b-119">Example</span></span>

<span data-ttu-id="c412b-120">Poniższy przykład przedstawia sposób usuwania niestandardowego ustawienia konfiguracji dla `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="c412b-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="c412b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c412b-121">See also</span></span>

- [<span data-ttu-id="c412b-122">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c412b-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
