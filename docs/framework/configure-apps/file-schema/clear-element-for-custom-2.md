---
title: <clear>element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: fbb689db4abc5d59729d9a4d9807a02a0983d40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927713"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="ee867-102">\<Wyczyść element > dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="ee867-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="ee867-103">Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji.</span><span class="sxs-lookup"><span data-stu-id="ee867-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="ee867-104">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ee867-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="ee867-105">&nbsp;&nbsp;[ **\<sekcjaname >** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="ee867-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="ee867-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="ee867-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ee867-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee867-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="ee867-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ee867-108">Attributes</span></span>

<span data-ttu-id="ee867-109">Brak</span><span class="sxs-lookup"><span data-stu-id="ee867-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="ee867-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="ee867-110">Parent element</span></span>

|     | <span data-ttu-id="ee867-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ee867-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="ee867-112">sekcjaname > element  **\<** </span><span class="sxs-lookup"><span data-stu-id="ee867-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="ee867-113">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i. <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="ee867-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ee867-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ee867-114">Child elements</span></span>

<span data-ttu-id="ee867-115">Brak</span><span class="sxs-lookup"><span data-stu-id="ee867-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="ee867-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee867-116">Remarks</span></span>

<span data-ttu-id="ee867-117">Można użyć elementu  **\<Clear >** , aby usunąć wszystkie ustawienia z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ee867-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="ee867-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee867-118">Example</span></span>

<span data-ttu-id="ee867-119">W tym przykładzie zdefiniowano plik konfiguracji komputera i plik konfiguracji aplikacji oraz pokazano,  **\<** jak używać elementu Clear > w pliku konfiguracyjnym aplikacji, aby wyczyścić sekcje wcześniej zdefiniowane w konfiguracji maszyny rozszerzeniem.</span><span class="sxs-lookup"><span data-stu-id="ee867-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="ee867-120">Następujący kod pliku konfiguracji komputera deklaruje sekcję  **\<>** :</span><span class="sxs-lookup"><span data-stu-id="ee867-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="ee867-121">Następujący kod pliku konfiguracji aplikacji usuwa wszystkie ustawienia z  **\<sekcji >** .</span><span class="sxs-lookup"><span data-stu-id="ee867-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="ee867-122">Aplikacja nie może pobrać z ustawień, które zostały zadeklarowane w sekcji  **\<>** w pliku konfiguracji maszyny.</span><span class="sxs-lookup"><span data-stu-id="ee867-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="ee867-123">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ee867-123">Configuration file</span></span>

<span data-ttu-id="ee867-124">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee867-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee867-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee867-125">See also</span></span>

- [<span data-ttu-id="ee867-126">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ee867-126">Configuration file schema for the .NET Framework</span></span>](index.md)
