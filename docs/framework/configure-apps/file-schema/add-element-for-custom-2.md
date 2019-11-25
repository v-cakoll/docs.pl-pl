---
title: element <add> dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac07fc9ba6f030209a5e0d0160689fab95bc1b4a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088762"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="faf88-102">\<dodać elementu > dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="faf88-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="faf88-103">Dodaje niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="faf88-103">Adds custom application settings.</span></span> <span data-ttu-id="faf88-104">Każdy **\<Dodaj tag >** zawiera parę klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="faf88-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="faf88-105">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="faf88-105">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="faf88-106">&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)</span><span class="sxs-lookup"><span data-stu-id="faf88-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)</span></span>\
<span data-ttu-id="faf88-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**</span><span class="sxs-lookup"><span data-stu-id="faf88-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="faf88-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="faf88-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="faf88-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="faf88-109">Attributes</span></span>

| <span data-ttu-id="faf88-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="faf88-110">Attribute</span></span> | <span data-ttu-id="faf88-111">Opis</span><span class="sxs-lookup"><span data-stu-id="faf88-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="faf88-112">**głównych**</span><span class="sxs-lookup"><span data-stu-id="faf88-112">**key**</span></span>   | <span data-ttu-id="faf88-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="faf88-113">Required attribute.</span></span><br><br><span data-ttu-id="faf88-114">Określa nazwę ustawienia.</span><span class="sxs-lookup"><span data-stu-id="faf88-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="faf88-115">**value**</span><span class="sxs-lookup"><span data-stu-id="faf88-115">**value**</span></span> | <span data-ttu-id="faf88-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="faf88-116">Required attribute.</span></span><br><br><span data-ttu-id="faf88-117">Określa wartość ustawienia.</span><span class="sxs-lookup"><span data-stu-id="faf88-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="faf88-118">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="faf88-118">Parent element</span></span>

| <span data-ttu-id="faf88-119">Element</span><span class="sxs-lookup"><span data-stu-id="faf88-119">Element</span></span> | <span data-ttu-id="faf88-120">Opis</span><span class="sxs-lookup"><span data-stu-id="faf88-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="faf88-121"> **\<sectionname >** Postaci</span><span class="sxs-lookup"><span data-stu-id="faf88-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="faf88-122">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają klas <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="faf88-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="faf88-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="faf88-123">Child elements</span></span>

<span data-ttu-id="faf88-124">Brak</span><span class="sxs-lookup"><span data-stu-id="faf88-124">None</span></span>

## <a name="example"></a><span data-ttu-id="faf88-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="faf88-125">Example</span></span>

<span data-ttu-id="faf88-126">Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracji niestandardowej i użyć **\<dodaj >** elementu, aby umieścić ustawienia w sekcji:</span><span class="sxs-lookup"><span data-stu-id="faf88-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="faf88-127">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="faf88-127">Configuration file</span></span>

<span data-ttu-id="faf88-128">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="faf88-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="faf88-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faf88-129">See also</span></span>

- [<span data-ttu-id="faf88-130">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="faf88-130">Configuration file schema for the .NET Framework</span></span>](index.md)
