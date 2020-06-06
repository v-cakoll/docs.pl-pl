---
title: <sectionGroup>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: eb221027470fe6e485f8fcc4b939b71e4f219712
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215260"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="cc6f2-102">\<sectionGroup>, element dla \<configSections></span><span class="sxs-lookup"><span data-stu-id="cc6f2-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="cc6f2-103">Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="cc6f2-103">Defines a namespace for configuration sections.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a><span data-ttu-id="cc6f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc6f2-104">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="cc6f2-105">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cc6f2-105">Attribute</span></span>

|           | <span data-ttu-id="cc6f2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cc6f2-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="cc6f2-107">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="cc6f2-107">**name**</span></span>  | <span data-ttu-id="cc6f2-108">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="cc6f2-108">Required attribute.</span></span><br><br><span data-ttu-id="cc6f2-109">Określa nazwę definiowanej grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="cc6f2-109">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="cc6f2-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="cc6f2-110">Parent element</span></span>

|     | <span data-ttu-id="cc6f2-111">Opis</span><span class="sxs-lookup"><span data-stu-id="cc6f2-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cc6f2-112">**\<configSections>** Postaci</span><span class="sxs-lookup"><span data-stu-id="cc6f2-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="cc6f2-113">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cc6f2-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="cc6f2-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cc6f2-114">Child elements</span></span>

|     | <span data-ttu-id="cc6f2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="cc6f2-115">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="cc6f2-116">Zawiera deklarację sekcji konfiguracyjnej.</span><span class="sxs-lookup"><span data-stu-id="cc6f2-116">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="cc6f2-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc6f2-117">Remarks</span></span>

<span data-ttu-id="cc6f2-118">Deklarowanie grupy sekcji tworzy tag kontenera dla sekcji konfiguracyjnych i zapewnia, że nie występują konflikty nazw z sekcjami konfiguracji zdefiniowanymi przez kogoś innego.</span><span class="sxs-lookup"><span data-stu-id="cc6f2-118">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="cc6f2-119">Można zagnieżdżać **\<sectionGroup>** elementy w obrębie siebie.</span><span class="sxs-lookup"><span data-stu-id="cc6f2-119">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="cc6f2-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc6f2-120">Example</span></span>

<span data-ttu-id="cc6f2-121">Poniższy przykład pokazuje, jak zadeklarować grupę sekcji i zadeklarować sekcje w grupie sekcji:</span><span class="sxs-lookup"><span data-stu-id="cc6f2-121">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="cc6f2-122">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cc6f2-122">Configuration file</span></span>

<span data-ttu-id="cc6f2-123">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc6f2-123">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc6f2-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc6f2-124">See also</span></span>

- [<span data-ttu-id="cc6f2-125">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cc6f2-125">Configuration file schema for the .NET Framework</span></span>](index.md)
