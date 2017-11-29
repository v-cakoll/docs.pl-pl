---
title: "&lt;Wyczyść&gt; element NameValueSectionHandler i DictionarySectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e91c3d9693cf656a8c56c82d1997f74c2b3d64c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="4bcb8-102">\<Wyczyść > element NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="4bcb8-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="4bcb8-103">Czyści wszystkie ustawienia zdefiniowane w sekcji.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="4bcb8-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4bcb8-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="4bcb8-105">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="4bcb8-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="4bcb8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="4bcb8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4bcb8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bcb8-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="4bcb8-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4bcb8-108">Attributes</span></span>

<span data-ttu-id="4bcb8-109">Brak</span><span class="sxs-lookup"><span data-stu-id="4bcb8-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="4bcb8-110">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="4bcb8-110">Parent element</span></span>

|     | <span data-ttu-id="4bcb8-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4bcb8-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="4bcb8-112">**\<sectionName >** — Element</span><span class="sxs-lookup"><span data-stu-id="4bcb8-112">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="4bcb8-113">Definiuje ustawienia w sekcji Konfiguracja niestandardowa, korzystających z <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4bcb8-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4bcb8-114">Child elements</span></span>

<span data-ttu-id="4bcb8-115">Brak</span><span class="sxs-lookup"><span data-stu-id="4bcb8-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="4bcb8-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bcb8-116">Remarks</span></span>

<span data-ttu-id="4bcb8-117">Można użyć  **\<Wyczyść >** elementu do usunięcia wszystkich ustawień z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="4bcb8-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bcb8-118">Example</span></span>

<span data-ttu-id="4bcb8-119">W tym przykładzie definiuje plik konfiguracji maszyny i pliku konfiguracji aplikacji i przedstawia sposób użycia  **\<Wyczyść >** elementu w pliku konfiguracji aplikacji, aby wyczyścić wcześniej zdefiniowane w sekcji plik konfiguracji maszyny.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="4bcb8-120">Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="4bcb8-121">Poniższy kod pliku konfiguracji aplikacji spowoduje usunięcie wszystkich ustawień z  **\<mySection >**.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="4bcb8-122">Aplikacja nie może pobrać ustawienia, które zostały zadeklarowane w w  **\<mySection >** sekcji pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="4bcb8-123">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4bcb8-123">Configuration file</span></span>

<span data-ttu-id="4bcb8-124">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bcb8-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bcb8-125">See also</span></span>

[<span data-ttu-id="4bcb8-126">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4bcb8-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
