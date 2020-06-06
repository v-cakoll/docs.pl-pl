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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155352"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="78a97-102">\<configSections>, element dla \<configuration></span><span class="sxs-lookup"><span data-stu-id="78a97-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="78a97-103">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="78a97-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="78a97-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="78a97-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="78a97-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="78a97-105">Attributes</span></span>

<span data-ttu-id="78a97-106">Brak</span><span class="sxs-lookup"><span data-stu-id="78a97-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="78a97-107">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="78a97-107">Parent element</span></span>

|     | <span data-ttu-id="78a97-108">Opis</span><span class="sxs-lookup"><span data-stu-id="78a97-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="78a97-109">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="78a97-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="78a97-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="78a97-110">Child elements</span></span>

|     | <span data-ttu-id="78a97-111">Opis</span><span class="sxs-lookup"><span data-stu-id="78a97-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="78a97-112">Zawiera deklarację sekcji konfiguracyjnej.</span><span class="sxs-lookup"><span data-stu-id="78a97-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="78a97-113">Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="78a97-113">Defines a namespace for configuration sections.</span></span> |
| [**\<remove>**](remove-element-for-configsections.md) | <span data-ttu-id="78a97-114">Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji.</span><span class="sxs-lookup"><span data-stu-id="78a97-114">Removes a predefined section or section group.</span></span> |
| [**\<clear>**](clear-element-for-configsections.md) | <span data-ttu-id="78a97-115">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="78a97-115">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="78a97-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78a97-116">Remarks</span></span>

<span data-ttu-id="78a97-117">Jeśli ten element znajduje się w pliku konfiguracji, musi być pierwszym elementem podrzędnym **\<configuration>** elementu.</span><span class="sxs-lookup"><span data-stu-id="78a97-117">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="78a97-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="78a97-118">Example</span></span>

<span data-ttu-id="78a97-119">Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracyjną i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="78a97-119">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="78a97-120">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="78a97-120">Configuration file</span></span>

<span data-ttu-id="78a97-121">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78a97-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="78a97-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78a97-122">See also</span></span>

- [<span data-ttu-id="78a97-123">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="78a97-123">Configuration file schema for the .NET Framework</span></span>](index.md)
