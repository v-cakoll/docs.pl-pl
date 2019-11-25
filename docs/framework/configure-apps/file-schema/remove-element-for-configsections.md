---
title: <remove>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efc7208aa51cbf6abdb2fe151d48071c0aa95b5c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089052"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="07a3d-102">\<usunąć > elementu \<configSections ></span><span class="sxs-lookup"><span data-stu-id="07a3d-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="07a3d-103">Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji.</span><span class="sxs-lookup"><span data-stu-id="07a3d-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="07a3d-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="07a3d-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="07a3d-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="07a3d-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="07a3d-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<usuń >**</span><span class="sxs-lookup"><span data-stu-id="07a3d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="07a3d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="07a3d-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="07a3d-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="07a3d-108">Attribute</span></span>

|           | <span data-ttu-id="07a3d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="07a3d-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="07a3d-110">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="07a3d-110">**name**</span></span>  | <span data-ttu-id="07a3d-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="07a3d-111">Required attribute.</span></span><br><br><span data-ttu-id="07a3d-112">Określa nazwę sekcji lub grupy sekcji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="07a3d-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="07a3d-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="07a3d-113">Parent element</span></span>

|     | <span data-ttu-id="07a3d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="07a3d-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="07a3d-115"> **\<configSections >** Postaci</span><span class="sxs-lookup"><span data-stu-id="07a3d-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="07a3d-116">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="07a3d-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="07a3d-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="07a3d-117">Child elements</span></span>

<span data-ttu-id="07a3d-118">Brak</span><span class="sxs-lookup"><span data-stu-id="07a3d-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="07a3d-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07a3d-119">Remarks</span></span>

<span data-ttu-id="07a3d-120">Można użyć elementu **\<remove >** , aby usunąć sekcje i grupy sekcji z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="07a3d-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="07a3d-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="07a3d-121">Example</span></span>

<span data-ttu-id="07a3d-122">Poniższy przykład pokazuje, jak użyć **\<usunąć >** elementu w pliku konfiguracyjnym aplikacji, aby usunąć sekcję wcześniej zdefiniowaną w pliku konfiguracji maszyny.</span><span class="sxs-lookup"><span data-stu-id="07a3d-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="07a3d-123">Następujący kod pliku konfiguracji komputera deklaruje sekcję **\<sampleSection >** :</span><span class="sxs-lookup"><span data-stu-id="07a3d-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
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

<span data-ttu-id="07a3d-124">Poniższy kod pliku konfiguracji aplikacji usuwa sekcję **\<sampleSection >** .</span><span class="sxs-lookup"><span data-stu-id="07a3d-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="07a3d-125">Po usunięciu aplikacja nie może pobrać ustawień w **\<sampleSection >** .</span><span class="sxs-lookup"><span data-stu-id="07a3d-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="07a3d-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="07a3d-126">Configuration file</span></span>

<span data-ttu-id="07a3d-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07a3d-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="07a3d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07a3d-128">See also</span></span>

- [<span data-ttu-id="07a3d-129">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="07a3d-129">Configuration file schema for the .NET Framework</span></span>](index.md)
