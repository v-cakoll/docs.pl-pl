---
title: <configSections>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6024144b6f12df22369366f04c3cbad02c5011d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119021"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="4490e-102">\<element > configSections dla konfiguracji \<</span><span class="sxs-lookup"><span data-stu-id="4490e-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="4490e-103">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4490e-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="4490e-104">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4490e-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="4490e-105">&nbsp;&nbsp; **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="4490e-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="4490e-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4490e-106">Attributes</span></span>

<span data-ttu-id="4490e-107">Brak</span><span class="sxs-lookup"><span data-stu-id="4490e-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="4490e-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="4490e-108">Parent element</span></span>

|     | <span data-ttu-id="4490e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4490e-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4490e-110"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="4490e-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="4490e-111">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4490e-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4490e-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4490e-112">Child elements</span></span>

|     | <span data-ttu-id="4490e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4490e-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4490e-114"> **\<sekcja >** </span><span class="sxs-lookup"><span data-stu-id="4490e-114">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="4490e-115">Zawiera deklarację sekcji konfiguracyjnej.</span><span class="sxs-lookup"><span data-stu-id="4490e-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="4490e-116"> **\<sekcji >** </span><span class="sxs-lookup"><span data-stu-id="4490e-116">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="4490e-117">Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="4490e-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="4490e-118"> **\<Usuń >** </span><span class="sxs-lookup"><span data-stu-id="4490e-118">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="4490e-119">Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji.</span><span class="sxs-lookup"><span data-stu-id="4490e-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="4490e-120"> **\<Wyczyść >** </span><span class="sxs-lookup"><span data-stu-id="4490e-120">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="4490e-121">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="4490e-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4490e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4490e-122">Remarks</span></span>

<span data-ttu-id="4490e-123">Jeśli ten element znajduje się w pliku konfiguracji, musi być pierwszym elementem podrzędnym elementu **\<configuration >** .</span><span class="sxs-lookup"><span data-stu-id="4490e-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="4490e-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="4490e-124">Example</span></span>

<span data-ttu-id="4490e-125">Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracyjną i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="4490e-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="4490e-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4490e-126">Configuration file</span></span>

<span data-ttu-id="4490e-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4490e-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4490e-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4490e-128">See also</span></span>

- [<span data-ttu-id="4490e-129">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4490e-129">Configuration file schema for the .NET Framework</span></span>](index.md)
