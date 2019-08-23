---
title: <assemblyBinding>, element dla <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921273"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="4007c-102">\<zestawbinding > elementu \<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4007c-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="4007c-103">Określa zasady powiązań zestawów na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4007c-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="4007c-104">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4007c-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="4007c-105">&nbsp;&nbsp; **\<> zestawubinding**</span><span class="sxs-lookup"><span data-stu-id="4007c-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4007c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4007c-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="4007c-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4007c-107">Attribute</span></span>

|           | <span data-ttu-id="4007c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4007c-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4007c-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="4007c-109">**xmlns**</span></span> | <span data-ttu-id="4007c-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4007c-110">Required attribute.</span></span><br><br><span data-ttu-id="4007c-111">Określa przestrzeń nazw XML wymaganą dla powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="4007c-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="4007c-112">Użyj ciągu "urn: schematys-Microsoft-com: ASM. v1" jako wartości.</span><span class="sxs-lookup"><span data-stu-id="4007c-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4007c-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="4007c-113">Parent element</span></span>

|     | <span data-ttu-id="4007c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4007c-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4007c-115"> **\<> konfiguracji**</span><span class="sxs-lookup"><span data-stu-id="4007c-115">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="4007c-116">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4007c-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="4007c-117">Element podrzędny</span><span class="sxs-lookup"><span data-stu-id="4007c-117">Child element</span></span>

|     | <span data-ttu-id="4007c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4007c-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4007c-119"> **\<linkedConfiguration>** </span><span class="sxs-lookup"><span data-stu-id="4007c-119">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="4007c-120">Określa plik konfiguracji, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="4007c-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4007c-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4007c-121">Remarks</span></span>

<span data-ttu-id="4007c-122">[ **\<Linkedconfiguration — >** ](linkedconfiguration-element.md) element ułatwia zarządzanie zestawów składników, umożliwiając pliki konfiguracji aplikacji do dołączenia zestawu plików konfiguracji w lokalizacje znane zamiast duplikowania ustawienia konfiguracji zestawu.</span><span class="sxs-lookup"><span data-stu-id="4007c-122">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="4007c-123">**\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o Windows side-by-side manifestów.</span><span class="sxs-lookup"><span data-stu-id="4007c-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="4007c-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="4007c-124">Example</span></span>

<span data-ttu-id="4007c-125">Poniższy przykład pokazuje, jak dołączyć plik konfiguracji na lokalnym dysku twardym:</span><span class="sxs-lookup"><span data-stu-id="4007c-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4007c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4007c-126">See also</span></span>

- [<span data-ttu-id="4007c-127">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4007c-127">Configuration file schema for the .NET Framework</span></span>](index.md)
