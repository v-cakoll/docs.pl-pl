---
title: Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 890269857aaa00ce62195ccb2f4cb184b363b61e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921042"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="3c483-102">Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="3c483-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="3c483-103">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i. <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="3c483-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="3c483-104">[ **\<> konfiguracji**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3c483-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="3c483-105">&nbsp;&nbsp; **\<sectionName>**</span><span class="sxs-lookup"><span data-stu-id="3c483-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="3c483-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3c483-106">Attributes</span></span>

<span data-ttu-id="3c483-107">Brak</span><span class="sxs-lookup"><span data-stu-id="3c483-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="3c483-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="3c483-108">Parent element</span></span>

|     | <span data-ttu-id="3c483-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3c483-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3c483-110"> **\<> konfiguracji**</span><span class="sxs-lookup"><span data-stu-id="3c483-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="3c483-111">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c483-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3c483-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3c483-112">Child elements</span></span>

|     | <span data-ttu-id="3c483-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3c483-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="3c483-114">Dodaj > dla i [ **\<** ](add-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="3c483-114">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="3c483-115">Dodaje niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3c483-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="3c483-116">Usuń > dla i [ **\<** ](remove-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="3c483-116">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="3c483-117">Usuwa poprzednio zdefiniowane ustawienie.</span><span class="sxs-lookup"><span data-stu-id="3c483-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="3c483-118">Wyczyść > dla i [ **\<** ](clear-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="3c483-118">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="3c483-119">Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji.</span><span class="sxs-lookup"><span data-stu-id="3c483-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3c483-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c483-120">Remarks</span></span>

<span data-ttu-id="3c483-121">**\<Parametrami sectionName>** element jest elementem niestandardowe zdefiniowane przez **\<sekcji>** tagów w **\<configSections>** elementu.</span><span class="sxs-lookup"><span data-stu-id="3c483-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="3c483-122">W poniższej tabeli przedstawiono typ obiektu, który zwraca metoda ConfigurationSettings. GetConfig dla każdej procedury obsługi sekcji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="3c483-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="3c483-123">Procedura obsługi sekcji konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3c483-123">Configuration section handler</span></span>                        | <span data-ttu-id="3c483-124">Typ zwracany</span><span class="sxs-lookup"><span data-stu-id="3c483-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="3c483-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c483-125">Example</span></span>

<span data-ttu-id="3c483-126">Poniższy przykład pokazuje, jak zadeklarować sekcje, które używają <xref:System.Configuration.DictionarySectionHandler> klas <xref:System.Configuration.NameValueSectionHandler> i.</span><span class="sxs-lookup"><span data-stu-id="3c483-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="3c483-127">Pierwszy element niestandardowy to  **\<dictionarySample >** , który zawiera <xref:System.Configuration.DictionarySectionHandler> ustawienia odczytane przez klasę w `System.dll` zestawie.</span><span class="sxs-lookup"><span data-stu-id="3c483-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="3c483-128">Drugi element niestandardowy jest  **\<częścią >** , która zawiera <xref:System.Configuration.NameValueSectionHandler> ustawienia odczytane przez klasę w `System.dll` zestawie.</span><span class="sxs-lookup"><span data-stu-id="3c483-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="3c483-129">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3c483-129">Configuration file</span></span>

<span data-ttu-id="3c483-130">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3c483-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c483-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c483-131">See also</span></span>

- [<span data-ttu-id="3c483-132">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3c483-132">Configuration file schema for the .NET Framework</span></span>](index.md)
