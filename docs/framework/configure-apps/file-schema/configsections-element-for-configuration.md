---
title: <configSections>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155352"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="9d755-102">\<configSeks> element do \<> konfiguracyjnego</span><span class="sxs-lookup"><span data-stu-id="9d755-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="9d755-103">Zawiera sekcje konfiguracji i deklaracje obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="9d755-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="9d755-104">konfiguracja &nbsp; &nbsp;>[\*\* \<\*\*](configuration-element.md) \*\* \<konfiguracjeSekcje>\*\*</span><span class="sxs-lookup"><span data-stu-id="9d755-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="9d755-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d755-105">Attributes</span></span>

<span data-ttu-id="9d755-106">Brak</span><span class="sxs-lookup"><span data-stu-id="9d755-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="9d755-107">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="9d755-107">Parent element</span></span>

|     | <span data-ttu-id="9d755-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9d755-108">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9d755-109">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="9d755-109">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="9d755-110">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d755-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9d755-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d755-111">Child elements</span></span>

|     | <span data-ttu-id="9d755-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9d755-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9d755-113">**\<>sekcji**</span><span class="sxs-lookup"><span data-stu-id="9d755-113">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="9d755-114">Zawiera deklarację sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d755-114">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="9d755-115">**\<sectionGrupa>**</span><span class="sxs-lookup"><span data-stu-id="9d755-115">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="9d755-116">Definiuje obszar nazw dla sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d755-116">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="9d755-117">**\<usuń>**</span><span class="sxs-lookup"><span data-stu-id="9d755-117">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="9d755-118">Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji.</span><span class="sxs-lookup"><span data-stu-id="9d755-118">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="9d755-119">**\<wyraźne>**</span><span class="sxs-lookup"><span data-stu-id="9d755-119">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="9d755-120">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="9d755-120">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9d755-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d755-121">Remarks</span></span>

<span data-ttu-id="9d755-122">Jeśli ten element znajduje się w pliku konfiguracji, musi być pierwszym elementem podrzędnym \*\* \<elementu konfiguracji>.\*\*</span><span class="sxs-lookup"><span data-stu-id="9d755-122">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="9d755-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d755-123">Example</span></span>

<span data-ttu-id="9d755-124">W poniższym przykładzie pokazano, jak zdefiniować sekcję konfiguracji i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="9d755-124">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="9d755-125">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9d755-125">Configuration file</span></span>

<span data-ttu-id="9d755-126">Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d755-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d755-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d755-127">See also</span></span>

- [<span data-ttu-id="9d755-128">Schemat pliku konfiguracyjnego programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d755-128">Configuration file schema for the .NET Framework</span></span>](index.md)
