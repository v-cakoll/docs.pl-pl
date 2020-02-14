---
title: Element niestandardowy dla SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 1d0431085a04d3fb817dfe0883779acc4d693084
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214783"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="b0278-102">Element niestandardowy dla SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="b0278-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="b0278-103">Definiuje ustawienia w sekcji konfiguracji niestandardowej zdefiniowanej przez \<sekcję > elementu i używa klasy <xref:System.Configuration.SingleTagSectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="b0278-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="b0278-104">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b0278-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="b0278-105">&nbsp;&nbsp; *\<sectionname >*</span><span class="sxs-lookup"><span data-stu-id="b0278-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="b0278-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0278-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="b0278-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b0278-107">Attributes</span></span>

<span data-ttu-id="b0278-108">Atrybuty i wartości atrybutów są zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b0278-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="b0278-109">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="b0278-109">Parent element</span></span>

|     | <span data-ttu-id="b0278-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b0278-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b0278-111"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="b0278-111">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="b0278-112">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0278-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b0278-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b0278-113">Child elements</span></span>

<span data-ttu-id="b0278-114">None</span><span class="sxs-lookup"><span data-stu-id="b0278-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="b0278-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0278-115">Remarks</span></span>

<span data-ttu-id="b0278-116">**\<sectionname >** element jest elementem niestandardowym zdefiniowanym przez [ **\<sekcję >** ](section-element.md) tagu w\<elementu > [**configSections**](configsections-element-for-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="b0278-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="b0278-117">System konfiguracji zwraca obiekt <xref:System.Collections.IDictionary> podczas wywoływania <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b0278-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="b0278-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0278-118">Example</span></span>

<span data-ttu-id="b0278-119">Poniższy przykład deklaruje element niestandardowy o nazwie **\<sampleSection >** , który zawiera ustawienia odczytane przez klasę <xref:System.Configuration.SingleTagSectionHandler>:</span><span class="sxs-lookup"><span data-stu-id="b0278-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="b0278-120">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b0278-120">Configuration file</span></span>

<span data-ttu-id="b0278-121">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0278-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0278-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0278-122">See also</span></span>

- [<span data-ttu-id="b0278-123">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b0278-123">Configuration file schema for the .NET Framework</span></span>](index.md)
