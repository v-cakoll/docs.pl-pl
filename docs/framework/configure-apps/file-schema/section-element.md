---
title: "&lt;sekcja&gt; — element"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8ed8b0211c8366d799fe158d91dcb42f92ad0cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="section-element"></a><span data-ttu-id="b5cc9-102">\<sekcja > — element</span><span class="sxs-lookup"><span data-stu-id="b5cc9-102">\<section> element</span></span>

<span data-ttu-id="b5cc9-103">Zawiera deklaracji sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="b5cc9-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b5cc9-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="b5cc9-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="b5cc9-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="b5cc9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sekcja >**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="b5cc9-107">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b5cc9-107">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="b5cc9-108">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="b5cc9-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="b5cc9-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="b5cc9-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="b5cc9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sekcja >**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b5cc9-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5cc9-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="b5cc9-112">Wymaganych atrybutów</span><span class="sxs-lookup"><span data-stu-id="b5cc9-112">Required attributes</span></span>

|           | <span data-ttu-id="b5cc9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b5cc9-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="b5cc9-114">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-114">**name**</span></span>  | <span data-ttu-id="b5cc9-115">Określa nazwę sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="b5cc9-116">**Typ**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-116">**type**</span></span>  | <span data-ttu-id="b5cc9-117">Określa nazwę klasy obsługi sekcji konfiguracji, która odczytuje sekcji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="b5cc9-118">Wartość typu ma składnię "fully-qualified-section-handler-class-name, prosty zestawu name".</span><span class="sxs-lookup"><span data-stu-id="b5cc9-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="b5cc9-119">Nazwa zestawu prostych jest nazwa głównego pliku bez *.dll* rozszerzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="b5cc9-120">Opcjonalne atrybuty</span><span class="sxs-lookup"><span data-stu-id="b5cc9-120">Optional attributes</span></span>

<span data-ttu-id="b5cc9-121">Następujące atrybuty są stosowane tylko do aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="b5cc9-122">System konfiguracji ignoruje te atrybuty dla różnych typów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="b5cc9-123">Opis</span><span class="sxs-lookup"><span data-stu-id="b5cc9-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="b5cc9-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-124">**allowDefinition**</span></span> | <span data-ttu-id="b5cc9-125">Określa do jakiego sekcji mogą być używane w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="b5cc9-126">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="b5cc9-126">Use one of the following values:</span></span><br><br><span data-ttu-id="b5cc9-127">**Wszędzie**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-127">**Everywhere**</span></span><br><span data-ttu-id="b5cc9-128">Umożliwia sekcji, aby można używać w dowolnym pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="b5cc9-129">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-129">This is the default.</span></span><br><span data-ttu-id="b5cc9-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-130">**MachineOnly**</span></span><br><span data-ttu-id="b5cc9-131">Umożliwia sekcji, aby można używać tylko w pliku konfiguracji komputera (*Machine.config*).</span><span class="sxs-lookup"><span data-stu-id="b5cc9-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="b5cc9-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-132">**MachineToApplication**</span></span><br><span data-ttu-id="b5cc9-133">Umożliwia sekcji do użycia w pliku konfiguracyjnym maszyny lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="b5cc9-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-134">**allowLocation**</span></span>   | <span data-ttu-id="b5cc9-135">Określa, czy sekcja mogą być używane w ramach  **\<lokalizacji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="b5cc9-136">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="b5cc9-136">Use one of the following values:</span></span><br><br><span data-ttu-id="b5cc9-137">**wartość true**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-137">**true**</span></span><br><span data-ttu-id="b5cc9-138">Umożliwia sekcji do użycia w  **\<lokalizacji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="b5cc9-139">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-139">This is the default.</span></span><br><span data-ttu-id="b5cc9-140">**wartość false**</span><span class="sxs-lookup"><span data-stu-id="b5cc9-140">**false**</span></span><br><span data-ttu-id="b5cc9-141">Nie zezwalaj na sekcji do użycia w  **\<lokalizacji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="b5cc9-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b5cc9-142">Parent elements</span></span>

|     | <span data-ttu-id="b5cc9-143">Opis</span><span class="sxs-lookup"><span data-stu-id="b5cc9-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b5cc9-144">**\<configSections >** — Element</span><span class="sxs-lookup"><span data-stu-id="b5cc9-144">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="b5cc9-145">Zawiera konfigurację deklaracji sekcji i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="b5cc9-146">**\<sectionGroup >** — Element</span><span class="sxs-lookup"><span data-stu-id="b5cc9-146">**\<sectionGroup>** Element</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="b5cc9-147">Definiuje obszar nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="b5cc9-148">A  **\<sekcji >** element jest elementem podrzędnym albo  **\<configSections >** lub  **\<sectionGroup >** , ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="b5cc9-149">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b5cc9-149">Child elements</span></span>

<span data-ttu-id="b5cc9-150">Brak</span><span class="sxs-lookup"><span data-stu-id="b5cc9-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="b5cc9-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5cc9-151">Remarks</span></span>

<span data-ttu-id="b5cc9-152">Deklarowanie sekcji konfiguracji zasadniczo definiuje nowego elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="b5cc9-153">Nowy element zawiera ustawienia, że konfiguracja sekcji obsługi (to znaczy, że klasa implementująca <xref:System.Configuration.IConfigurationSectionHandler> interfejsu) odczytuje.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="b5cc9-154">Atrybuty i elementy podrzędne sekcji definiowane są zależne od modułu obsługi sekcji, używaną do odczytu ustawień.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="b5cc9-155">Deklarowanie modułu obsługi sekcji konfiguracji w *Machine.config* pliku pozwala na użycie sekcji konfiguracji w żadnym pliku konfiguracji aplikacji na tym komputerze, chyba że **allowDefinition**atrybut określa, w przeciwnym razie wartość.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="b5cc9-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5cc9-156">Example</span></span>

<span data-ttu-id="b5cc9-157">Poniższy przykład pokazuje, jak planować sekcji konfiguracji i określać ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="b5cc9-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="b5cc9-158">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b5cc9-158">Configuration file</span></span>

<span data-ttu-id="b5cc9-159">Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5cc9-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5cc9-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5cc9-160">See also</span></span>

[<span data-ttu-id="b5cc9-161">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b5cc9-161">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
