---
title: '&lt;Dodaj&gt; element NameValueSectionHandler i DictionarySectionHandler'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
ms.openlocfilehash: aeb3e3a4be201369ca2df8d231498dd2400d3c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="39e66-102">\<Dodaj > element NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="39e66-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="39e66-103">Dodaje ustawienia aplikacji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="39e66-103">Adds custom application settings.</span></span> <span data-ttu-id="39e66-104">Każdy  **\<Dodaj >** tag zawiera pary klucza/wartości.</span><span class="sxs-lookup"><span data-stu-id="39e66-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="39e66-105">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="39e66-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="39e66-106">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="39e66-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="39e66-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="39e66-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="39e66-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="39e66-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="39e66-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39e66-109">Attributes</span></span>

| <span data-ttu-id="39e66-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="39e66-110">Attribute</span></span> | <span data-ttu-id="39e66-111">Opis</span><span class="sxs-lookup"><span data-stu-id="39e66-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="39e66-112">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="39e66-112">**key**</span></span>   | <span data-ttu-id="39e66-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="39e66-113">Required attribute.</span></span><br><br><span data-ttu-id="39e66-114">Określa nazwę ustawienia.</span><span class="sxs-lookup"><span data-stu-id="39e66-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="39e66-115">**value**</span><span class="sxs-lookup"><span data-stu-id="39e66-115">**value**</span></span> | <span data-ttu-id="39e66-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="39e66-116">Required attribute.</span></span><br><br><span data-ttu-id="39e66-117">Określa wartość ustawienia.</span><span class="sxs-lookup"><span data-stu-id="39e66-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="39e66-118">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="39e66-118">Parent element</span></span>

| <span data-ttu-id="39e66-119">Element</span><span class="sxs-lookup"><span data-stu-id="39e66-119">Element</span></span> | <span data-ttu-id="39e66-120">Opis</span><span class="sxs-lookup"><span data-stu-id="39e66-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="39e66-121">**\<sectionName >** — Element</span><span class="sxs-lookup"><span data-stu-id="39e66-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="39e66-122">Definiuje ustawienia w sekcji Konfiguracja niestandardowa, korzystających z <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="39e66-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="39e66-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39e66-123">Child elements</span></span>

<span data-ttu-id="39e66-124">Brak</span><span class="sxs-lookup"><span data-stu-id="39e66-124">None</span></span>

## <a name="example"></a><span data-ttu-id="39e66-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="39e66-125">Example</span></span>

<span data-ttu-id="39e66-126">Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracji niestandardowej, a następnie użyć  **\<Dodaj >** elementu, aby umieścić ustawienia w sekcji:</span><span class="sxs-lookup"><span data-stu-id="39e66-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="39e66-127">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="39e66-127">Configuration file</span></span>

<span data-ttu-id="39e66-128">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="39e66-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="39e66-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39e66-129">See also</span></span>

[<span data-ttu-id="39e66-130">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="39e66-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
