---
title: <sectionGroup>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 750708483f9680745eef4531d86fa7ecaa329f51
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301194"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="1dd81-102">\<sectionGroup >, element dla \<configSections ></span><span class="sxs-lookup"><span data-stu-id="1dd81-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="1dd81-103">Definiuje obszar nazw dla sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1dd81-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="1dd81-104">[ **\<Konfiguracja >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1dd81-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="1dd81-105">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="1dd81-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="1dd81-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="1dd81-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1dd81-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dd81-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="1dd81-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1dd81-108">Attribute</span></span>

|           | <span data-ttu-id="1dd81-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1dd81-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="1dd81-110">**name**</span><span class="sxs-lookup"><span data-stu-id="1dd81-110">**name**</span></span>  | <span data-ttu-id="1dd81-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1dd81-111">Required attribute.</span></span><br><br><span data-ttu-id="1dd81-112">Określa nazwę grupy sekcji, który jest definiowany.</span><span class="sxs-lookup"><span data-stu-id="1dd81-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="1dd81-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="1dd81-113">Parent element</span></span>

|     | <span data-ttu-id="1dd81-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1dd81-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1dd81-115"> *\*\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="1dd81-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="1dd81-116">Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1dd81-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="1dd81-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1dd81-117">Child elements</span></span>

|     | <span data-ttu-id="1dd81-118">Opis</span><span class="sxs-lookup"><span data-stu-id="1dd81-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1dd81-119"> *\*\<sekcja >** </span><span class="sxs-lookup"><span data-stu-id="1dd81-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="1dd81-120">Zawiera deklarację sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1dd81-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1dd81-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1dd81-121">Remarks</span></span>

<span data-ttu-id="1dd81-122">Deklarowanie grupy sekcji tworzy tag kontenera dla sekcji konfiguracji i gwarantuje, że nie istnieją żadne konflikty nazewnictwa z sekcji konfiguracji zdefiniowane przez kogoś innego.</span><span class="sxs-lookup"><span data-stu-id="1dd81-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="1dd81-123">Można zagnieżdżać  **\<sectionGroup >** elementów wewnątrz siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="1dd81-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="1dd81-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="1dd81-124">Example</span></span>

<span data-ttu-id="1dd81-125">Poniższy przykład pokazuje sposób deklarowania grupy sekcji i zadeklarować sekcje w obrębie grupy sekcji:</span><span class="sxs-lookup"><span data-stu-id="1dd81-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="1dd81-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1dd81-126">Configuration file</span></span>

<span data-ttu-id="1dd81-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1dd81-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="1dd81-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dd81-128">See also</span></span>

- [<span data-ttu-id="1dd81-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1dd81-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
