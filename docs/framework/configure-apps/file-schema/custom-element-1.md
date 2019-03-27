---
title: Element niestandardowy dla SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bfc2a916e37ac27d45746eb268912b3752f4d80f
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464440"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="d4a11-102">Element niestandardowy dla SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="d4a11-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="d4a11-103">Definiuje ustawienia w sekcji niestandardowej konfiguracji, który jest definiowany przez \<sekcji > element i używa <xref:System.Configuration.SingleTagSectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="d4a11-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="d4a11-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d4a11-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d4a11-105">&nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="d4a11-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="d4a11-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4a11-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="d4a11-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4a11-107">Attributes</span></span>

<span data-ttu-id="d4a11-108">Atrybuty i wartości atrybutów są zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d4a11-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="d4a11-109">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="d4a11-109">Parent element</span></span>

|     | <span data-ttu-id="d4a11-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d4a11-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d4a11-111">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="d4a11-111">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="d4a11-112">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d4a11-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d4a11-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4a11-113">Child elements</span></span>

<span data-ttu-id="d4a11-114">Brak</span><span class="sxs-lookup"><span data-stu-id="d4a11-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="d4a11-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4a11-115">Remarks</span></span>

<span data-ttu-id="d4a11-116"> *\*\<Parametrami sectionName >** element jest elementem niestandardowe zdefiniowane przez [  *\*\<sekcji >** ](~/docs/framework/configure-apps/file-schema/section-element.md) tagów w [  *\*\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d4a11-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="d4a11-117">Zwraca system konfiguracji <xref:System.Collections.IDictionary> obiektu po wywołaniu <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d4a11-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="d4a11-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4a11-118">Example</span></span>

<span data-ttu-id="d4a11-119">Poniższy przykład deklaruje element niestandardowy o nazwie  **\<sampleSection >** zawierającego ustawienia odczytywane przez <xref:System.Configuration.SingleTagSectionHandler> klasy:</span><span class="sxs-lookup"><span data-stu-id="d4a11-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="d4a11-120">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d4a11-120">Configuration file</span></span>

<span data-ttu-id="d4a11-121">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d4a11-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4a11-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4a11-122">See also</span></span>

- [<span data-ttu-id="d4a11-123">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d4a11-123">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
