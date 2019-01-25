---
title: '&lt;Wyczyść&gt; element dla NameValueSectionHandler i DictionarySectionHandler'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 55925ee5e9c5a17f14bd199125dbaacbadb9d928
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720944"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="6e6a3-102">\<Wyczyść >, element dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="6e6a3-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="6e6a3-103">Czyści wszystkie wcześniej zdefiniowane ustawienia w sekcji.</span><span class="sxs-lookup"><span data-stu-id="6e6a3-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="6e6a3-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6e6a3-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="6e6a3-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="6e6a3-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="6e6a3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="6e6a3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6e6a3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e6a3-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="6e6a3-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6e6a3-108">Attributes</span></span>

<span data-ttu-id="6e6a3-109">Brak</span><span class="sxs-lookup"><span data-stu-id="6e6a3-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="6e6a3-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="6e6a3-110">Parent element</span></span>

|     | <span data-ttu-id="6e6a3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6e6a3-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="6e6a3-112">**\<parametrami sectionName >** — Element</span><span class="sxs-lookup"><span data-stu-id="6e6a3-112">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="6e6a3-113">Definiuje ustawienia powiązane z sekcji konfiguracji niestandardowej, korzystających z <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="6e6a3-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6e6a3-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6e6a3-114">Child elements</span></span>

<span data-ttu-id="6e6a3-115">Brak</span><span class="sxs-lookup"><span data-stu-id="6e6a3-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="6e6a3-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e6a3-116">Remarks</span></span>

<span data-ttu-id="6e6a3-117">Możesz użyć  **\<Wyczyść >** elementu do usunięcia wszystkich ustawień z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6e6a3-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="6e6a3-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e6a3-118">Example</span></span>

<span data-ttu-id="6e6a3-119">W tym przykładzie definiuje plik konfiguracji i pliku konfiguracji aplikacji i przedstawia sposób użycia  **\<Wyczyść >** elementu w pliku konfiguracyjnym aplikacji, aby wyczyścić wcześniej zdefiniowane w sekcji plik konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="6e6a3-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="6e6a3-120">Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="6e6a3-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="6e6a3-121">Poniższy kod pliku konfiguracji aplikacji spowoduje usunięcie wszystkich ustawień z  **\<mySection >**.</span><span class="sxs-lookup"><span data-stu-id="6e6a3-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="6e6a3-122">Aplikacja nie może pobrać dowolne z ustawień, które zostały zadeklarowane w w  **\<mySection >** sekcję pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="6e6a3-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="6e6a3-123">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6e6a3-123">Configuration file</span></span>

<span data-ttu-id="6e6a3-124">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e6a3-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e6a3-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e6a3-125">See also</span></span>

- [<span data-ttu-id="6e6a3-126">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6e6a3-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
