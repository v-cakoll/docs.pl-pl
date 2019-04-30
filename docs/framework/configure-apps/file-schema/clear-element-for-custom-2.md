---
title: <clear> element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ad3ac93b2a7f92cd33787620fc0caa2b632aa072
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705366"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="77321-102">\<Wyczyść >, element dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="77321-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="77321-103">Czyści wszystkie wcześniej zdefiniowane ustawienia w sekcji.</span><span class="sxs-lookup"><span data-stu-id="77321-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="77321-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="77321-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="77321-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="77321-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="77321-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="77321-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="77321-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="77321-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="77321-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="77321-108">Attributes</span></span>

<span data-ttu-id="77321-109">Brak</span><span class="sxs-lookup"><span data-stu-id="77321-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="77321-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="77321-110">Parent element</span></span>

|     | <span data-ttu-id="77321-111">Opis</span><span class="sxs-lookup"><span data-stu-id="77321-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="77321-112">**\<parametrami sectionName >** — Element</span><span class="sxs-lookup"><span data-stu-id="77321-112">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="77321-113">Definiuje ustawienia powiązane z sekcji konfiguracji niestandardowej, korzystających z <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="77321-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="77321-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="77321-114">Child elements</span></span>

<span data-ttu-id="77321-115">Brak</span><span class="sxs-lookup"><span data-stu-id="77321-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="77321-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77321-116">Remarks</span></span>

<span data-ttu-id="77321-117">Możesz użyć  **\<Wyczyść >** elementu do usunięcia wszystkich ustawień z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="77321-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="77321-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="77321-118">Example</span></span>

<span data-ttu-id="77321-119">W tym przykładzie definiuje plik konfiguracji i pliku konfiguracji aplikacji i przedstawia sposób użycia  **\<Wyczyść >** elementu w pliku konfiguracyjnym aplikacji, aby wyczyścić wcześniej zdefiniowane w sekcji plik konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="77321-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="77321-120">Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="77321-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="77321-121">Poniższy kod pliku konfiguracji aplikacji spowoduje usunięcie wszystkich ustawień z  **\<mySection >**.</span><span class="sxs-lookup"><span data-stu-id="77321-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="77321-122">Aplikacja nie może pobrać dowolne z ustawień, które zostały zadeklarowane w w  **\<mySection >** sekcję pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="77321-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="77321-123">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="77321-123">Configuration file</span></span>

<span data-ttu-id="77321-124">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="77321-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="77321-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77321-125">See also</span></span>

- [<span data-ttu-id="77321-126">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="77321-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
