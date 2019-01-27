---
title: Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 74496726aa2fe5c88a273a22f096c585aa54de0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693801"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="71209-102">Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="71209-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="71209-103">Definiuje ustawienia powiązane z sekcji konfiguracji niestandardowej, korzystających z <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="71209-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="71209-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="71209-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="71209-105">&nbsp;&nbsp;**\<sectionName>**</span><span class="sxs-lookup"><span data-stu-id="71209-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="71209-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="71209-106">Attributes</span></span>

<span data-ttu-id="71209-107">Brak</span><span class="sxs-lookup"><span data-stu-id="71209-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="71209-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="71209-108">Parent element</span></span>

|     | <span data-ttu-id="71209-109">Opis</span><span class="sxs-lookup"><span data-stu-id="71209-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="71209-110">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="71209-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="71209-111">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71209-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="71209-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="71209-112">Child elements</span></span>

|     | <span data-ttu-id="71209-113">Opis</span><span class="sxs-lookup"><span data-stu-id="71209-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="71209-114">[**\<Dodaj >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) dla <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="71209-114">[**\<add>**](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="71209-115">Dodaje ustawienia bezpieczeństwa aplikacji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="71209-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="71209-116">[**\<Usuń >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) dla <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="71209-116">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> |    <span data-ttu-id="71209-117">Usuwa ustawienie uprzednio zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="71209-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="71209-118">[**\<Wyczyść >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) dla <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="71209-118">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="71209-119">Czyści wszystkie wcześniej zdefiniowane ustawienia w sekcji.</span><span class="sxs-lookup"><span data-stu-id="71209-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="71209-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71209-120">Remarks</span></span>

<span data-ttu-id="71209-121"> *\*\<Parametrami sectionName >** element jest elementem niestandardowe zdefiniowane przez  *\*\<sekcji >** tagów w  *\*\<configSections >** elementu.</span><span class="sxs-lookup"><span data-stu-id="71209-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="71209-122">W poniższej tabeli przedstawiono typ obiektu, metoda ConfigurationSettings.GetConfig zwraca dla każdej procedury obsługi sekcji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="71209-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="71209-123">Program obsługi sekcji konfiguracji</span><span class="sxs-lookup"><span data-stu-id="71209-123">Configuration section handler</span></span>                        | <span data-ttu-id="71209-124">Zwracany typ</span><span class="sxs-lookup"><span data-stu-id="71209-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="71209-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="71209-125">Example</span></span>

<span data-ttu-id="71209-126">Poniższy przykład pokazuje sposób deklarowania sekcje, które używają <xref:System.Configuration.DictionarySectionHandler> i <xref:System.Configuration.NameValueSectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="71209-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span> 

<span data-ttu-id="71209-127">Pierwszy element niestandardowego jest  **\<dictionarySample >**, który zawiera ustawienia odczytywane przez <xref:System.Configuration.DictionarySectionHandler> klasy w `System.dll` zestawu.</span><span class="sxs-lookup"><span data-stu-id="71209-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="71209-128">Drugi element niestandardowego jest  **\<mySection >**, który zawiera ustawienia odczytywane przez <xref:System.Configuration.NameValueSectionHandler> klasy w `System.dll` zestawu.</span><span class="sxs-lookup"><span data-stu-id="71209-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="71209-129">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="71209-129">Configuration file</span></span>

<span data-ttu-id="71209-130">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71209-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="71209-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71209-131">See also</span></span>

- [<span data-ttu-id="71209-132">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="71209-132">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
