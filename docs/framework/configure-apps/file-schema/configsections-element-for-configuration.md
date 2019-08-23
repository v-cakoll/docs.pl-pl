---
title: <configSections>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927673"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="806bf-102">\<configSections > elementu \<konfiguracji ></span><span class="sxs-lookup"><span data-stu-id="806bf-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="806bf-103">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="806bf-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="806bf-104">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="806bf-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="806bf-105">&nbsp;&nbsp; **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="806bf-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="806bf-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="806bf-106">Attributes</span></span>

<span data-ttu-id="806bf-107">Brak</span><span class="sxs-lookup"><span data-stu-id="806bf-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="806bf-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="806bf-108">Parent element</span></span>

|     | <span data-ttu-id="806bf-109">Opis</span><span class="sxs-lookup"><span data-stu-id="806bf-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="806bf-110"> **\<> konfiguracji**</span><span class="sxs-lookup"><span data-stu-id="806bf-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="806bf-111">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="806bf-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="806bf-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="806bf-112">Child elements</span></span>

|     | <span data-ttu-id="806bf-113">Opis</span><span class="sxs-lookup"><span data-stu-id="806bf-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="806bf-114"> **\<sekcja >** </span><span class="sxs-lookup"><span data-stu-id="806bf-114">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="806bf-115">Zawiera deklarację sekcji konfiguracyjnej.</span><span class="sxs-lookup"><span data-stu-id="806bf-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="806bf-116"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="806bf-116">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="806bf-117">Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="806bf-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="806bf-118"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="806bf-118">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="806bf-119">Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji.</span><span class="sxs-lookup"><span data-stu-id="806bf-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="806bf-120"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="806bf-120">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="806bf-121">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="806bf-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="806bf-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="806bf-122">Remarks</span></span>

<span data-ttu-id="806bf-123">Jeśli ten element znajduje się w pliku konfiguracji, musi być pierwszym elementem  **\<** podrzędnym elementu Configuration >.</span><span class="sxs-lookup"><span data-stu-id="806bf-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="806bf-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="806bf-124">Example</span></span>

<span data-ttu-id="806bf-125">Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracyjną i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="806bf-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="806bf-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="806bf-126">Configuration file</span></span>

<span data-ttu-id="806bf-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="806bf-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="806bf-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="806bf-128">See also</span></span>

- [<span data-ttu-id="806bf-129">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="806bf-129">Configuration file schema for the .NET Framework</span></span>](index.md)
