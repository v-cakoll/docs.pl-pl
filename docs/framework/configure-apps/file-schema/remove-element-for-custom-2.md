---
title: '&lt;Usuń&gt; element NameValueSectionHandler i DictionarySectionHandler'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 61f1c98d3f12b5aa1d25595ca28328602683b073
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="14f07-102">\<Usuń > element NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="14f07-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="14f07-103">Usuwa wcześniej zdefiniowanego ustawienie.</span><span class="sxs-lookup"><span data-stu-id="14f07-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="14f07-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="14f07-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="14f07-105">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="14f07-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="14f07-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="14f07-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="14f07-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="14f07-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="14f07-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="14f07-108">Attribute</span></span>

|           | <span data-ttu-id="14f07-109">Opis</span><span class="sxs-lookup"><span data-stu-id="14f07-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="14f07-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="14f07-110">**key**</span></span>   | <span data-ttu-id="14f07-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="14f07-111">Required attribute.</span></span><br><br><span data-ttu-id="14f07-112">Określa nazwę ustawienia do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="14f07-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="14f07-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="14f07-113">Parent element</span></span>

| <span data-ttu-id="14f07-114">Element</span><span class="sxs-lookup"><span data-stu-id="14f07-114">Element</span></span> | <span data-ttu-id="14f07-115">Opis</span><span class="sxs-lookup"><span data-stu-id="14f07-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="14f07-116">**\<sectionName >** — Element</span><span class="sxs-lookup"><span data-stu-id="14f07-116">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="14f07-117">Definiuje ustawienia w sekcji Konfiguracja niestandardowa, korzystających z <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="14f07-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="14f07-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="14f07-118">Child elements</span></span>

<span data-ttu-id="14f07-119">Brak</span><span class="sxs-lookup"><span data-stu-id="14f07-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="14f07-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14f07-120">Remarks</span></span>

<span data-ttu-id="14f07-121">Można użyć  **\<Usuń >** elementu do usunięcia ustawień z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="14f07-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="14f07-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="14f07-122">Example</span></span>

<span data-ttu-id="14f07-123">Poniższy przykład przedstawia użycie  **\<Usuń >** elementu w pliku konfiguracji aplikacji, aby usunąć ustawienia wcześniej zdefiniowanej w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="14f07-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="14f07-124">Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<mySection >** i dodaje dwa ustawienia `key1` i `key2`, do niej:</span><span class="sxs-lookup"><span data-stu-id="14f07-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="14f07-125">Poniższy kod pliku konfiguracji aplikacji usuwa `key2` z  **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="14f07-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="14f07-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="14f07-126">Configuration file</span></span>

<span data-ttu-id="14f07-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="14f07-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="14f07-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14f07-128">See also</span></span>

[<span data-ttu-id="14f07-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="14f07-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
