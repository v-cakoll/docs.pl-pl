---
title: Element niestandardowy dla SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8fae3673fe72d036802cb1a8366aaa2430c38884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927500"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="1ab9a-102">Element niestandardowy dla SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="1ab9a-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="1ab9a-103">Definiuje ustawienia w sekcji konfiguracji niestandardowej zdefiniowanej przez \<sekcję > elementu i <xref:System.Configuration.SingleTagSectionHandler> używa klasy.</span><span class="sxs-lookup"><span data-stu-id="1ab9a-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="1ab9a-104">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1ab9a-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="1ab9a-105">&nbsp;&nbsp; *\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="1ab9a-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="1ab9a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ab9a-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="1ab9a-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1ab9a-107">Attributes</span></span>

<span data-ttu-id="1ab9a-108">Atrybuty i wartości atrybutów są zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1ab9a-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="1ab9a-109">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="1ab9a-109">Parent element</span></span>

|     | <span data-ttu-id="1ab9a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1ab9a-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1ab9a-111"> **\<> konfiguracji**</span><span class="sxs-lookup"><span data-stu-id="1ab9a-111">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="1ab9a-112">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ab9a-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="1ab9a-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1ab9a-113">Child elements</span></span>

<span data-ttu-id="1ab9a-114">Brak</span><span class="sxs-lookup"><span data-stu-id="1ab9a-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="1ab9a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ab9a-115">Remarks</span></span>

<span data-ttu-id="1ab9a-116">Element **SectionName > jest elementem niestandardowym zdefiniowanym przez tag > sekcji w elemencie > configSections. \<** [ **\<** ](section-element.md) [ **\<** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="1ab9a-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="1ab9a-117">System konfiguracji zwraca <xref:System.Collections.IDictionary> obiekt podczas wywoływania <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1ab9a-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="1ab9a-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ab9a-118">Example</span></span>

<span data-ttu-id="1ab9a-119">Poniższy przykład deklaruje element niestandardowy o nazwie  **\<sampleSection >** , który zawiera <xref:System.Configuration.SingleTagSectionHandler> ustawienia odczytane przez klasę:</span><span class="sxs-lookup"><span data-stu-id="1ab9a-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="1ab9a-120">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1ab9a-120">Configuration file</span></span>

<span data-ttu-id="1ab9a-121">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1ab9a-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ab9a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ab9a-122">See also</span></span>

- [<span data-ttu-id="1ab9a-123">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1ab9a-123">Configuration file schema for the .NET Framework</span></span>](index.md)
