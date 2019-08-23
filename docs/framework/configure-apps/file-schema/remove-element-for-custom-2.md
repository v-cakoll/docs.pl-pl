---
title: <remove>element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd338ff2d613be31ab1524f6baed6107f803a688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920947"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="6007f-102">\<Usuń element > dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="6007f-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="6007f-103">Usuwa poprzednio zdefiniowane ustawienie.</span><span class="sxs-lookup"><span data-stu-id="6007f-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="6007f-104">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6007f-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="6007f-105">&nbsp;&nbsp;[ **\<sekcjaname >** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="6007f-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="6007f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="6007f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6007f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6007f-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="6007f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6007f-108">Attribute</span></span>

|           | <span data-ttu-id="6007f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6007f-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="6007f-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="6007f-110">**key**</span></span>   | <span data-ttu-id="6007f-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6007f-111">Required attribute.</span></span><br><br><span data-ttu-id="6007f-112">Określa nazwę ustawienia do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="6007f-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="6007f-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="6007f-113">Parent element</span></span>

| <span data-ttu-id="6007f-114">Element</span><span class="sxs-lookup"><span data-stu-id="6007f-114">Element</span></span> | <span data-ttu-id="6007f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6007f-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="6007f-116">sekcjaname > element  **\<** </span><span class="sxs-lookup"><span data-stu-id="6007f-116">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="6007f-117">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i. <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="6007f-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6007f-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6007f-118">Child elements</span></span>

<span data-ttu-id="6007f-119">Brak</span><span class="sxs-lookup"><span data-stu-id="6007f-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="6007f-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6007f-120">Remarks</span></span>

<span data-ttu-id="6007f-121">Aby usunąć ustawienia z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji, można użyć  **\<elementu Usuń >** .</span><span class="sxs-lookup"><span data-stu-id="6007f-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="6007f-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="6007f-122">Example</span></span>

<span data-ttu-id="6007f-123">Poniższy przykład pokazuje,  **\<** jak używać elementu Remove > w pliku konfiguracyjnym aplikacji, aby usunąć ustawienia zdefiniowane wcześniej w pliku konfiguracji maszyny.</span><span class="sxs-lookup"><span data-stu-id="6007f-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="6007f-124">Poniższy kod pliku konfiguracji komputera deklaruje sekcję  **\<>** i `key1` dodaje dwa ustawienia i `key2`, do:</span><span class="sxs-lookup"><span data-stu-id="6007f-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="6007f-125">Następujący kod pliku konfiguracji aplikacji usuwa `key2` ustawienie z  **\<sekcji >** :</span><span class="sxs-lookup"><span data-stu-id="6007f-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="6007f-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6007f-126">Configuration file</span></span>

<span data-ttu-id="6007f-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6007f-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6007f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6007f-128">See also</span></span>

- [<span data-ttu-id="6007f-129">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6007f-129">Configuration file schema for the .NET Framework</span></span>](index.md)
