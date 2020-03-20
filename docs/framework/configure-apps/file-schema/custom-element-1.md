---
title: Element niestandardowy dla usługi SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 04360a796b18cf1e414f1f84bff247a1e9d8ef9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155157"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="db6e5-102">Element niestandardowy dla usługi SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="db6e5-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="db6e5-103">Definiuje ustawienia w sekcji konfiguracji niestandardowej, \<która jest zdefiniowana przez <xref:System.Configuration.SingleTagSectionHandler> element> sekcji i używa klasy.</span><span class="sxs-lookup"><span data-stu-id="db6e5-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="db6e5-104">&nbsp; [**>\<konfiguracji**](configuration-element.md) &nbsp; \* \<\*</span><span class="sxs-lookup"><span data-stu-id="db6e5-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="db6e5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="db6e5-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="db6e5-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="db6e5-106">Attributes</span></span>

<span data-ttu-id="db6e5-107">Atrybuty i wartości atrybutów są definiowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="db6e5-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="db6e5-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="db6e5-108">Parent element</span></span>

|     | <span data-ttu-id="db6e5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="db6e5-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="db6e5-110">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="db6e5-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="db6e5-111">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db6e5-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="db6e5-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="db6e5-112">Child elements</span></span>

<span data-ttu-id="db6e5-113">Brak</span><span class="sxs-lookup"><span data-stu-id="db6e5-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="db6e5-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db6e5-114">Remarks</span></span>

<span data-ttu-id="db6e5-115">Element \*\* \<>sectionName\*\* jest elementem niestandardowym [\*\* \<\*\*](section-element.md) zdefiniowanym przez znacznik>sekcji w [\*\* \<konfistycznym>elemencie.\*\*](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="db6e5-115">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="db6e5-116">System konfiguracji zwraca <xref:System.Collections.IDictionary> obiekt podczas <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>wywoływania .</span><span class="sxs-lookup"><span data-stu-id="db6e5-116">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="db6e5-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="db6e5-117">Example</span></span>

<span data-ttu-id="db6e5-118">Poniższy przykład deklaruje element niestandardowy o nazwie <xref:System.Configuration.SingleTagSectionHandler> \*\* \<sampleSekcja>,\*\* która zawiera ustawienia odczytane przez klasę:</span><span class="sxs-lookup"><span data-stu-id="db6e5-118">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="db6e5-119">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="db6e5-119">Configuration file</span></span>

<span data-ttu-id="db6e5-120">Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db6e5-120">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="db6e5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db6e5-121">See also</span></span>

- [<span data-ttu-id="db6e5-122">Schemat pliku konfiguracyjnego programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="db6e5-122">Configuration file schema for the .NET Framework</span></span>](index.md)
