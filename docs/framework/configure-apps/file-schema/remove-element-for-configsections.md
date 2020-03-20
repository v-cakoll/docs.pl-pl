---
title: <remove>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154533"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="0104b-102">\<usunąć element> \<dla konfisek></span><span class="sxs-lookup"><span data-stu-id="0104b-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="0104b-103">Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji.</span><span class="sxs-lookup"><span data-stu-id="0104b-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="0104b-104">[**\<>konfiguracyjne**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0104b-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="0104b-105">&nbsp;&nbsp;[**\<>konfiguracyjne**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="0104b-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="0104b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<usuń>**</span><span class="sxs-lookup"><span data-stu-id="0104b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0104b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0104b-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="0104b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0104b-108">Attribute</span></span>

|           | <span data-ttu-id="0104b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0104b-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="0104b-110">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="0104b-110">**name**</span></span>  | <span data-ttu-id="0104b-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0104b-111">Required attribute.</span></span><br><br><span data-ttu-id="0104b-112">Określa nazwę sekcji lub grupy sekcji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="0104b-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="0104b-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="0104b-113">Parent element</span></span>

|     | <span data-ttu-id="0104b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0104b-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0104b-115">\*\* \<configSekcje>\*\* Element</span><span class="sxs-lookup"><span data-stu-id="0104b-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="0104b-116">Zawiera sekcje konfiguracji i deklaracje obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="0104b-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0104b-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0104b-117">Child elements</span></span>

<span data-ttu-id="0104b-118">Brak</span><span class="sxs-lookup"><span data-stu-id="0104b-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="0104b-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0104b-119">Remarks</span></span>

<span data-ttu-id="0104b-120">Można użyć \*\* \<elementu>usuwania,\*\* aby usunąć sekcje i grupy sekcji z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0104b-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="0104b-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="0104b-121">Example</span></span>

<span data-ttu-id="0104b-122">W poniższym przykładzie pokazano, jak użyć elementu \*\* \<>w\*\* pliku konfiguracji aplikacji, aby usunąć sekcję wcześniej zdefiniowaną w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="0104b-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="0104b-123">Następujący kod pliku konfiguracji maszyny deklaruje \*\* \<przykład sekcjiSekcja>: \*\*</span><span class="sxs-lookup"><span data-stu-id="0104b-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="0104b-124">Poniższy kod pliku konfiguracji aplikacji usuwa \*\* \<przykładową sekcję>.\*\*</span><span class="sxs-lookup"><span data-stu-id="0104b-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="0104b-125">Po usunięciu aplikacja nie może pobrać ustawień w \*\* \<próbceSekcja>\*\*.</span><span class="sxs-lookup"><span data-stu-id="0104b-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="0104b-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0104b-126">Configuration file</span></span>

<span data-ttu-id="0104b-127">Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0104b-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="0104b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0104b-128">See also</span></span>

- [<span data-ttu-id="0104b-129">Schemat pliku konfiguracyjnego programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0104b-129">Configuration file schema for the .NET Framework</span></span>](index.md)
