---
title: <clear>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155430"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="d3ba0-102">\<klarowny element> \<dla> konfisekcyjnych</span><span class="sxs-lookup"><span data-stu-id="d3ba0-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="d3ba0-103">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="d3ba0-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="d3ba0-104">&nbsp; &nbsp; &nbsp; &nbsp; \*\* \<\*\* [\*\* \<konfiguracja>\*\*](configuration-element.md) &nbsp; &nbsp; [\*\* \<konfiguracjeSekcje>\*\*](configsections-element-for-configuration.md) jasne></span><span class="sxs-lookup"><span data-stu-id="d3ba0-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d3ba0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3ba0-105">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="d3ba0-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d3ba0-106">Attribute</span></span>

|           | <span data-ttu-id="d3ba0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d3ba0-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d3ba0-108">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="d3ba0-108">**name**</span></span>  | <span data-ttu-id="d3ba0-109">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d3ba0-109">Required attribute.</span></span><br><br><span data-ttu-id="d3ba0-110">Określa nazwę sekcji lub grupy sekcji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="d3ba0-110">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="d3ba0-111">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="d3ba0-111">Parent element</span></span>

|     | <span data-ttu-id="d3ba0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d3ba0-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d3ba0-113">\*\* \<configSekcje>\*\* Element</span><span class="sxs-lookup"><span data-stu-id="d3ba0-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="d3ba0-114">Zawiera sekcje konfiguracji i deklaracje obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="d3ba0-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d3ba0-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d3ba0-115">Child elements</span></span>

<span data-ttu-id="d3ba0-116">Brak</span><span class="sxs-lookup"><span data-stu-id="d3ba0-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="d3ba0-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3ba0-117">Remarks</span></span>

<span data-ttu-id="d3ba0-118">Element \*\* \<>wyczyść\*\* usuwa wszystkie sekcje i grupy sekcji z aplikacji, które zostały zdefiniowane wcześniej w bieżącym pliku konfiguracyjnym lub na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d3ba0-118">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="d3ba0-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3ba0-119">Example</span></span>

<span data-ttu-id="d3ba0-120">W tym przykładzie definiuje plik konfiguracji komputera i plik konfiguracji aplikacji i pokazuje, jak używać \*\* \<elementu clear>\*\* w pliku konfiguracji aplikacji, aby wyczyścić sekcje wcześniej zdefiniowane w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="d3ba0-120">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="d3ba0-121">Następujący kod pliku konfiguracji komputera deklaruje dwie \*\* \<sekcje: sampleSekcja>\*\* i \*\* \<innySampleSection>\*\*, które są odczytywane przed plikiem konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d3ba0-121">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="d3ba0-122">Poniższy kod pliku konfiguracji aplikacji czyści wszystkie wcześniej zadeklarowane sekcje.</span><span class="sxs-lookup"><span data-stu-id="d3ba0-122">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="d3ba0-123">Aplikacja nie może używać ani pobierać ustawień w żadnej z sekcji, które zostały zadeklarowane w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="d3ba0-123">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="d3ba0-124">Jednak można użyć ustawień z \*\* \<innegoSekcja>,\*\* ponieważ pochodzi po \*\* \<element>jasne.\*\*</span><span class="sxs-lookup"><span data-stu-id="d3ba0-124">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="d3ba0-125">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d3ba0-125">Configuration file</span></span>

<span data-ttu-id="d3ba0-126">Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d3ba0-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3ba0-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3ba0-127">See also</span></span>

- [<span data-ttu-id="d3ba0-128">Schemat pliku konfiguracyjnego programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d3ba0-128">Configuration file schema for the .NET Framework</span></span>](index.md)
