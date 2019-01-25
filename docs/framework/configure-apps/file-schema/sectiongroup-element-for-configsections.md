---
title: '&lt;sectionGroup&gt; elementu &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 82f89e74d6a09b2c157ff9a273f078e606222f63
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523899"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="6557a-102">\<sectionGroup >, element dla \<configSections ></span><span class="sxs-lookup"><span data-stu-id="6557a-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="6557a-103">Definiuje obszar nazw dla sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6557a-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="6557a-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6557a-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="6557a-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="6557a-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="6557a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="6557a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6557a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6557a-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="6557a-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6557a-108">Attribute</span></span>

|           | <span data-ttu-id="6557a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6557a-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="6557a-110">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6557a-110">**name**</span></span>  | <span data-ttu-id="6557a-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6557a-111">Required attribute.</span></span><br><br><span data-ttu-id="6557a-112">Określa nazwę grupy sekcji, który jest definiowany.</span><span class="sxs-lookup"><span data-stu-id="6557a-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="6557a-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="6557a-113">Parent element</span></span>

|     | <span data-ttu-id="6557a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6557a-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6557a-115">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="6557a-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="6557a-116">Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6557a-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6557a-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6557a-117">Child elements</span></span>

|     | <span data-ttu-id="6557a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="6557a-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6557a-119">**\<sekcja >**</span><span class="sxs-lookup"><span data-stu-id="6557a-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="6557a-120">Zawiera deklarację sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6557a-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="6557a-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6557a-121">Remarks</span></span>

<span data-ttu-id="6557a-122">Deklarowanie grupy sekcji tworzy tag kontenera dla sekcji konfiguracji i gwarantuje, że nie istnieją żadne konflikty nazewnictwa z sekcji konfiguracji zdefiniowane przez kogoś innego.</span><span class="sxs-lookup"><span data-stu-id="6557a-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="6557a-123">Można zagnieżdżać  **\<sectionGroup >** elementów wewnątrz siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="6557a-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="6557a-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="6557a-124">Example</span></span>

<span data-ttu-id="6557a-125">Poniższy przykład pokazuje sposób deklarowania grupy sekcji i zadeklarować sekcje w obrębie grupy sekcji:</span><span class="sxs-lookup"><span data-stu-id="6557a-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="6557a-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6557a-126">Configuration file</span></span>

<span data-ttu-id="6557a-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6557a-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6557a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6557a-128">See also</span></span>

- [<span data-ttu-id="6557a-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6557a-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
