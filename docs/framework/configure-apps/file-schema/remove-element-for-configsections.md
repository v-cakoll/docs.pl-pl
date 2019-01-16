---
title: '&lt;Usuń&gt; elementu &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 11a930120c375616d73faae68a6d6807c2f633cb
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307230"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="527a6-102">\<Usuń >, element dla \<configSections ></span><span class="sxs-lookup"><span data-stu-id="527a6-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="527a6-103">Usuwa sekcję wstępnie zdefiniowanych lub grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="527a6-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="527a6-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="527a6-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="527a6-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="527a6-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="527a6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="527a6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="527a6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="527a6-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="527a6-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="527a6-108">Attribute</span></span>

|           | <span data-ttu-id="527a6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="527a6-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="527a6-110">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="527a6-110">**name**</span></span>  | <span data-ttu-id="527a6-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="527a6-111">Required attribute.</span></span><br><br><span data-ttu-id="527a6-112">Określa nazwę sekcji lub grupy sekcji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="527a6-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="527a6-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="527a6-113">Parent element</span></span>

|     | <span data-ttu-id="527a6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="527a6-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="527a6-115">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="527a6-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="527a6-116">Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="527a6-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="527a6-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="527a6-117">Child elements</span></span>

<span data-ttu-id="527a6-118">Brak</span><span class="sxs-lookup"><span data-stu-id="527a6-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="527a6-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="527a6-119">Remarks</span></span>

<span data-ttu-id="527a6-120">Możesz użyć  **\<Usuń >** elementu do usunięcia sekcje i grup sekcji z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="527a6-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="527a6-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="527a6-121">Example</span></span>

<span data-ttu-id="527a6-122">Poniższy przykład pokazuje, jak używać  **\<Usuń >** elementu w pliku konfiguracyjnym aplikacji, aby usunąć sekcję wcześniej zdefiniowane w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="527a6-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="527a6-123">Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="527a6-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="527a6-124">Poniższy kod pliku konfiguracji aplikacji usuwa  **\<sampleSection >** sekcji.</span><span class="sxs-lookup"><span data-stu-id="527a6-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="527a6-125">Po usunięciu aplikacji nie można pobrać ustawień w  **\<sampleSection >**.</span><span class="sxs-lookup"><span data-stu-id="527a6-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="527a6-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="527a6-126">Configuration file</span></span>

<span data-ttu-id="527a6-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="527a6-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="527a6-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="527a6-128">See also</span></span>

[<span data-ttu-id="527a6-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="527a6-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
