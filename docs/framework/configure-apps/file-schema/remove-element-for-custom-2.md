---
title: "&lt;Usuń&gt; element NameValueSectionHandler i DictionarySectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: decf0ca5f9f743a2a2884c06777b7ee9d6d6a8ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="9323d-102">\<Usuń > element NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="9323d-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="9323d-103">Usuwa wcześniej zdefiniowanego ustawienie.</span><span class="sxs-lookup"><span data-stu-id="9323d-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="9323d-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9323d-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="9323d-105">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="9323d-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="9323d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="9323d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9323d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9323d-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="9323d-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9323d-108">Attribute</span></span>

|           | <span data-ttu-id="9323d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9323d-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="9323d-110">**klucz**</span><span class="sxs-lookup"><span data-stu-id="9323d-110">**key**</span></span>   | <span data-ttu-id="9323d-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9323d-111">Required attribute.</span></span><br><br><span data-ttu-id="9323d-112">Określa nazwę ustawienia do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="9323d-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="9323d-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="9323d-113">Parent element</span></span>

| <span data-ttu-id="9323d-114">Element</span><span class="sxs-lookup"><span data-stu-id="9323d-114">Element</span></span> | <span data-ttu-id="9323d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9323d-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="9323d-116">**\<sectionName >** — Element</span><span class="sxs-lookup"><span data-stu-id="9323d-116">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="9323d-117">Definiuje ustawienia w sekcji Konfiguracja niestandardowa, korzystających z <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="9323d-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9323d-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9323d-118">Child elements</span></span>

<span data-ttu-id="9323d-119">Brak</span><span class="sxs-lookup"><span data-stu-id="9323d-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="9323d-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9323d-120">Remarks</span></span>

<span data-ttu-id="9323d-121">Można użyć  **\<Usuń >** elementu do usunięcia ustawień z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9323d-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="9323d-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="9323d-122">Example</span></span>

<span data-ttu-id="9323d-123">Poniższy przykład przedstawia użycie  **\<Usuń >** elementu w pliku konfiguracji aplikacji, aby usunąć ustawienia wcześniej zdefiniowanej w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="9323d-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="9323d-124">Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<mySection >** i dodaje dwa ustawienia `key1` i `key2`, do niej:</span><span class="sxs-lookup"><span data-stu-id="9323d-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="9323d-125">Poniższy kod pliku konfiguracji aplikacji usuwa `key2` z  **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="9323d-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="9323d-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9323d-126">Configuration file</span></span>

<span data-ttu-id="9323d-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9323d-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="9323d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9323d-128">See also</span></span>

[<span data-ttu-id="9323d-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9323d-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
