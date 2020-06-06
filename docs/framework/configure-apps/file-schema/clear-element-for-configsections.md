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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155430"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="906ee-102">\<clear>, element dla \<configSections></span><span class="sxs-lookup"><span data-stu-id="906ee-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="906ee-103">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="906ee-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="906ee-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="906ee-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="906ee-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="906ee-105">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="906ee-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="906ee-106">Attribute</span></span>

|           | <span data-ttu-id="906ee-107">Opis</span><span class="sxs-lookup"><span data-stu-id="906ee-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="906ee-108">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="906ee-108">**name**</span></span>  | <span data-ttu-id="906ee-109">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="906ee-109">Required attribute.</span></span><br><br><span data-ttu-id="906ee-110">Określa nazwę sekcji lub grupy sekcji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="906ee-110">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="906ee-111">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="906ee-111">Parent element</span></span>

|     | <span data-ttu-id="906ee-112">Opis</span><span class="sxs-lookup"><span data-stu-id="906ee-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="906ee-113">**\<configSections>** Postaci</span><span class="sxs-lookup"><span data-stu-id="906ee-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="906ee-114">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="906ee-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="906ee-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="906ee-115">Child elements</span></span>

<span data-ttu-id="906ee-116">Brak</span><span class="sxs-lookup"><span data-stu-id="906ee-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="906ee-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="906ee-117">Remarks</span></span>

<span data-ttu-id="906ee-118">**\<clear>** Element usuwa wszystkie sekcje i grupy sekcji z aplikacji, które zostały zdefiniowane wcześniej w bieżącym pliku konfiguracyjnym lub na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="906ee-118">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="906ee-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="906ee-119">Example</span></span>

<span data-ttu-id="906ee-120">Ten przykład definiuje plik konfiguracji komputera i plik konfiguracji aplikacji oraz pokazuje, jak używać **\<clear>** elementu w pliku konfiguracyjnym aplikacji do czyszczenia sekcji wcześniej zdefiniowanych w pliku konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="906ee-120">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="906ee-121">Następujący kod pliku konfiguracji komputera deklaruje dwie sekcje **\<sampleSection>** i **\<anotherSampleSection>** , które są odczytywane przed plikiem konfiguracyjnym aplikacji:</span><span class="sxs-lookup"><span data-stu-id="906ee-121">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="906ee-122">Poniższy kod pliku konfiguracji aplikacji czyści wszystkie wcześniej zadeklarowane sekcje.</span><span class="sxs-lookup"><span data-stu-id="906ee-122">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="906ee-123">Aplikacja nie może używać lub pobrać ustawień w żadnej z sekcji zadeklarowanych w pliku konfiguracji maszyny.</span><span class="sxs-lookup"><span data-stu-id="906ee-123">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="906ee-124">Może jednak używać ustawień z **\<anotherSection>** , ponieważ znajduje się po **\<clear>** elemencie.</span><span class="sxs-lookup"><span data-stu-id="906ee-124">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="906ee-125">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="906ee-125">Configuration file</span></span>

<span data-ttu-id="906ee-126">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="906ee-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="906ee-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="906ee-127">See also</span></span>

- [<span data-ttu-id="906ee-128">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="906ee-128">Configuration file schema for the .NET Framework</span></span>](index.md)
