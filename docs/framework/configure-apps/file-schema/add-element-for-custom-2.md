---
title: <add>element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215439"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="559fb-102">\<add>element dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="559fb-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="559fb-103">Dodaje niestandardowe ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="559fb-103">Adds custom application settings.</span></span> <span data-ttu-id="559fb-104">Każdy **\<add>** tag zawiera parę klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="559fb-104">Each **\<add>** tag contains a key/value pair.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="559fb-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="559fb-105">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="559fb-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="559fb-106">Attributes</span></span>

| <span data-ttu-id="559fb-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="559fb-107">Attribute</span></span> | <span data-ttu-id="559fb-108">Opis</span><span class="sxs-lookup"><span data-stu-id="559fb-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="559fb-109">**głównych**</span><span class="sxs-lookup"><span data-stu-id="559fb-109">**key**</span></span>   | <span data-ttu-id="559fb-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="559fb-110">Required attribute.</span></span><br><br><span data-ttu-id="559fb-111">Określa nazwę ustawienia.</span><span class="sxs-lookup"><span data-stu-id="559fb-111">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="559fb-112">**wartościami**</span><span class="sxs-lookup"><span data-stu-id="559fb-112">**value**</span></span> | <span data-ttu-id="559fb-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="559fb-113">Required attribute.</span></span><br><br><span data-ttu-id="559fb-114">Określa wartość ustawienia.</span><span class="sxs-lookup"><span data-stu-id="559fb-114">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="559fb-115">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="559fb-115">Parent element</span></span>

| <span data-ttu-id="559fb-116">Element</span><span class="sxs-lookup"><span data-stu-id="559fb-116">Element</span></span> | <span data-ttu-id="559fb-117">Opis</span><span class="sxs-lookup"><span data-stu-id="559fb-117">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="559fb-118">**\<sectionName>** Postaci</span><span class="sxs-lookup"><span data-stu-id="559fb-118">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="559fb-119">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="559fb-119">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="559fb-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="559fb-120">Child elements</span></span>

<span data-ttu-id="559fb-121">Brak</span><span class="sxs-lookup"><span data-stu-id="559fb-121">None</span></span>

## <a name="example"></a><span data-ttu-id="559fb-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="559fb-122">Example</span></span>

<span data-ttu-id="559fb-123">Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracji niestandardowej i użyć **\<add>** elementu, aby umieścić ustawienia w sekcji:</span><span class="sxs-lookup"><span data-stu-id="559fb-123">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="559fb-124">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="559fb-124">Configuration file</span></span>

<span data-ttu-id="559fb-125">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="559fb-125">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="559fb-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="559fb-126">See also</span></span>

- [<span data-ttu-id="559fb-127">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="559fb-127">Configuration file schema for the .NET Framework</span></span>](index.md)
