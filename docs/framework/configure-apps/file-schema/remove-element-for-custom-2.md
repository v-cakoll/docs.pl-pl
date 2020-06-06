---
title: <remove>element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214754"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="95ee8-102">\<remove>element dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="95ee8-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="95ee8-103">Usuwa poprzednio zdefiniowane ustawienie.</span><span class="sxs-lookup"><span data-stu-id="95ee8-103">Removes a previously defined setting.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="95ee8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95ee8-104">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="95ee8-105">Atrybut</span><span class="sxs-lookup"><span data-stu-id="95ee8-105">Attribute</span></span>

|           | <span data-ttu-id="95ee8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="95ee8-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="95ee8-107">**głównych**</span><span class="sxs-lookup"><span data-stu-id="95ee8-107">**key**</span></span>   | <span data-ttu-id="95ee8-108">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="95ee8-108">Required attribute.</span></span><br><br><span data-ttu-id="95ee8-109">Określa nazwę ustawienia do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="95ee8-109">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="95ee8-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="95ee8-110">Parent element</span></span>

| <span data-ttu-id="95ee8-111">Element</span><span class="sxs-lookup"><span data-stu-id="95ee8-111">Element</span></span> | <span data-ttu-id="95ee8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="95ee8-112">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="95ee8-113">**\<sectionName>** Postaci</span><span class="sxs-lookup"><span data-stu-id="95ee8-113">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="95ee8-114">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="95ee8-114">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="95ee8-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="95ee8-115">Child elements</span></span>

<span data-ttu-id="95ee8-116">Brak</span><span class="sxs-lookup"><span data-stu-id="95ee8-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="95ee8-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95ee8-117">Remarks</span></span>

<span data-ttu-id="95ee8-118">Można użyć elementu, **\<remove>** Aby usunąć ustawienia z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="95ee8-118">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="95ee8-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="95ee8-119">Example</span></span>

<span data-ttu-id="95ee8-120">Poniższy przykład pokazuje, jak używać **\<remove>** elementu w pliku konfiguracyjnym aplikacji do usuwania ustawień zdefiniowanych wcześniej w pliku konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="95ee8-120">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="95ee8-121">Poniższy kod pliku konfiguracji komputera deklaruje sekcję **\<mySection>** i dodaje dwa ustawienia `key1` i `key2` , do:</span><span class="sxs-lookup"><span data-stu-id="95ee8-121">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="95ee8-122">Następujący kod pliku konfiguracji aplikacji usuwa `key2` ustawienie z **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="95ee8-122">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="95ee8-123">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="95ee8-123">Configuration file</span></span>

<span data-ttu-id="95ee8-124">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95ee8-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="95ee8-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95ee8-125">See also</span></span>

- [<span data-ttu-id="95ee8-126">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="95ee8-126">Configuration file schema for the .NET Framework</span></span>](index.md)
