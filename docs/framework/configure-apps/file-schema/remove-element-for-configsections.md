---
title: <remove>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9ceffd3194c7df41f12ac6cd6b589602965b4920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674314"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="3ad0c-102">\<Usuń >, element dla \<configSections ></span><span class="sxs-lookup"><span data-stu-id="3ad0c-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="3ad0c-103">Usuwa sekcję wstępnie zdefiniowanych lub grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="3ad0c-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="3ad0c-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3ad0c-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="3ad0c-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3ad0c-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="3ad0c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="3ad0c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3ad0c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ad0c-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="3ad0c-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3ad0c-108">Attribute</span></span>

|           | <span data-ttu-id="3ad0c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3ad0c-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="3ad0c-110">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3ad0c-110">**name**</span></span>  | <span data-ttu-id="3ad0c-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3ad0c-111">Required attribute.</span></span><br><br><span data-ttu-id="3ad0c-112">Określa nazwę sekcji lub grupy sekcji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="3ad0c-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="3ad0c-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="3ad0c-113">Parent element</span></span>

|     | <span data-ttu-id="3ad0c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3ad0c-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3ad0c-115">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="3ad0c-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="3ad0c-116">Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3ad0c-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3ad0c-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ad0c-117">Child elements</span></span>

<span data-ttu-id="3ad0c-118">Brak</span><span class="sxs-lookup"><span data-stu-id="3ad0c-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="3ad0c-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ad0c-119">Remarks</span></span>

<span data-ttu-id="3ad0c-120">Możesz użyć  **\<Usuń >** elementu do usunięcia sekcje i grup sekcji z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3ad0c-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="3ad0c-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ad0c-121">Example</span></span>

<span data-ttu-id="3ad0c-122">Poniższy przykład pokazuje, jak używać  **\<Usuń >** elementu w pliku konfiguracyjnym aplikacji, aby usunąć sekcję wcześniej zdefiniowane w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="3ad0c-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="3ad0c-123">Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="3ad0c-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="3ad0c-124">Poniższy kod pliku konfiguracji aplikacji usuwa  **\<sampleSection >** sekcji.</span><span class="sxs-lookup"><span data-stu-id="3ad0c-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="3ad0c-125">Po usunięciu aplikacji nie można pobrać ustawień w  **\<sampleSection >**.</span><span class="sxs-lookup"><span data-stu-id="3ad0c-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="3ad0c-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3ad0c-126">Configuration file</span></span>

<span data-ttu-id="3ad0c-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3ad0c-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ad0c-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ad0c-128">See also</span></span>

- [<span data-ttu-id="3ad0c-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ad0c-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
