---
title: "&lt;Wyczyść&gt; elementu &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ac1e9a86d0c3e1bb1f23b753fd9867effef03ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="5998e-102">\<Wyczyść > elementu \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="5998e-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="5998e-103">Czyści ustawień niestandardowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5998e-103">Clears custom application settings.</span></span>

<span data-ttu-id="5998e-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5998e-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="5998e-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5998e-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="5998e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="5998e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5998e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5998e-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="5998e-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5998e-108">Attributes</span></span>

<span data-ttu-id="5998e-109">Brak</span><span class="sxs-lookup"><span data-stu-id="5998e-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="5998e-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="5998e-110">Parent element</span></span>

|     | <span data-ttu-id="5998e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5998e-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5998e-112">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="5998e-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="5998e-113">Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki plików, adresy URL usługi XML sieci Web lub inne informacje konfiguracyjne aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="5998e-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5998e-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5998e-114">Child elements</span></span>

<span data-ttu-id="5998e-115">Brak</span><span class="sxs-lookup"><span data-stu-id="5998e-115">None</span></span>

## <a name="example"></a><span data-ttu-id="5998e-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="5998e-116">Example</span></span>

<span data-ttu-id="5998e-117">Poniższy przykład przedstawia sposób wyczyść niestandardowych ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="5998e-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="5998e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5998e-118">See also</span></span>

[<span data-ttu-id="5998e-119">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5998e-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
