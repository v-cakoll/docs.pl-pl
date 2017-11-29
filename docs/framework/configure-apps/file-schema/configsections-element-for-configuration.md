---
title: '&lt;configSections&gt; elementu &lt;konfiguracji&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7bcf425f345a3153a83cc60e76d87b3c32d83dbe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="878ab-102">\<configSections > elementu \<configuration ></span><span class="sxs-lookup"><span data-stu-id="878ab-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="878ab-103">Zawiera konfigurację deklaracji sekcji i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="878ab-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="878ab-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="878ab-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="878ab-105">&nbsp;&nbsp;**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="878ab-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="878ab-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="878ab-106">Attributes</span></span>

<span data-ttu-id="878ab-107">Brak</span><span class="sxs-lookup"><span data-stu-id="878ab-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="878ab-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="878ab-108">Parent element</span></span>

|     | <span data-ttu-id="878ab-109">Opis</span><span class="sxs-lookup"><span data-stu-id="878ab-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="878ab-110">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="878ab-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="878ab-111">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="878ab-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="878ab-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="878ab-112">Child elements</span></span>

|     | <span data-ttu-id="878ab-113">Opis</span><span class="sxs-lookup"><span data-stu-id="878ab-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="878ab-114">**\<sekcja >**</span><span class="sxs-lookup"><span data-stu-id="878ab-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="878ab-115">Zawiera deklaracji sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="878ab-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="878ab-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="878ab-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="878ab-117">Definiuje obszar nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="878ab-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="878ab-118">**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="878ab-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="878ab-119">Usuwa wstępnie zdefiniowanych sekcji lub grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="878ab-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="878ab-120">**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="878ab-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="878ab-121">Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="878ab-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="878ab-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="878ab-122">Remarks</span></span>

<span data-ttu-id="878ab-123">W przypadku tego elementu w pliku konfiguracji, musi być pierwszym elementem podrzędnym  **\<konfiguracji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="878ab-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="878ab-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="878ab-124">Example</span></span>

<span data-ttu-id="878ab-125">Poniższy przykład pokazuje, jak planować sekcji konfiguracji i określać ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="878ab-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="878ab-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="878ab-126">Configuration file</span></span>

<span data-ttu-id="878ab-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="878ab-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="878ab-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="878ab-128">See also</span></span>

[<span data-ttu-id="878ab-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="878ab-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
