---
title: element <remove> dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214754"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="fb86b-102">\<usunąć elementu > dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="fb86b-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="fb86b-103">Usuwa poprzednio zdefiniowane ustawienie.</span><span class="sxs-lookup"><span data-stu-id="fb86b-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="fb86b-104">[ **\<> konfiguracji**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb86b-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="fb86b-105">&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)</span><span class="sxs-lookup"><span data-stu-id="fb86b-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)</span></span>\
<span data-ttu-id="fb86b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<usuń >**</span><span class="sxs-lookup"><span data-stu-id="fb86b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fb86b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb86b-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="fb86b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fb86b-108">Attribute</span></span>

|           | <span data-ttu-id="fb86b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fb86b-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="fb86b-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="fb86b-110">**key**</span></span>   | <span data-ttu-id="fb86b-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fb86b-111">Required attribute.</span></span><br><br><span data-ttu-id="fb86b-112">Określa nazwę ustawienia do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="fb86b-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="fb86b-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="fb86b-113">Parent element</span></span>

| <span data-ttu-id="fb86b-114">Element</span><span class="sxs-lookup"><span data-stu-id="fb86b-114">Element</span></span> | <span data-ttu-id="fb86b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="fb86b-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="fb86b-116"> **\<sectionname >** Postaci</span><span class="sxs-lookup"><span data-stu-id="fb86b-116">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="fb86b-117">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają klas <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="fb86b-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="fb86b-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fb86b-118">Child elements</span></span>

<span data-ttu-id="fb86b-119">None</span><span class="sxs-lookup"><span data-stu-id="fb86b-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="fb86b-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb86b-120">Remarks</span></span>

<span data-ttu-id="fb86b-121">Można użyć elementu **\<remove >** , aby usunąć ustawienia z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fb86b-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="fb86b-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb86b-122">Example</span></span>

<span data-ttu-id="fb86b-123">W poniższym przykładzie pokazano, jak za pomocą **\<usunąć >** elementu w pliku konfiguracyjnym aplikacji usunąć ustawienia zdefiniowane wcześniej w pliku konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="fb86b-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="fb86b-124">Poniższy kod pliku konfiguracji komputera deklaruje sekcję **\<sekcji >** i dodaje do niej dwa ustawienia, `key1` i `key2`:</span><span class="sxs-lookup"><span data-stu-id="fb86b-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="fb86b-125">Następujący kod pliku konfiguracji aplikacji usuwa ustawienie `key2` z **\<sekcji >** :</span><span class="sxs-lookup"><span data-stu-id="fb86b-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="fb86b-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fb86b-126">Configuration file</span></span>

<span data-ttu-id="fb86b-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb86b-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb86b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb86b-128">See also</span></span>

- [<span data-ttu-id="fb86b-129">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb86b-129">Configuration file schema for the .NET Framework</span></span>](index.md)
