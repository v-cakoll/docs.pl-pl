---
title: <assemblyBinding>, element dla <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155482"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="675c7-102">\<element> \<do konfiguracji></span><span class="sxs-lookup"><span data-stu-id="675c7-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="675c7-103">Określa zasady wiązania zestawu na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="675c7-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="675c7-104">konfiguracja &nbsp; &nbsp;>[\*\* \<\*\*](configuration-element.md) \*\* \<montażUUwiązanie>\*\*</span><span class="sxs-lookup"><span data-stu-id="675c7-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="675c7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="675c7-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="675c7-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="675c7-106">Attribute</span></span>

|           | <span data-ttu-id="675c7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="675c7-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="675c7-108">**Xmlns**</span><span class="sxs-lookup"><span data-stu-id="675c7-108">**xmlns**</span></span> | <span data-ttu-id="675c7-109">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="675c7-109">Required attribute.</span></span><br><br><span data-ttu-id="675c7-110">Określa obszar nazw XML wymagany dla powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="675c7-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="675c7-111">Użyj ciągu "urn:schemas-microsoft-com:asm.v1" jako wartości.</span><span class="sxs-lookup"><span data-stu-id="675c7-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="675c7-112">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="675c7-112">Parent element</span></span>

|     | <span data-ttu-id="675c7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="675c7-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="675c7-114">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="675c7-114">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="675c7-115">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="675c7-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="675c7-116">Element podrzędny</span><span class="sxs-lookup"><span data-stu-id="675c7-116">Child element</span></span>

|     | <span data-ttu-id="675c7-117">Opis</span><span class="sxs-lookup"><span data-stu-id="675c7-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="675c7-118">**\<>konfiguracji linkedConfiguration**</span><span class="sxs-lookup"><span data-stu-id="675c7-118">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="675c7-119">Określa plik konfiguracji do uwzględnienia.</span><span class="sxs-lookup"><span data-stu-id="675c7-119">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="675c7-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="675c7-120">Remarks</span></span>

<span data-ttu-id="675c7-121">Element [\*\* \<>linkedConfiguration\*\*](linkedconfiguration-element.md) upraszcza zarządzanie zestawami komponentów, umożliwiając plikom konfiguracyjnym aplikacji dołączanie plików konfiguracyjnych w dobrze znanych lokalizacjach, a nie duplikowanie ustawień konfiguracji zestawu.</span><span class="sxs-lookup"><span data-stu-id="675c7-121">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="675c7-122">Element \*\* \<linkedConfiguration>\*\* nie jest obsługiwany dla aplikacji z manifestami obok siebie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="675c7-122">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="675c7-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="675c7-123">Example</span></span>

<span data-ttu-id="675c7-124">W poniższym przykładzie pokazano, jak dołączyć plik konfiguracyjny na lokalnym dysku twardym:</span><span class="sxs-lookup"><span data-stu-id="675c7-124">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="675c7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="675c7-125">See also</span></span>

- [<span data-ttu-id="675c7-126">Schemat pliku konfiguracyjnego programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="675c7-126">Configuration file schema for the .NET Framework</span></span>](index.md)
