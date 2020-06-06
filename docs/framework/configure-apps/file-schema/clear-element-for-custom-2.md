---
title: <clear>element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: f6d860f35d22002030ffa3d09dd0d8a96116bf5e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214745"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="0f398-102">\<clear>element dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="0f398-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="0f398-103">Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji.</span><span class="sxs-lookup"><span data-stu-id="0f398-103">Clears all previously defined settings in a section.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="0f398-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f398-104">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="0f398-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0f398-105">Attributes</span></span>

<span data-ttu-id="0f398-106">Brak</span><span class="sxs-lookup"><span data-stu-id="0f398-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="0f398-107">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="0f398-107">Parent element</span></span>

|     | <span data-ttu-id="0f398-108">Opis</span><span class="sxs-lookup"><span data-stu-id="0f398-108">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="0f398-109">**\<sectionName>** Postaci</span><span class="sxs-lookup"><span data-stu-id="0f398-109">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="0f398-110">Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="0f398-110">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0f398-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0f398-111">Child elements</span></span>

<span data-ttu-id="0f398-112">Brak</span><span class="sxs-lookup"><span data-stu-id="0f398-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="0f398-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f398-113">Remarks</span></span>

<span data-ttu-id="0f398-114">Można użyć elementu, **\<clear>** Aby usunąć wszystkie ustawienia z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0f398-114">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="0f398-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f398-115">Example</span></span>

<span data-ttu-id="0f398-116">Ten przykład definiuje plik konfiguracji komputera i plik konfiguracji aplikacji oraz pokazuje, jak używać **\<clear>** elementu w pliku konfiguracyjnym aplikacji do czyszczenia sekcji wcześniej zdefiniowanych w pliku konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="0f398-116">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="0f398-117">Następujący kod pliku konfiguracji komputera deklaruje sekcję **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="0f398-117">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="0f398-118">Poniższy kod pliku konfiguracji aplikacji usuwa wszystkie ustawienia z programu **\<mySection>** .</span><span class="sxs-lookup"><span data-stu-id="0f398-118">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="0f398-119">Aplikacja nie może pobrać z ustawień, które zostały zadeklarowane w **\<mySection>** sekcji w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="0f398-119">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="0f398-120">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0f398-120">Configuration file</span></span>

<span data-ttu-id="0f398-121">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f398-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f398-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f398-122">See also</span></span>

- [<span data-ttu-id="0f398-123">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0f398-123">Configuration file schema for the .NET Framework</span></span>](index.md)
