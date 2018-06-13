---
title: '&lt;assemblybinding —&gt; elementu &lt;konfiguracji&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6a3358b2d64ade65e641caa203e2e760dcc4be2c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743124"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="063ac-102">\<assemblybinding — > elementu \<configuration ></span><span class="sxs-lookup"><span data-stu-id="063ac-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="063ac-103">Określa zestaw powiązania zasad na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="063ac-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="063ac-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="063ac-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="063ac-105">&nbsp;&nbsp;**\<assemblybinding — >**</span><span class="sxs-lookup"><span data-stu-id="063ac-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="063ac-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="063ac-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="063ac-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="063ac-107">Attribute</span></span>

|           | <span data-ttu-id="063ac-108">Opis</span><span class="sxs-lookup"><span data-stu-id="063ac-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="063ac-109">**Xmlns**</span><span class="sxs-lookup"><span data-stu-id="063ac-109">**xmlns**</span></span> | <span data-ttu-id="063ac-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="063ac-110">Required attribute.</span></span><br><br><span data-ttu-id="063ac-111">Określa przestrzeń nazw XML, wymagane do powiązań zestawów.</span><span class="sxs-lookup"><span data-stu-id="063ac-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="063ac-112">Należy użyć ciągu "urn: schemas-microsoft-com:asm.v1" jako wartości.</span><span class="sxs-lookup"><span data-stu-id="063ac-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="063ac-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="063ac-113">Parent element</span></span>

|     | <span data-ttu-id="063ac-114">Opis</span><span class="sxs-lookup"><span data-stu-id="063ac-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="063ac-115">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="063ac-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="063ac-116">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="063ac-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="063ac-117">Element podrzędny</span><span class="sxs-lookup"><span data-stu-id="063ac-117">Child element</span></span>

|     | <span data-ttu-id="063ac-118">Opis</span><span class="sxs-lookup"><span data-stu-id="063ac-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="063ac-119">**\<linkedconfiguration — >**</span><span class="sxs-lookup"><span data-stu-id="063ac-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="063ac-120">Określa plik konfiguracji do uwzględnienia.</span><span class="sxs-lookup"><span data-stu-id="063ac-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="063ac-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="063ac-121">Remarks</span></span>

<span data-ttu-id="063ac-122">[  **\<Linkedconfiguration — >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element upraszcza zarządzanie zestawów składników, zezwalając pliki konfiguracji aplikacji, aby uwzględnić zestawu plików konfiguracyjnych w dobrze znanej lokalizacji, a nie ustawienia konfiguracji usługi zduplikować zestawu.</span><span class="sxs-lookup"><span data-stu-id="063ac-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="063ac-123">**\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o manifestów side-by-side systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="063ac-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="063ac-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="063ac-124">Example</span></span>

<span data-ttu-id="063ac-125">Poniższy przykład przedstawia dołączenie pliku konfiguracji na lokalnym dysku twardym:</span><span class="sxs-lookup"><span data-stu-id="063ac-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="063ac-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="063ac-126">See also</span></span>

[<span data-ttu-id="063ac-127">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="063ac-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
