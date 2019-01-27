---
title: '&lt;Wyczyść&gt; elementu &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9439e2ac7634b242c9f847346f7dcf265d6ab419
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678008"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="aaa89-102">\<Wyczyść >, element dla \<configSections ></span><span class="sxs-lookup"><span data-stu-id="aaa89-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="aaa89-103">Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="aaa89-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="aaa89-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aaa89-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="aaa89-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="aaa89-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="aaa89-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="aaa89-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="aaa89-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="aaa89-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="aaa89-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aaa89-108">Attribute</span></span>

|           | <span data-ttu-id="aaa89-109">Opis</span><span class="sxs-lookup"><span data-stu-id="aaa89-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="aaa89-110">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="aaa89-110">**name**</span></span>  | <span data-ttu-id="aaa89-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="aaa89-111">Required attribute.</span></span><br><br><span data-ttu-id="aaa89-112">Określa nazwę sekcji lub grupy sekcji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="aaa89-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="aaa89-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="aaa89-113">Parent element</span></span>

|     | <span data-ttu-id="aaa89-114">Opis</span><span class="sxs-lookup"><span data-stu-id="aaa89-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="aaa89-115">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="aaa89-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="aaa89-116">Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="aaa89-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="aaa89-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aaa89-117">Child elements</span></span>

<span data-ttu-id="aaa89-118">Brak</span><span class="sxs-lookup"><span data-stu-id="aaa89-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="aaa89-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aaa89-119">Remarks</span></span>

<span data-ttu-id="aaa89-120"> *\*\<Wyczyść >** elementu usuwa wszystkie sekcje i grup sekcji z Twojej aplikacji, które zostały wcześniej zdefiniowane w bieżącym pliku konfiguracji lub wyższego poziomu w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="aaa89-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="aaa89-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="aaa89-121">Example</span></span>

<span data-ttu-id="aaa89-122">W tym przykładzie definiuje plik konfiguracji i pliku konfiguracji aplikacji i przedstawia sposób użycia  **\<Wyczyść >** elementu w pliku konfiguracyjnym aplikacji, aby wyczyścić wcześniej zdefiniowane w sekcji plik konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="aaa89-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="aaa89-123">Poniższy kod pliku konfiguracji maszyny deklaruje dwie sekcje  **\<sampleSection >** i  **\<anotherSampleSection >**, które są odczytywane przed zastosowaniem plik konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="aaa89-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="aaa89-124">Poniższy kod pliku konfiguracji aplikacji czyści wszystkie wcześniej zadeklarowanej sekcje.</span><span class="sxs-lookup"><span data-stu-id="aaa89-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="aaa89-125">Aplikacja nie może używać lub pobrać ustawień albo sekcje, które zostały zadeklarowane w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="aaa89-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="aaa89-126">Jednak można użyć ustawień z  **\<anotherSection >** ponieważ pochodzi on po  **\<Wyczyść >** elementu.</span><span class="sxs-lookup"><span data-stu-id="aaa89-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="aaa89-127">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="aaa89-127">Configuration file</span></span>

<span data-ttu-id="aaa89-128">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aaa89-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="aaa89-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aaa89-129">See also</span></span>

- [<span data-ttu-id="aaa89-130">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aaa89-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
