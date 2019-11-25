---
title: <sectionGroup>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 746a997e162b0fd370a249b8d039be623b57d77f
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089004"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="de049-102">\<> elementu \<configSections ></span><span class="sxs-lookup"><span data-stu-id="de049-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="de049-103">Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="de049-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="de049-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="de049-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="de049-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="de049-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="de049-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<sekcji >**</span><span class="sxs-lookup"><span data-stu-id="de049-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="de049-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="de049-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="de049-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="de049-108">Attribute</span></span>

|           | <span data-ttu-id="de049-109">Opis</span><span class="sxs-lookup"><span data-stu-id="de049-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="de049-110">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="de049-110">**name**</span></span>  | <span data-ttu-id="de049-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="de049-111">Required attribute.</span></span><br><br><span data-ttu-id="de049-112">Określa nazwę definiowanej grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="de049-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="de049-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="de049-113">Parent element</span></span>

|     | <span data-ttu-id="de049-114">Opis</span><span class="sxs-lookup"><span data-stu-id="de049-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="de049-115"> **\<configSections >** Postaci</span><span class="sxs-lookup"><span data-stu-id="de049-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="de049-116">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="de049-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="de049-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="de049-117">Child elements</span></span>

|     | <span data-ttu-id="de049-118">Opis</span><span class="sxs-lookup"><span data-stu-id="de049-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="de049-119"> **\<sekcja >** </span><span class="sxs-lookup"><span data-stu-id="de049-119">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="de049-120">Zawiera deklarację sekcji konfiguracyjnej.</span><span class="sxs-lookup"><span data-stu-id="de049-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="de049-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de049-121">Remarks</span></span>

<span data-ttu-id="de049-122">Deklarowanie grupy sekcji tworzy tag kontenera dla sekcji konfiguracyjnych i zapewnia, że nie występują konflikty nazw z sekcjami konfiguracji zdefiniowanymi przez kogoś innego.</span><span class="sxs-lookup"><span data-stu-id="de049-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="de049-123">\<można zagnieżdżać **>** elementów w obrębie siebie.</span><span class="sxs-lookup"><span data-stu-id="de049-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="de049-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="de049-124">Example</span></span>

<span data-ttu-id="de049-125">Poniższy przykład pokazuje, jak zadeklarować grupę sekcji i zadeklarować sekcje w grupie sekcji:</span><span class="sxs-lookup"><span data-stu-id="de049-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="de049-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="de049-126">Configuration file</span></span>

<span data-ttu-id="de049-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de049-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="de049-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de049-128">See also</span></span>

- [<span data-ttu-id="de049-129">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="de049-129">Configuration file schema for the .NET Framework</span></span>](index.md)
