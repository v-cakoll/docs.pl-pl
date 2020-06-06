---
title: Element niestandardowy dla SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "80635399"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="65695-102">Element niestandardowy dla SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="65695-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="65695-103">Definiuje ustawienia w sekcji konfiguracji niestandardowej zdefiniowanej przez \<section> element i używa <xref:System.Configuration.SingleTagSectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="65695-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="65695-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="65695-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="65695-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="65695-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="65695-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="65695-106">Attributes</span></span>

<span data-ttu-id="65695-107">Atrybuty i wartości atrybutów są zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="65695-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="65695-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="65695-108">Parent element</span></span>

|     | <span data-ttu-id="65695-109">Opis</span><span class="sxs-lookup"><span data-stu-id="65695-109">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="65695-110">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65695-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="65695-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="65695-111">Child elements</span></span>

<span data-ttu-id="65695-112">Brak</span><span class="sxs-lookup"><span data-stu-id="65695-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="65695-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65695-113">Remarks</span></span>

<span data-ttu-id="65695-114">**\<sectionName>** Element jest elementem niestandardowym zdefiniowanym przez [**\<section>**](section-element.md) tag w [**\<configSections>**](configsections-element-for-configuration.md) elemencie.</span><span class="sxs-lookup"><span data-stu-id="65695-114">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="65695-115">System konfiguracji zwraca <xref:System.Collections.IDictionary> obiekt podczas wywoływania <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="65695-115">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="65695-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="65695-116">Example</span></span>

<span data-ttu-id="65695-117">Poniższy przykład deklaruje element niestandardowy o nazwie **\<sampleSection>** , który zawiera ustawienia odczytane przez <xref:System.Configuration.SingleTagSectionHandler> klasę:</span><span class="sxs-lookup"><span data-stu-id="65695-117">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="65695-118">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="65695-118">Configuration file</span></span>

<span data-ttu-id="65695-119">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65695-119">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="65695-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65695-120">See also</span></span>

- [<span data-ttu-id="65695-121">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="65695-121">Configuration file schema for the .NET Framework</span></span>](index.md)
