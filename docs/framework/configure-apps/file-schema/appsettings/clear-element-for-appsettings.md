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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214798"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="7d8c7-102">\<clear>, element dla \<appSettings></span><span class="sxs-lookup"><span data-stu-id="7d8c7-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="7d8c7-103">Czyści niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d8c7-103">Clears custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="7d8c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d8c7-104">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="7d8c7-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d8c7-105">Attributes</span></span>

<span data-ttu-id="7d8c7-106">Brak</span><span class="sxs-lookup"><span data-stu-id="7d8c7-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="7d8c7-107">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="7d8c7-107">Parent element</span></span>

|     | <span data-ttu-id="7d8c7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="7d8c7-108">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="7d8c7-109">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d8c7-109">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7d8c7-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d8c7-110">Child elements</span></span>

<span data-ttu-id="7d8c7-111">Brak</span><span class="sxs-lookup"><span data-stu-id="7d8c7-111">None</span></span>

## <a name="example"></a><span data-ttu-id="7d8c7-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d8c7-112">Example</span></span>

<span data-ttu-id="7d8c7-113">Poniższy przykład pokazuje, jak wyczyścić niestandardowe ustawienia konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="7d8c7-113">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="7d8c7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d8c7-114">See also</span></span>

- [<span data-ttu-id="7d8c7-115">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7d8c7-115">Configuration file schema for the .NET Framework</span></span>](../index.md)
