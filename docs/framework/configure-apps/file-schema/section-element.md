---
title: '&lt;sekcja&gt; — element'
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
ms.openlocfilehash: 295cb8ee77c3042dc5742fb23cf4bbcd085b4d36
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659218"
---
# <a name="section-element"></a><span data-ttu-id="a2a5f-102">\<sekcja > element</span><span class="sxs-lookup"><span data-stu-id="a2a5f-102">\<section> element</span></span>

<span data-ttu-id="a2a5f-103">Zawiera deklarację sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="a2a5f-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a2a5f-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a2a5f-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a2a5f-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="a2a5f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sekcja >**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="a2a5f-107">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a2a5f-107">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a2a5f-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a2a5f-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="a2a5f-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="a2a5f-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="a2a5f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sekcja >**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a2a5f-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2a5f-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="a2a5f-112">Wymaganych atrybutów</span><span class="sxs-lookup"><span data-stu-id="a2a5f-112">Required attributes</span></span>

|           | <span data-ttu-id="a2a5f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a2a5f-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a2a5f-114">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-114">**name**</span></span>  | <span data-ttu-id="a2a5f-115">Określa nazwę sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="a2a5f-116">**type**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-116">**type**</span></span>  | <span data-ttu-id="a2a5f-117">Określa nazwę klasy programu obsługi sekcji konfiguracji, które odczytuje sekcji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="a2a5f-118">Wartość typu ma składnię "fully-qualified-section-handler-class-name simple zestawu name".</span><span class="sxs-lookup"><span data-stu-id="a2a5f-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="a2a5f-119">Nazwa zestawu prostych jest nazwą pliku głównego bez *.dll* rozszerzenie pliku.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="a2a5f-120">Opcjonalne atrybuty</span><span class="sxs-lookup"><span data-stu-id="a2a5f-120">Optional attributes</span></span>

<span data-ttu-id="a2a5f-121">Następujące atrybuty mają zastosowanie tylko w przypadku aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="a2a5f-122">System konfiguracji ignoruje te atrybuty dla innych typów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="a2a5f-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a2a5f-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="a2a5f-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-124">**allowDefinition**</span></span> | <span data-ttu-id="a2a5f-125">Określa plik konfiguracji, który można używać w sekcji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="a2a5f-126">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="a2a5f-126">Use one of the following values:</span></span><br><br><span data-ttu-id="a2a5f-127">**Wszędzie**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-127">**Everywhere**</span></span><br><span data-ttu-id="a2a5f-128">Umożliwia sekcji, aby można używać w dowolnym pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="a2a5f-129">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-129">This is the default.</span></span><br><span data-ttu-id="a2a5f-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-130">**MachineOnly**</span></span><br><span data-ttu-id="a2a5f-131">Zezwala na sekcji, który ma być używany tylko w pliku konfiguracji komputera (*Machine.config*).</span><span class="sxs-lookup"><span data-stu-id="a2a5f-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="a2a5f-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-132">**MachineToApplication**</span></span><br><span data-ttu-id="a2a5f-133">Umożliwia sekcji do użycia w pliku konfiguracji komputera lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="a2a5f-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-134">**allowLocation**</span></span>   | <span data-ttu-id="a2a5f-135">Określa, czy sekcja może być używany w ramach  **\<lokalizacja >** elementu.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="a2a5f-136">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="a2a5f-136">Use one of the following values:</span></span><br><br><span data-ttu-id="a2a5f-137">**true**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-137">**true**</span></span><br><span data-ttu-id="a2a5f-138">Zezwala na sekcji, aby można używać wewnątrz  **\<lokalizacja >** elementu.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="a2a5f-139">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-139">This is the default.</span></span><br><span data-ttu-id="a2a5f-140">**false**</span><span class="sxs-lookup"><span data-stu-id="a2a5f-140">**false**</span></span><br><span data-ttu-id="a2a5f-141">Nie zezwala na sekcji, aby można używać wewnątrz  **\<lokalizacja >** elementu.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="a2a5f-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a2a5f-142">Parent elements</span></span>

|     | <span data-ttu-id="a2a5f-143">Opis</span><span class="sxs-lookup"><span data-stu-id="a2a5f-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a2a5f-144">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="a2a5f-144">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="a2a5f-145">Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="a2a5f-146">**\<sectionGroup>** Element</span><span class="sxs-lookup"><span data-stu-id="a2a5f-146">**\<sectionGroup>** Element</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="a2a5f-147">Definiuje obszar nazw dla sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="a2a5f-148">A  **\<sekcji >** element jest elementem podrzędnym jednej  **\<configSections >** lub  **\<sectionGroup >** , ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="a2a5f-149">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a2a5f-149">Child elements</span></span>

<span data-ttu-id="a2a5f-150">Brak</span><span class="sxs-lookup"><span data-stu-id="a2a5f-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="a2a5f-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2a5f-151">Remarks</span></span>

<span data-ttu-id="a2a5f-152">Deklarowanie sekcji konfiguracji zasadniczo definiuje nowy element pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="a2a5f-153">Nowy element zawiera ustawienia, że konfiguracja sekcji obsługi (to znaczy, klasę, która implementuje <xref:System.Configuration.IConfigurationSectionHandler> interfejsu) odczytuje.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="a2a5f-154">Atrybuty i elementy podrzędne sekcji, jaką zdefiniujesz zależą od obsługi sekcji, używane do odczytywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="a2a5f-155">Deklarowanie program obsługi sekcji konfiguracji w *Machine.config* pliku umożliwia używanie sekcji konfiguracji w pliku konfiguracyjnym dowolnej aplikacji na tym komputerze, chyba że **allowDefinition**atrybutu określi inaczej.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="a2a5f-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2a5f-156">Example</span></span>

<span data-ttu-id="a2a5f-157">Poniższy przykład pokazuje jak zdefiniować sekcję konfiguracji i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="a2a5f-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="a2a5f-158">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a2a5f-158">Configuration file</span></span>

<span data-ttu-id="a2a5f-159">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2a5f-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2a5f-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2a5f-160">See also</span></span>

- [<span data-ttu-id="a2a5f-161">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2a5f-161">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
