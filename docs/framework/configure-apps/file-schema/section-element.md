---
title: <section>  — element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153736"
---
# <a name="section-element"></a><span data-ttu-id="87550-102">\<element> sekcji</span><span class="sxs-lookup"><span data-stu-id="87550-102">\<section> element</span></span>

<span data-ttu-id="87550-103">Zawiera deklarację sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87550-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="87550-104">[**\<>konfiguracyjne**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="87550-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="87550-105">&nbsp;&nbsp;[**\<>konfiguracyjne**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="87550-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="87550-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<>sekcji**</span><span class="sxs-lookup"><span data-stu-id="87550-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="87550-107">[**\<>konfiguracyjne**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="87550-107">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="87550-108">&nbsp;&nbsp;[**\<>konfiguracyjne**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="87550-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="87550-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGrupa>**](sectiongroup-element-for-configsections.md)</span><span class="sxs-lookup"><span data-stu-id="87550-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>\
<span data-ttu-id="87550-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>sekcji**</span><span class="sxs-lookup"><span data-stu-id="87550-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="87550-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="87550-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="87550-112">Wymagane atrybuty</span><span class="sxs-lookup"><span data-stu-id="87550-112">Required attributes</span></span>

|           | <span data-ttu-id="87550-113">Opis</span><span class="sxs-lookup"><span data-stu-id="87550-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="87550-114">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="87550-114">**name**</span></span>  | <span data-ttu-id="87550-115">Określa nazwę sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87550-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="87550-116">**Typu**</span><span class="sxs-lookup"><span data-stu-id="87550-116">**type**</span></span>  | <span data-ttu-id="87550-117">Określa nazwę klasy obsługi sekcji konfiguracji, która odczytuje sekcję z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87550-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="87550-118">Wartość typu ma składnię "w pełni kwalifikowana sekcja-handler-class-name, simple-assembly-name".</span><span class="sxs-lookup"><span data-stu-id="87550-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="87550-119">Prosta nazwa zestawu to główna nazwa pliku bez rozszerzenia pliku *.dll.*</span><span class="sxs-lookup"><span data-stu-id="87550-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="87550-120">Atrybuty opcjonalne</span><span class="sxs-lookup"><span data-stu-id="87550-120">Optional attributes</span></span>

<span data-ttu-id="87550-121">Następujące atrybuty mają zastosowanie tylko do aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="87550-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="87550-122">System konfiguracji ignoruje te atrybuty dla innych typów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87550-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="87550-123">Opis</span><span class="sxs-lookup"><span data-stu-id="87550-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="87550-124">**zezwalaj NaDefiniowanie**</span><span class="sxs-lookup"><span data-stu-id="87550-124">**allowDefinition**</span></span> | <span data-ttu-id="87550-125">Określa, w którym pliku konfiguracyjnym może być używany sekcja.</span><span class="sxs-lookup"><span data-stu-id="87550-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="87550-126">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="87550-126">Use one of the following values:</span></span><br><br><span data-ttu-id="87550-127">**Wszędzie**</span><span class="sxs-lookup"><span data-stu-id="87550-127">**Everywhere**</span></span><br><span data-ttu-id="87550-128">Umożliwia użycie sekcji w dowolnym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="87550-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="87550-129">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="87550-129">This is the default.</span></span><br><span data-ttu-id="87550-130">**MaszynaOnująca**</span><span class="sxs-lookup"><span data-stu-id="87550-130">**MachineOnly**</span></span><br><span data-ttu-id="87550-131">Umożliwia użycie sekcji tylko w pliku konfiguracyjnym komputera (*Machine.config*).</span><span class="sxs-lookup"><span data-stu-id="87550-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="87550-132">**Machinetoapplication**</span><span class="sxs-lookup"><span data-stu-id="87550-132">**MachineToApplication**</span></span><br><span data-ttu-id="87550-133">Umożliwia użycie sekcji w pliku konfiguracyjnym komputera lub w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87550-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="87550-134">**allowLocation (zezwalajlokalizacja)**</span><span class="sxs-lookup"><span data-stu-id="87550-134">**allowLocation**</span></span>   | <span data-ttu-id="87550-135">Określa, czy sekcja może być używana w \*\* \<>\*\* element lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="87550-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="87550-136">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="87550-136">Use one of the following values:</span></span><br><br><span data-ttu-id="87550-137">**true**</span><span class="sxs-lookup"><span data-stu-id="87550-137">**true**</span></span><br><span data-ttu-id="87550-138">Umożliwia użycie sekcji w obrębie \*\* \<elementu>lokalizacji.\*\*</span><span class="sxs-lookup"><span data-stu-id="87550-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="87550-139">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="87550-139">This is the default.</span></span><br><span data-ttu-id="87550-140">**false**</span><span class="sxs-lookup"><span data-stu-id="87550-140">**false**</span></span><br><span data-ttu-id="87550-141">Nie zezwala na użycie sekcji w obrębie \*\* \<>\*\* elementu lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="87550-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="87550-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87550-142">Parent elements</span></span>

|     | <span data-ttu-id="87550-143">Opis</span><span class="sxs-lookup"><span data-stu-id="87550-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="87550-144">\*\* \<configSekcje>\*\* Element</span><span class="sxs-lookup"><span data-stu-id="87550-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="87550-145">Zawiera sekcje konfiguracji i deklaracje obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="87550-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="87550-146">\*\* \<sectionGrupa>\*\* Element</span><span class="sxs-lookup"><span data-stu-id="87550-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="87550-147">Definiuje obszar nazw dla sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87550-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="87550-148">Element \*\* \<>sekcji\*\* jest elementem podrzędnym \*\* \<konfisycji>\*\* lub \*\* \<sectionGroup>\*\* ale nie obu.</span><span class="sxs-lookup"><span data-stu-id="87550-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="87550-149">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87550-149">Child elements</span></span>

<span data-ttu-id="87550-150">Brak</span><span class="sxs-lookup"><span data-stu-id="87550-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="87550-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87550-151">Remarks</span></span>

<span data-ttu-id="87550-152">Deklarowanie sekcji konfiguracji zasadniczo definiuje nowy element dla pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87550-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="87550-153">Nowy element zawiera ustawienia, które odczytuje program obsługi sekcji <xref:System.Configuration.IConfigurationSectionHandler> konfiguracji (czyli klasa implementujący interfejs).</span><span class="sxs-lookup"><span data-stu-id="87550-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="87550-154">Atrybuty i elementy podrzędne zdefiniowanej sekcji zależą od programu obsługi sekcji używanego do odczytywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="87550-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="87550-155">Deklarowanie obsługi sekcji konfiguracji w pliku *Machine.config* umożliwia użycie sekcji konfiguracji w dowolnym pliku konfiguracji aplikacji na tym komputerze, chyba że atrybut **allowDefinition** określa inaczej.</span><span class="sxs-lookup"><span data-stu-id="87550-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="87550-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="87550-156">Example</span></span>

<span data-ttu-id="87550-157">W poniższym przykładzie pokazano, jak zdefiniować sekcję konfiguracji i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="87550-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="87550-158">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="87550-158">Configuration file</span></span>

<span data-ttu-id="87550-159">Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87550-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="87550-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87550-160">See also</span></span>

- [<span data-ttu-id="87550-161">Schemat pliku konfiguracyjnego programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="87550-161">Configuration file schema for the .NET Framework</span></span>](index.md)
