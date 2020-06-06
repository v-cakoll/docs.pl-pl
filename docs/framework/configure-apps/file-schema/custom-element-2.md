---
title: Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215477"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="6d45f-102">Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="6d45f-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="6d45f-103">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="6d45f-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a><span data-ttu-id="6d45f-104">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6d45f-104">Attributes</span></span>

<span data-ttu-id="6d45f-105">Brak</span><span class="sxs-lookup"><span data-stu-id="6d45f-105">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="6d45f-106">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="6d45f-106">Parent element</span></span>

|     | <span data-ttu-id="6d45f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6d45f-107">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="6d45f-108">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6d45f-108">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6d45f-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6d45f-109">Child elements</span></span>

|     | <span data-ttu-id="6d45f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6d45f-110">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="6d45f-111">[**\<add>**](add-element-for-custom-2.md)dla <xref:System.Configuration.NameValueSectionHandler> i<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="6d45f-111">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="6d45f-112">Dodaje niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d45f-112">Adds custom application settings.</span></span> |
| <span data-ttu-id="6d45f-113">[**\<remove>**](remove-element-for-custom-2.md)dla <xref:System.Configuration.NameValueSectionHandler> i<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="6d45f-113">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="6d45f-114">Usuwa poprzednio zdefiniowane ustawienie.</span><span class="sxs-lookup"><span data-stu-id="6d45f-114">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="6d45f-115">[**\<clear>**](clear-element-for-custom-2.md)dla <xref:System.Configuration.NameValueSectionHandler> i<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="6d45f-115">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="6d45f-116">Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji.</span><span class="sxs-lookup"><span data-stu-id="6d45f-116">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="6d45f-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d45f-117">Remarks</span></span>

<span data-ttu-id="6d45f-118">**\<sectionName>** Element jest elementem niestandardowym zdefiniowanym przez **\<section>** tag w **\<configSections>** elemencie.</span><span class="sxs-lookup"><span data-stu-id="6d45f-118">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="6d45f-119">W poniższej tabeli przedstawiono typ obiektu, który zwraca metoda ConfigurationSettings. GetConfig dla każdej procedury obsługi sekcji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="6d45f-119">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="6d45f-120">Procedura obsługi sekcji konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6d45f-120">Configuration section handler</span></span>                        | <span data-ttu-id="6d45f-121">Typ zwracany</span><span class="sxs-lookup"><span data-stu-id="6d45f-121">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="6d45f-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d45f-122">Example</span></span>

<span data-ttu-id="6d45f-123">Poniższy przykład pokazuje, jak zadeklarować sekcje, które używają <xref:System.Configuration.DictionarySectionHandler> <xref:System.Configuration.NameValueSectionHandler> klas i.</span><span class="sxs-lookup"><span data-stu-id="6d45f-123">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="6d45f-124">Pierwszy element niestandardowy to **\<dictionarySample>** , który zawiera ustawienia odczytane przez <xref:System.Configuration.DictionarySectionHandler> klasę w `System.dll` zestawie.</span><span class="sxs-lookup"><span data-stu-id="6d45f-124">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="6d45f-125">Drugi element niestandardowy to **\<mySection>** , który zawiera ustawienia odczytane przez <xref:System.Configuration.NameValueSectionHandler> klasę w `System.dll` zestawie.</span><span class="sxs-lookup"><span data-stu-id="6d45f-125">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="6d45f-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6d45f-126">Configuration file</span></span>

<span data-ttu-id="6d45f-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d45f-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d45f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d45f-128">See also</span></span>

- [<span data-ttu-id="6d45f-129">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6d45f-129">Configuration file schema for the .NET Framework</span></span>](index.md)
