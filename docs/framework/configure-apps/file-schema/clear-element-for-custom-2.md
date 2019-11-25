---
title: element <clear> dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fff5a5c2a523480f2eaebb127ec98ff6e9908acf
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088714"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="e6b57-102">\<Wyczyść element > dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="e6b57-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="e6b57-103">Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji.</span><span class="sxs-lookup"><span data-stu-id="e6b57-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="e6b57-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e6b57-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="e6b57-105">&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)</span><span class="sxs-lookup"><span data-stu-id="e6b57-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)</span></span>\
<span data-ttu-id="e6b57-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="e6b57-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e6b57-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6b57-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="e6b57-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e6b57-108">Attributes</span></span>

<span data-ttu-id="e6b57-109">Brak</span><span class="sxs-lookup"><span data-stu-id="e6b57-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="e6b57-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="e6b57-110">Parent element</span></span>

|     | <span data-ttu-id="e6b57-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e6b57-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="e6b57-112"> **\<sectionname >** Postaci</span><span class="sxs-lookup"><span data-stu-id="e6b57-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="e6b57-113">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają klas <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="e6b57-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e6b57-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e6b57-114">Child elements</span></span>

<span data-ttu-id="e6b57-115">Brak</span><span class="sxs-lookup"><span data-stu-id="e6b57-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="e6b57-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6b57-116">Remarks</span></span>

<span data-ttu-id="e6b57-117">Można użyć elementu **\<clear >** , aby usunąć wszystkie ustawienia z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e6b57-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="e6b57-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6b57-118">Example</span></span>

<span data-ttu-id="e6b57-119">Ten przykład definiuje plik konfiguracji komputera i plik konfiguracji aplikacji oraz pokazuje, jak używać **\<wyczyść >** elementu w pliku konfiguracyjnym aplikacji, aby wyczyścić sekcje wcześniej zdefiniowane w pliku konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="e6b57-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="e6b57-120">Następujący kod pliku konfiguracji komputera deklaruje sekcję **\<sekcji >** :</span><span class="sxs-lookup"><span data-stu-id="e6b57-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="e6b57-121">Następujący kod pliku konfiguracyjnego aplikacji usuwa wszystkie ustawienia z **\<sekcji >** .</span><span class="sxs-lookup"><span data-stu-id="e6b57-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="e6b57-122">Aplikacja nie może pobrać z ustawień, które zostały zadeklarowane w sekcji **\<** sekcji w pliku konfiguracji maszyny.</span><span class="sxs-lookup"><span data-stu-id="e6b57-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="e6b57-123">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e6b57-123">Configuration file</span></span>

<span data-ttu-id="e6b57-124">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e6b57-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6b57-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6b57-125">See also</span></span>

- [<span data-ttu-id="e6b57-126">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e6b57-126">Configuration file schema for the .NET Framework</span></span>](index.md)
