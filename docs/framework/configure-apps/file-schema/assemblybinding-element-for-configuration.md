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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155482"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="f1f4a-102">\<assemblyBinding>, element dla \<configuration></span><span class="sxs-lookup"><span data-stu-id="f1f4a-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="f1f4a-103">Określa zasady powiązań zestawów na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1f4a-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="f1f4a-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="f1f4a-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f1f4a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1f4a-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="f1f4a-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f1f4a-106">Attribute</span></span>

|           | <span data-ttu-id="f1f4a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f4a-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f1f4a-108">**'xmlns**</span><span class="sxs-lookup"><span data-stu-id="f1f4a-108">**xmlns**</span></span> | <span data-ttu-id="f1f4a-109">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f1f4a-109">Required attribute.</span></span><br><br><span data-ttu-id="f1f4a-110">Określa przestrzeń nazw XML wymaganą dla powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="f1f4a-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="f1f4a-111">Użyj ciągu "urn: schematys-Microsoft-com: ASM. v1" jako wartości.</span><span class="sxs-lookup"><span data-stu-id="f1f4a-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f1f4a-112">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="f1f4a-112">Parent element</span></span>

|     | <span data-ttu-id="f1f4a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f4a-113">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="f1f4a-114">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1f4a-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="f1f4a-115">Element podrzędny</span><span class="sxs-lookup"><span data-stu-id="f1f4a-115">Child element</span></span>

|     | <span data-ttu-id="f1f4a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f4a-116">Description</span></span> |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | <span data-ttu-id="f1f4a-117">Określa plik konfiguracji, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="f1f4a-117">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f1f4a-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1f4a-118">Remarks</span></span>

<span data-ttu-id="f1f4a-119">[**\<linkedConfiguration>**](linkedconfiguration-element.md)Element upraszcza zarządzanie zestawami składników przez zezwolenie plikom konfiguracji aplikacji na uwzględnianie plików konfiguracji zestawu w dobrze znanych lokalizacjach, a nie duplikowanie ustawień konfiguracji zestawu.</span><span class="sxs-lookup"><span data-stu-id="f1f4a-119">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="f1f4a-120">**\<linkedConfiguration>** Element nie jest obsługiwany w przypadku aplikacji z manifestami równoległymi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f1f4a-120">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="f1f4a-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1f4a-121">Example</span></span>

<span data-ttu-id="f1f4a-122">Poniższy przykład pokazuje, jak dołączyć plik konfiguracji na lokalnym dysku twardym:</span><span class="sxs-lookup"><span data-stu-id="f1f4a-122">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f1f4a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1f4a-123">See also</span></span>

- [<span data-ttu-id="f1f4a-124">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f1f4a-124">Configuration file schema for the .NET Framework</span></span>](index.md)
