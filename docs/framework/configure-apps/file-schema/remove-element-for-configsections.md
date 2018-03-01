---
title: "&lt;Usuń&gt; elementu &lt;configSections&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bf2cb49fbeb01ad176a1d24d711cebc97ba14004
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="fd1fa-102">\<Usuń > elementu \<configSections ></span><span class="sxs-lookup"><span data-stu-id="fd1fa-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="fd1fa-103">Usuwa wstępnie zdefiniowanych sekcji lub grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="fd1fa-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="fd1fa-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="fd1fa-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="fd1fa-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="fd1fa-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="fd1fa-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="fd1fa-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fd1fa-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd1fa-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="fd1fa-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fd1fa-108">Attribute</span></span>

|           | <span data-ttu-id="fd1fa-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fd1fa-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="fd1fa-110">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="fd1fa-110">**name**</span></span>  | <span data-ttu-id="fd1fa-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fd1fa-111">Required attribute.</span></span><br><br><span data-ttu-id="fd1fa-112">Określa nazwę sekcji lub grupy sekcji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="fd1fa-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="fd1fa-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="fd1fa-113">Parent element</span></span>

|     | <span data-ttu-id="fd1fa-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fd1fa-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fd1fa-115">**\<configSections >** — Element</span><span class="sxs-lookup"><span data-stu-id="fd1fa-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="fd1fa-116">Zawiera konfigurację deklaracji sekcji i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fd1fa-116">Contains configuration section and namespace declarations.</span></span> |

# <a name="child-elements"></a><span data-ttu-id="fd1fa-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fd1fa-117">Child elements</span></span>

<span data-ttu-id="fd1fa-118">Brak</span><span class="sxs-lookup"><span data-stu-id="fd1fa-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="fd1fa-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd1fa-119">Remarks</span></span>

<span data-ttu-id="fd1fa-120">Można użyć  **\<Usuń >** elementu do usunięcia sekcje i grup sekcji z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fd1fa-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="fd1fa-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd1fa-121">Example</span></span>

<span data-ttu-id="fd1fa-122">Poniższy przykład przedstawia użycie  **\<Usuń >** elementu w pliku konfiguracji aplikacji, aby usunąć sekcję wcześniej zdefiniowanej w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="fd1fa-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="fd1fa-123">Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="fd1fa-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="fd1fa-124">Poniższy kod pliku konfiguracji aplikacji usuwa  **\<sampleSection >** sekcji.</span><span class="sxs-lookup"><span data-stu-id="fd1fa-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="fd1fa-125">Po usunięciu aplikacji nie można pobrać ustawień w  **\<sampleSection >**.</span><span class="sxs-lookup"><span data-stu-id="fd1fa-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="fd1fa-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fd1fa-126">Configuration file</span></span>

<span data-ttu-id="fd1fa-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd1fa-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd1fa-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd1fa-128">See also</span></span>

[<span data-ttu-id="fd1fa-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fd1fa-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
