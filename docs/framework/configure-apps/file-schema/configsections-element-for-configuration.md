---
title: <configSections>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 1e4bb7a7cfb0b140ca6d13c162708c3c30bd496d
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441690"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="8a903-102">\<configSections>, element dla \<configuration></span><span class="sxs-lookup"><span data-stu-id="8a903-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="8a903-103">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8a903-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="8a903-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="8a903-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="8a903-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8a903-105">Attributes</span></span>

<span data-ttu-id="8a903-106">Brak</span><span class="sxs-lookup"><span data-stu-id="8a903-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="8a903-107">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="8a903-107">Parent element</span></span>

|     | <span data-ttu-id="8a903-108">Opis</span><span class="sxs-lookup"><span data-stu-id="8a903-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="8a903-109">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a903-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8a903-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8a903-110">Child elements</span></span>

|     | <span data-ttu-id="8a903-111">Opis</span><span class="sxs-lookup"><span data-stu-id="8a903-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="8a903-112">Zawiera deklarację sekcji konfiguracyjnej.</span><span class="sxs-lookup"><span data-stu-id="8a903-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="8a903-113">Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="8a903-113">Defines a namespace for configuration sections.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8a903-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a903-114">Remarks</span></span>

<span data-ttu-id="8a903-115">Jeśli ten element znajduje się w pliku konfiguracji, musi być pierwszym elementem podrzędnym **\<configuration>** elementu.</span><span class="sxs-lookup"><span data-stu-id="8a903-115">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="8a903-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a903-116">Example</span></span>

<span data-ttu-id="8a903-117">Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracyjną i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="8a903-117">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="8a903-118">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8a903-118">Configuration file</span></span>

<span data-ttu-id="8a903-119">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine.config*) i plikach *Web.config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a903-119">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a903-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a903-120">See also</span></span>

- [<span data-ttu-id="8a903-121">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8a903-121">Configuration file schema for the .NET Framework</span></span>](index.md)
