---
title: '&lt;sectionGroup&gt; elementu &lt;configSections&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 654a6e639a24120e1e0c993ebe36f14e75b46a12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="074f1-102">\<sectionGroup > elementu \<configSections ></span><span class="sxs-lookup"><span data-stu-id="074f1-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="074f1-103">Definiuje obszar nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="074f1-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="074f1-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="074f1-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="074f1-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="074f1-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="074f1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="074f1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="074f1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="074f1-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="074f1-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="074f1-108">Attribute</span></span>

|           | <span data-ttu-id="074f1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="074f1-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="074f1-110">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="074f1-110">**name**</span></span>  | <span data-ttu-id="074f1-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="074f1-111">Required attribute.</span></span><br><br><span data-ttu-id="074f1-112">Określa nazwę grupy sekcji definiowanej.</span><span class="sxs-lookup"><span data-stu-id="074f1-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="074f1-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="074f1-113">Parent element</span></span>

|     | <span data-ttu-id="074f1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="074f1-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="074f1-115">**\<configSections >** — Element</span><span class="sxs-lookup"><span data-stu-id="074f1-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="074f1-116">Zawiera konfigurację deklaracji sekcji i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="074f1-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="074f1-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="074f1-117">Child elements</span></span>

|     | <span data-ttu-id="074f1-118">Opis</span><span class="sxs-lookup"><span data-stu-id="074f1-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="074f1-119">**\<sekcja >**</span><span class="sxs-lookup"><span data-stu-id="074f1-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="074f1-120">Zawiera deklaracji sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="074f1-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="074f1-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="074f1-121">Remarks</span></span>

<span data-ttu-id="074f1-122">Deklarowanie grupy sekcji tworzy znacznik sekcji konfiguracji i zapewnia, że nie ma żadnych konfliktów nazw z sekcji konfiguracyjnych, zdefiniowana przez kogoś innego.</span><span class="sxs-lookup"><span data-stu-id="074f1-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="074f1-123">Można zagnieżdżać  **\<sectionGroup >** elementy wewnątrz innych.</span><span class="sxs-lookup"><span data-stu-id="074f1-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="074f1-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="074f1-124">Example</span></span>

<span data-ttu-id="074f1-125">Poniższy przykład przedstawia sposób zadeklarować grupy sekcji ani deklarować sekcje w obrębie grupy sekcji:</span><span class="sxs-lookup"><span data-stu-id="074f1-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="074f1-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="074f1-126">Configuration file</span></span>

<span data-ttu-id="074f1-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="074f1-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="074f1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="074f1-128">See also</span></span>

[<span data-ttu-id="074f1-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="074f1-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
