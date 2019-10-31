---
title: Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d73c07d58bb226346cb99a1fe50b12bb0e7e746e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118543"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="d764b-102">Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="d764b-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="d764b-103">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają klas <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="d764b-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="d764b-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d764b-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="d764b-105">&nbsp;&nbsp; **\<sectionname >**</span><span class="sxs-lookup"><span data-stu-id="d764b-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="d764b-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d764b-106">Attributes</span></span>

<span data-ttu-id="d764b-107">Brak</span><span class="sxs-lookup"><span data-stu-id="d764b-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="d764b-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="d764b-108">Parent element</span></span>

|     | <span data-ttu-id="d764b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d764b-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d764b-110"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="d764b-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="d764b-111">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d764b-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d764b-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d764b-112">Child elements</span></span>

|     | <span data-ttu-id="d764b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d764b-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="d764b-114">[ **\<dodać >** ](add-element-for-custom-2.md) dla <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="d764b-114">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="d764b-115">Dodaje niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d764b-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="d764b-116">[ **\<usunąć >** ](remove-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="d764b-116">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="d764b-117">Usuwa poprzednio zdefiniowane ustawienie.</span><span class="sxs-lookup"><span data-stu-id="d764b-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="d764b-118">[ **\<wyczyść >** ](clear-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="d764b-118">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="d764b-119">Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji.</span><span class="sxs-lookup"><span data-stu-id="d764b-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d764b-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d764b-120">Remarks</span></span>

<span data-ttu-id="d764b-121">**\<sectionname >** element jest elementem niestandardowym zdefiniowanym przez **\<sekcję >** tagu w\<elementu > **configSections** .</span><span class="sxs-lookup"><span data-stu-id="d764b-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="d764b-122">W poniższej tabeli przedstawiono typ obiektu, który zwraca metoda ConfigurationSettings. GetConfig dla każdej procedury obsługi sekcji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="d764b-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="d764b-123">Procedura obsługi sekcji konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d764b-123">Configuration section handler</span></span>                        | <span data-ttu-id="d764b-124">Typ zwracany</span><span class="sxs-lookup"><span data-stu-id="d764b-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="d764b-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="d764b-125">Example</span></span>

<span data-ttu-id="d764b-126">Poniższy przykład pokazuje, jak zadeklarować sekcje, które używają klas <xref:System.Configuration.DictionarySectionHandler> i <xref:System.Configuration.NameValueSectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="d764b-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="d764b-127">Pierwszy element niestandardowy jest **\<dictionarySample >** , który zawiera ustawienia odczytane przez klasę <xref:System.Configuration.DictionarySectionHandler> w zestawie `System.dll`.</span><span class="sxs-lookup"><span data-stu-id="d764b-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="d764b-128">Drugi element niestandardowy jest **\<sekcji >** , która zawiera ustawienia odczytane przez klasę <xref:System.Configuration.NameValueSectionHandler> w zestawie `System.dll`.</span><span class="sxs-lookup"><span data-stu-id="d764b-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="d764b-129">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d764b-129">Configuration file</span></span>

<span data-ttu-id="d764b-130">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d764b-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d764b-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d764b-131">See also</span></span>

- [<span data-ttu-id="d764b-132">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d764b-132">Configuration file schema for the .NET Framework</span></span>](index.md)
