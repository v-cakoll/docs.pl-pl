---
title: '&lt;configSections&gt; elementu &lt;konfiguracji&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 145a2a5cc23758c9fd2211c2da7fee0bbd736f0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="bc968-102">\<configSections > elementu \<configuration ></span><span class="sxs-lookup"><span data-stu-id="bc968-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="bc968-103">Zawiera konfigurację deklaracji sekcji i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bc968-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="bc968-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bc968-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="bc968-105">&nbsp;&nbsp;**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="bc968-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="bc968-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bc968-106">Attributes</span></span>

<span data-ttu-id="bc968-107">Brak</span><span class="sxs-lookup"><span data-stu-id="bc968-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="bc968-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="bc968-108">Parent element</span></span>

|     | <span data-ttu-id="bc968-109">Opis</span><span class="sxs-lookup"><span data-stu-id="bc968-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bc968-110">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="bc968-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="bc968-111">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bc968-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="bc968-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bc968-112">Child elements</span></span>

|     | <span data-ttu-id="bc968-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bc968-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bc968-114">**\<sekcja >**</span><span class="sxs-lookup"><span data-stu-id="bc968-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="bc968-115">Zawiera deklaracji sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bc968-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="bc968-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="bc968-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="bc968-117">Definiuje obszar nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="bc968-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="bc968-118">**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="bc968-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="bc968-119">Usuwa wstępnie zdefiniowanych sekcji lub grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="bc968-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="bc968-120">**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="bc968-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="bc968-121">Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="bc968-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bc968-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc968-122">Remarks</span></span>

<span data-ttu-id="bc968-123">W przypadku tego elementu w pliku konfiguracji, musi być pierwszym elementem podrzędnym  **\<konfiguracji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="bc968-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="bc968-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc968-124">Example</span></span>

<span data-ttu-id="bc968-125">Poniższy przykład pokazuje, jak planować sekcji konfiguracji i określać ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="bc968-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="bc968-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bc968-126">Configuration file</span></span>

<span data-ttu-id="bc968-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bc968-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc968-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc968-128">See also</span></span>

[<span data-ttu-id="bc968-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bc968-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
