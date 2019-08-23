---
title: <clear>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c06fca8b83638fb47bedb21863cb9b200cd211f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927729"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="8c343-102">\<Wyczyść element > dla \<configSections ></span><span class="sxs-lookup"><span data-stu-id="8c343-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="8c343-103">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="8c343-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="8c343-104">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8c343-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="8c343-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="8c343-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="8c343-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="8c343-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8c343-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c343-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="8c343-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8c343-108">Attribute</span></span>

|           | <span data-ttu-id="8c343-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8c343-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="8c343-110">**name**</span><span class="sxs-lookup"><span data-stu-id="8c343-110">**name**</span></span>  | <span data-ttu-id="8c343-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8c343-111">Required attribute.</span></span><br><br><span data-ttu-id="8c343-112">Określa nazwę sekcji lub grupy sekcji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="8c343-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="8c343-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="8c343-113">Parent element</span></span>

|     | <span data-ttu-id="8c343-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8c343-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8c343-115">configSections, element >  **\<** </span><span class="sxs-lookup"><span data-stu-id="8c343-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="8c343-116">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8c343-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8c343-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8c343-117">Child elements</span></span>

<span data-ttu-id="8c343-118">Brak</span><span class="sxs-lookup"><span data-stu-id="8c343-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="8c343-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c343-119">Remarks</span></span>

<span data-ttu-id="8c343-120">Element **Clear > usuwa wszystkie sekcje i grupy sekcji z aplikacji, które zostały zdefiniowane wcześniej w bieżącym pliku konfiguracyjnym lub na wyższym poziomie w hierarchii plików konfiguracji. \<**</span><span class="sxs-lookup"><span data-stu-id="8c343-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="8c343-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c343-121">Example</span></span>

<span data-ttu-id="8c343-122">W tym przykładzie zdefiniowano plik konfiguracji komputera i plik konfiguracji aplikacji oraz pokazano,  **\<** jak używać elementu Clear > w pliku konfiguracyjnym aplikacji, aby wyczyścić sekcje wcześniej zdefiniowane w konfiguracji maszyny rozszerzeniem.</span><span class="sxs-lookup"><span data-stu-id="8c343-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="8c343-123">Następujący kod pliku konfiguracji komputera deklaruje dwie sekcje,  **\<sampleSection >** i  **\<anotherSampleSection >** , które są odczytywane przed plikiem konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="8c343-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="8c343-124">Poniższy kod pliku konfiguracji aplikacji czyści wszystkie wcześniej zadeklarowane sekcje.</span><span class="sxs-lookup"><span data-stu-id="8c343-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="8c343-125">Aplikacja nie może używać lub pobrać ustawień w żadnej z sekcji zadeklarowanych w pliku konfiguracji maszyny.</span><span class="sxs-lookup"><span data-stu-id="8c343-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="8c343-126">Może jednak używać ustawień z  **\<anotherSection >**  **\<** , ponieważ znajduje się po elemencie Clear >.</span><span class="sxs-lookup"><span data-stu-id="8c343-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="8c343-127">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8c343-127">Configuration file</span></span>

<span data-ttu-id="8c343-128">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c343-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c343-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c343-129">See also</span></span>

- [<span data-ttu-id="8c343-130">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8c343-130">Configuration file schema for the .NET Framework</span></span>](index.md)
