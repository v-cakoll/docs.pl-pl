---
title: <add>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: 5c7de79ec626966e71d461dd3865b294a8979db2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214816"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="b9db7-102">\<add>, element dla \<appSettings></span><span class="sxs-lookup"><span data-stu-id="b9db7-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="b9db7-103">Dodaje niestandardowe ustawienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9db7-103">Adds a custom application setting.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="b9db7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9db7-104">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="b9db7-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b9db7-105">Attributes</span></span>

|           | <span data-ttu-id="b9db7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b9db7-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="b9db7-107">**głównych**</span><span class="sxs-lookup"><span data-stu-id="b9db7-107">**key**</span></span>   | <span data-ttu-id="b9db7-108">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b9db7-108">Required attribute.</span></span><br><br><span data-ttu-id="b9db7-109">Określa nazwę klucza do dodania.</span><span class="sxs-lookup"><span data-stu-id="b9db7-109">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="b9db7-110">**wartościami**</span><span class="sxs-lookup"><span data-stu-id="b9db7-110">**value**</span></span> | <span data-ttu-id="b9db7-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b9db7-111">Required attribute.</span></span><br><br><span data-ttu-id="b9db7-112">Określa wartość klucza do dodania.</span><span class="sxs-lookup"><span data-stu-id="b9db7-112">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="b9db7-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="b9db7-113">Parent element</span></span>

|     | <span data-ttu-id="b9db7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b9db7-114">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="b9db7-115">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9db7-115">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b9db7-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b9db7-116">Child elements</span></span>

<span data-ttu-id="b9db7-117">Brak</span><span class="sxs-lookup"><span data-stu-id="b9db7-117">None</span></span>

## <a name="example"></a><span data-ttu-id="b9db7-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9db7-118">Example</span></span>

<span data-ttu-id="b9db7-119">Poniższy przykład pokazuje, jak dodać niestandardowe ustawienie konfiguracji dla nazwy aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b9db7-119">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="b9db7-120">Poniższy przykład używa elementu, `<add>` Aby zdefiniować dwa ustawienia zgodności w aplikacji ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="b9db7-120">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="b9db7-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9db7-121">See also</span></span>

- [<span data-ttu-id="b9db7-122">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b9db7-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
