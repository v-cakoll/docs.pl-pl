---
title: <clear>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 266d32ccb8b322f0472e0f552f9c0fc877c9a78e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214798"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="a4412-102">\<Wyczyść > elementu \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="a4412-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="a4412-103">Czyści niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4412-103">Clears custom application settings.</span></span>

<span data-ttu-id="a4412-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4412-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a4412-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="a4412-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="a4412-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="a4412-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a4412-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4412-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="a4412-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a4412-108">Attributes</span></span>

<span data-ttu-id="a4412-109">None</span><span class="sxs-lookup"><span data-stu-id="a4412-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="a4412-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="a4412-110">Parent element</span></span>

|     | <span data-ttu-id="a4412-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a4412-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a4412-112"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="a4412-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="a4412-113">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4412-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a4412-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a4412-114">Child elements</span></span>

<span data-ttu-id="a4412-115">None</span><span class="sxs-lookup"><span data-stu-id="a4412-115">None</span></span>

## <a name="example"></a><span data-ttu-id="a4412-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4412-116">Example</span></span>

<span data-ttu-id="a4412-117">Poniższy przykład pokazuje, jak wyczyścić niestandardowe ustawienia konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="a4412-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="a4412-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4412-118">See also</span></span>

- [<span data-ttu-id="a4412-119">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a4412-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
