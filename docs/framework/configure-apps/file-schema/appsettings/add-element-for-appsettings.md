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
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214816"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="f076f-102">\<dodać > elementu \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="f076f-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="f076f-103">Dodaje niestandardowe ustawienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f076f-103">Adds a custom application setting.</span></span>

<span data-ttu-id="f076f-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f076f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f076f-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="f076f-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="f076f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**</span><span class="sxs-lookup"><span data-stu-id="f076f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f076f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f076f-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="f076f-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f076f-108">Attributes</span></span>

|           | <span data-ttu-id="f076f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f076f-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f076f-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="f076f-110">**key**</span></span>   | <span data-ttu-id="f076f-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f076f-111">Required attribute.</span></span><br><br><span data-ttu-id="f076f-112">Określa nazwę klucza do dodania.</span><span class="sxs-lookup"><span data-stu-id="f076f-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="f076f-113">**value**</span><span class="sxs-lookup"><span data-stu-id="f076f-113">**value**</span></span> | <span data-ttu-id="f076f-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f076f-114">Required attribute.</span></span><br><br><span data-ttu-id="f076f-115">Określa wartość klucza do dodania.</span><span class="sxs-lookup"><span data-stu-id="f076f-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f076f-116">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="f076f-116">Parent element</span></span>

|     | <span data-ttu-id="f076f-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f076f-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f076f-118"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="f076f-118">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="f076f-119">Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f076f-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f076f-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f076f-120">Child elements</span></span>

<span data-ttu-id="f076f-121">None</span><span class="sxs-lookup"><span data-stu-id="f076f-121">None</span></span>

## <a name="example"></a><span data-ttu-id="f076f-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f076f-122">Example</span></span>

<span data-ttu-id="f076f-123">Poniższy przykład pokazuje, jak dodać niestandardowe ustawienie konfiguracji dla nazwy aplikacji:</span><span class="sxs-lookup"><span data-stu-id="f076f-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="f076f-124">Poniższy przykład używa elementu `<add>`, aby zdefiniować dwa ustawienia zgodności w aplikacji ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="f076f-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="f076f-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f076f-125">See also</span></span>

- [<span data-ttu-id="f076f-126">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f076f-126">Configuration file schema for the .NET Framework</span></span>](../index.md)
