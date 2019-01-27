---
title: '&lt;assemblyBinding&gt; elementu &lt;konfiguracji&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 64985d4ed2c6a82c54a7623df4b13d7ec54bff33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599351"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="99933-102">\<assemblybinding — >, element dla \<konfiguracji ></span><span class="sxs-lookup"><span data-stu-id="99933-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="99933-103">Określa politykę powiązania zestawu na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="99933-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="99933-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="99933-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="99933-105">&nbsp;&nbsp;**\<assemblybinding — >**</span><span class="sxs-lookup"><span data-stu-id="99933-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="99933-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="99933-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="99933-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="99933-107">Attribute</span></span>

|           | <span data-ttu-id="99933-108">Opis</span><span class="sxs-lookup"><span data-stu-id="99933-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="99933-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="99933-109">**xmlns**</span></span> | <span data-ttu-id="99933-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="99933-110">Required attribute.</span></span><br><br><span data-ttu-id="99933-111">Określa przestrzeń nazw XML wymagane w celu tworzenia powiązań zestawów.</span><span class="sxs-lookup"><span data-stu-id="99933-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="99933-112">Użyj ciągu "urn: schemas-microsoft-com:asm.v1" jako wartości.</span><span class="sxs-lookup"><span data-stu-id="99933-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="99933-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="99933-113">Parent element</span></span>

|     | <span data-ttu-id="99933-114">Opis</span><span class="sxs-lookup"><span data-stu-id="99933-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="99933-115">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="99933-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="99933-116">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99933-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="99933-117">Element podrzędny</span><span class="sxs-lookup"><span data-stu-id="99933-117">Child element</span></span>

|     | <span data-ttu-id="99933-118">Opis</span><span class="sxs-lookup"><span data-stu-id="99933-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="99933-119">**\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="99933-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="99933-120">Określa wymagający uwzględnienia plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="99933-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="99933-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99933-121">Remarks</span></span>

<span data-ttu-id="99933-122">[  **\<Linkedconfiguration — >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element ułatwia zarządzanie zestawów składników, umożliwiając pliki konfiguracji aplikacji do dołączenia zestawu plików konfiguracji w lokalizacje znane zamiast duplikowania ustawienia konfiguracji zestawu.</span><span class="sxs-lookup"><span data-stu-id="99933-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="99933-123"> *\*\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o Windows side-by-side manifestów.</span><span class="sxs-lookup"><span data-stu-id="99933-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="99933-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="99933-124">Example</span></span>

<span data-ttu-id="99933-125">Poniższy przykład pokazuje, jak dołączyć plik konfiguracji na lokalnym dysku twardym:</span><span class="sxs-lookup"><span data-stu-id="99933-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="99933-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99933-126">See also</span></span>

- [<span data-ttu-id="99933-127">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="99933-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
