---
title: <section> — element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 58f823ce0c128f30e361b4a631d41286533b5f0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701505"
---
# <a name="section-element"></a><span data-ttu-id="f1912-102">\<sekcja > element</span><span class="sxs-lookup"><span data-stu-id="f1912-102">\<section> element</span></span>

<span data-ttu-id="f1912-103">Zawiera deklarację sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1912-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="f1912-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f1912-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="f1912-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f1912-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="f1912-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sekcja >**</span><span class="sxs-lookup"><span data-stu-id="f1912-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="f1912-107">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f1912-107">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="f1912-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f1912-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="f1912-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="f1912-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="f1912-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sekcja >**</span><span class="sxs-lookup"><span data-stu-id="f1912-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f1912-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1912-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="f1912-112">Wymaganych atrybutów</span><span class="sxs-lookup"><span data-stu-id="f1912-112">Required attributes</span></span>

|           | <span data-ttu-id="f1912-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f1912-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f1912-114">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f1912-114">**name**</span></span>  | <span data-ttu-id="f1912-115">Określa nazwę sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1912-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="f1912-116">**type**</span><span class="sxs-lookup"><span data-stu-id="f1912-116">**type**</span></span>  | <span data-ttu-id="f1912-117">Określa nazwę klasy programu obsługi sekcji konfiguracji, które odczytuje sekcji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1912-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="f1912-118">Wartość typu ma składnię "fully-qualified-section-handler-class-name simple zestawu name".</span><span class="sxs-lookup"><span data-stu-id="f1912-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="f1912-119">Nazwa zestawu prostych jest nazwą pliku głównego bez *.dll* rozszerzenie pliku.</span><span class="sxs-lookup"><span data-stu-id="f1912-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="f1912-120">Opcjonalne atrybuty</span><span class="sxs-lookup"><span data-stu-id="f1912-120">Optional attributes</span></span>

<span data-ttu-id="f1912-121">Następujące atrybuty mają zastosowanie tylko w przypadku aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f1912-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="f1912-122">System konfiguracji ignoruje te atrybuty dla innych typów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1912-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="f1912-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f1912-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="f1912-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="f1912-124">**allowDefinition**</span></span> | <span data-ttu-id="f1912-125">Określa plik konfiguracji, który można używać w sekcji.</span><span class="sxs-lookup"><span data-stu-id="f1912-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="f1912-126">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="f1912-126">Use one of the following values:</span></span><br><br><span data-ttu-id="f1912-127">**Wszędzie**</span><span class="sxs-lookup"><span data-stu-id="f1912-127">**Everywhere**</span></span><br><span data-ttu-id="f1912-128">Umożliwia sekcji, aby można używać w dowolnym pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1912-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="f1912-129">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="f1912-129">This is the default.</span></span><br><span data-ttu-id="f1912-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="f1912-130">**MachineOnly**</span></span><br><span data-ttu-id="f1912-131">Zezwala na sekcji, który ma być używany tylko w pliku konfiguracji komputera (*Machine.config*).</span><span class="sxs-lookup"><span data-stu-id="f1912-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="f1912-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="f1912-132">**MachineToApplication**</span></span><br><span data-ttu-id="f1912-133">Umożliwia sekcji do użycia w pliku konfiguracji komputera lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1912-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="f1912-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="f1912-134">**allowLocation**</span></span>   | <span data-ttu-id="f1912-135">Określa, czy sekcja może być używany w ramach  **\<lokalizacja >** elementu.</span><span class="sxs-lookup"><span data-stu-id="f1912-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="f1912-136">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="f1912-136">Use one of the following values:</span></span><br><br><span data-ttu-id="f1912-137">**true**</span><span class="sxs-lookup"><span data-stu-id="f1912-137">**true**</span></span><br><span data-ttu-id="f1912-138">Zezwala na sekcji, aby można używać wewnątrz  **\<lokalizacja >** elementu.</span><span class="sxs-lookup"><span data-stu-id="f1912-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="f1912-139">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="f1912-139">This is the default.</span></span><br><span data-ttu-id="f1912-140">**false**</span><span class="sxs-lookup"><span data-stu-id="f1912-140">**false**</span></span><br><span data-ttu-id="f1912-141">Nie zezwala na sekcji, aby można używać wewnątrz  **\<lokalizacja >** elementu.</span><span class="sxs-lookup"><span data-stu-id="f1912-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="f1912-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f1912-142">Parent elements</span></span>

|     | <span data-ttu-id="f1912-143">Opis</span><span class="sxs-lookup"><span data-stu-id="f1912-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f1912-144">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="f1912-144">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="f1912-145">Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1912-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="f1912-146">**\<sectionGroup>** Element</span><span class="sxs-lookup"><span data-stu-id="f1912-146">**\<sectionGroup>** Element</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="f1912-147">Definiuje obszar nazw dla sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1912-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="f1912-148">A  **\<sekcji >** element jest elementem podrzędnym jednej  **\<configSections >** lub  **\<sectionGroup >** , ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="f1912-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="f1912-149">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f1912-149">Child elements</span></span>

<span data-ttu-id="f1912-150">Brak</span><span class="sxs-lookup"><span data-stu-id="f1912-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="f1912-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1912-151">Remarks</span></span>

<span data-ttu-id="f1912-152">Deklarowanie sekcji konfiguracji zasadniczo definiuje nowy element pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1912-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="f1912-153">Nowy element zawiera ustawienia, że konfiguracja sekcji obsługi (to znaczy, klasę, która implementuje <xref:System.Configuration.IConfigurationSectionHandler> interfejsu) odczytuje.</span><span class="sxs-lookup"><span data-stu-id="f1912-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="f1912-154">Atrybuty i elementy podrzędne sekcji, jaką zdefiniujesz zależą od obsługi sekcji, używane do odczytywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="f1912-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="f1912-155">Deklarowanie program obsługi sekcji konfiguracji w *Machine.config* pliku umożliwia używanie sekcji konfiguracji w pliku konfiguracyjnym dowolnej aplikacji na tym komputerze, chyba że **allowDefinition**atrybutu określi inaczej.</span><span class="sxs-lookup"><span data-stu-id="f1912-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="f1912-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1912-156">Example</span></span>

<span data-ttu-id="f1912-157">Poniższy przykład pokazuje jak zdefiniować sekcję konfiguracji i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="f1912-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="f1912-158">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f1912-158">Configuration file</span></span>

<span data-ttu-id="f1912-159">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1912-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1912-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1912-160">See also</span></span>

- [<span data-ttu-id="f1912-161">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f1912-161">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
