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
ms.openlocfilehash: d522d004630dee942e24c39a936feae7dc957bd5
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300790"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="2ff23-102">\<configSections >, element dla \<konfiguracji ></span><span class="sxs-lookup"><span data-stu-id="2ff23-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="2ff23-103">Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2ff23-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="2ff23-104">[ **\<Konfiguracja >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2ff23-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="2ff23-105">&nbsp;&nbsp; **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="2ff23-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="2ff23-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2ff23-106">Attributes</span></span>

<span data-ttu-id="2ff23-107">Brak</span><span class="sxs-lookup"><span data-stu-id="2ff23-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="2ff23-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="2ff23-108">Parent element</span></span>

|     | <span data-ttu-id="2ff23-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2ff23-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2ff23-110"> *\*\<Konfiguracja >** </span><span class="sxs-lookup"><span data-stu-id="2ff23-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="2ff23-111">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2ff23-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2ff23-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2ff23-112">Child elements</span></span>

|     | <span data-ttu-id="2ff23-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2ff23-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2ff23-114"> *\*\<sekcja >** </span><span class="sxs-lookup"><span data-stu-id="2ff23-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="2ff23-115">Zawiera deklarację sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2ff23-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="2ff23-116"> *\*\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="2ff23-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="2ff23-117">Definiuje obszar nazw dla sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2ff23-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="2ff23-118"> *\*\<remove>** </span><span class="sxs-lookup"><span data-stu-id="2ff23-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="2ff23-119">Usuwa sekcję wstępnie zdefiniowanych lub grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="2ff23-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="2ff23-120"> *\*\<clear>** </span><span class="sxs-lookup"><span data-stu-id="2ff23-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="2ff23-121">Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="2ff23-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2ff23-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ff23-122">Remarks</span></span>

<span data-ttu-id="2ff23-123">Jeśli ten element znajduje się w pliku konfiguracji, musi to być pierwszy element podrzędny elementu  **\<konfiguracji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="2ff23-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="2ff23-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ff23-124">Example</span></span>

<span data-ttu-id="2ff23-125">Poniższy przykład pokazuje jak zdefiniować sekcję konfiguracji i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="2ff23-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="2ff23-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2ff23-126">Configuration file</span></span>

<span data-ttu-id="2ff23-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2ff23-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ff23-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ff23-128">See also</span></span>

- [<span data-ttu-id="2ff23-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2ff23-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
