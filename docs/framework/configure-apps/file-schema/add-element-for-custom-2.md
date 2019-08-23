---
title: <add>element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: ec6d5045580e887de5f05a05c8f39fa62c6e3f2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921331"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="d95a9-102">\<Dodaj element > dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="d95a9-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="d95a9-103">Dodaje niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d95a9-103">Adds custom application settings.</span></span> <span data-ttu-id="d95a9-104">Każdy tag Add > zawiera parę klucz/wartość.  **\<**</span><span class="sxs-lookup"><span data-stu-id="d95a9-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="d95a9-105">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d95a9-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="d95a9-106">&nbsp;&nbsp;[ **\<sekcjaname >** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="d95a9-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="d95a9-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="d95a9-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d95a9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d95a9-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="d95a9-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d95a9-109">Attributes</span></span>

| <span data-ttu-id="d95a9-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d95a9-110">Attribute</span></span> | <span data-ttu-id="d95a9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d95a9-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d95a9-112">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="d95a9-112">**key**</span></span>   | <span data-ttu-id="d95a9-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d95a9-113">Required attribute.</span></span><br><br><span data-ttu-id="d95a9-114">Określa nazwę ustawienia.</span><span class="sxs-lookup"><span data-stu-id="d95a9-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="d95a9-115">**value**</span><span class="sxs-lookup"><span data-stu-id="d95a9-115">**value**</span></span> | <span data-ttu-id="d95a9-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d95a9-116">Required attribute.</span></span><br><br><span data-ttu-id="d95a9-117">Określa wartość ustawienia.</span><span class="sxs-lookup"><span data-stu-id="d95a9-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="d95a9-118">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="d95a9-118">Parent element</span></span>

| <span data-ttu-id="d95a9-119">Element</span><span class="sxs-lookup"><span data-stu-id="d95a9-119">Element</span></span> | <span data-ttu-id="d95a9-120">Opis</span><span class="sxs-lookup"><span data-stu-id="d95a9-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="d95a9-121">sekcjaname > element  **\<** </span><span class="sxs-lookup"><span data-stu-id="d95a9-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="d95a9-122">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i. <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="d95a9-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d95a9-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d95a9-123">Child elements</span></span>

<span data-ttu-id="d95a9-124">Brak</span><span class="sxs-lookup"><span data-stu-id="d95a9-124">None</span></span>

## <a name="example"></a><span data-ttu-id="d95a9-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="d95a9-125">Example</span></span>

<span data-ttu-id="d95a9-126">Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracji niestandardowej i użyć  **\<elementu Dodaj >** , aby umieścić ustawienia w sekcji:</span><span class="sxs-lookup"><span data-stu-id="d95a9-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="d95a9-127">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d95a9-127">Configuration file</span></span>

<span data-ttu-id="d95a9-128">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d95a9-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d95a9-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d95a9-129">See also</span></span>

- [<span data-ttu-id="d95a9-130">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d95a9-130">Configuration file schema for the .NET Framework</span></span>](index.md)
