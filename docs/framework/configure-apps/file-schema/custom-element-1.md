---
title: Niestandardowy element SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 07bc0d9560546f4946d34413697fb0adcf84c58d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="e2701-102">Niestandardowy element SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="e2701-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="e2701-103">Definiuje ustawienia w sekcji Konfiguracja niestandardowa, która jest definiowana za pomocą</span><span class="sxs-lookup"><span data-stu-id="e2701-103">Defines settings in a custom configuration section that is defined by a</span></span> <section> <span data-ttu-id="e2701-104">element i używa <xref:System.Configuration.SingleTagSectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="e2701-104">element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="e2701-105">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e2701-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="e2701-106">&nbsp;&nbsp;*\<sectionName >*</span><span class="sxs-lookup"><span data-stu-id="e2701-106">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="e2701-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2701-107">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="e2701-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e2701-108">Attributes</span></span>

<span data-ttu-id="e2701-109">Atrybuty i wartości atrybutów są zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e2701-109">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="e2701-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="e2701-110">Parent element</span></span>

|     | <span data-ttu-id="e2701-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e2701-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e2701-112">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="e2701-112">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="e2701-113">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2701-113">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e2701-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e2701-114">Child elements</span></span>

<span data-ttu-id="e2701-115">Brak</span><span class="sxs-lookup"><span data-stu-id="e2701-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="e2701-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2701-116">Remarks</span></span>

<span data-ttu-id="e2701-117">**\<SectionName >** element jest elementem niestandardowe zdefiniowane przez [  **\<sekcji >** ](~/docs/framework/configure-apps/file-schema/section-element.md) tagów w [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="e2701-117">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="e2701-118">System konfiguracji zwraca <xref:System.Collections.IDictionary> obiektu po wywołaniu <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2701-118">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="e2701-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2701-119">Example</span></span>

<span data-ttu-id="e2701-120">Poniższy przykład deklaruje elementu niestandardowego o nazwie  **\<sampleSection >** zawierający ustawienia odczytywane przez <xref:System.Configuration.SingleTagSectionHandler> klasy:</span><span class="sxs-lookup"><span data-stu-id="e2701-120">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="e2701-121">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e2701-121">Configuration file</span></span>

<span data-ttu-id="e2701-122">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2701-122">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2701-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2701-123">See also</span></span>

[<span data-ttu-id="e2701-124">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e2701-124">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
