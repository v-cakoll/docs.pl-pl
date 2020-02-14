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
ms.openlocfilehash: 8785523d664294e3ca3792fb0f84d739d1f1a376
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215729"
---
# <a name="section-element"></a><span data-ttu-id="540a8-102">\<sekcja ></span><span class="sxs-lookup"><span data-stu-id="540a8-102">\<section> element</span></span>

<span data-ttu-id="540a8-103">Zawiera deklarację sekcji konfiguracyjnej.</span><span class="sxs-lookup"><span data-stu-id="540a8-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="540a8-104">[ **\<> konfiguracji**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="540a8-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="540a8-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="540a8-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="540a8-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<**</span><span class="sxs-lookup"><span data-stu-id="540a8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="540a8-107">[ **\<> konfiguracji**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="540a8-107">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="540a8-108">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="540a8-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="540a8-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sekcja**](sectiongroup-element-for-configsections.md) ></span><span class="sxs-lookup"><span data-stu-id="540a8-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>\
<span data-ttu-id="540a8-110">&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="540a8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="540a8-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="540a8-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="540a8-112">Wymagane atrybuty</span><span class="sxs-lookup"><span data-stu-id="540a8-112">Required attributes</span></span>

|           | <span data-ttu-id="540a8-113">Opis</span><span class="sxs-lookup"><span data-stu-id="540a8-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="540a8-114">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="540a8-114">**name**</span></span>  | <span data-ttu-id="540a8-115">Określa nazwę sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="540a8-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="540a8-116">**type**</span><span class="sxs-lookup"><span data-stu-id="540a8-116">**type**</span></span>  | <span data-ttu-id="540a8-117">Określa nazwę klasy procedury obsługi sekcji konfiguracji, która odczytuje sekcję z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="540a8-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="540a8-118">Wartość typu ma składnię "w pełni kwalifikowana-sekcja-Handler-class-name, Simple-Assembly-Name".</span><span class="sxs-lookup"><span data-stu-id="540a8-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="540a8-119">Prosta nazwa zestawu to główna nazwa pliku bez rozszerzenia pliku *dll* .</span><span class="sxs-lookup"><span data-stu-id="540a8-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="540a8-120">Atrybuty opcjonalne</span><span class="sxs-lookup"><span data-stu-id="540a8-120">Optional attributes</span></span>

<span data-ttu-id="540a8-121">Następujące atrybuty są stosowane tylko w przypadku aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="540a8-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="540a8-122">System konfiguracji ignoruje te atrybuty dla innych typów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="540a8-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="540a8-123">Opis</span><span class="sxs-lookup"><span data-stu-id="540a8-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="540a8-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="540a8-124">**allowDefinition**</span></span> | <span data-ttu-id="540a8-125">Określa plik konfiguracji, w którym można użyć sekcji.</span><span class="sxs-lookup"><span data-stu-id="540a8-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="540a8-126">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="540a8-126">Use one of the following values:</span></span><br><br><span data-ttu-id="540a8-127">**Tam**</span><span class="sxs-lookup"><span data-stu-id="540a8-127">**Everywhere**</span></span><br><span data-ttu-id="540a8-128">Zezwala na używanie sekcji w dowolnym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="540a8-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="540a8-129">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="540a8-129">This is the default.</span></span><br><span data-ttu-id="540a8-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="540a8-130">**MachineOnly**</span></span><br><span data-ttu-id="540a8-131">Zezwala na użycie sekcji tylko w pliku konfiguracji komputera (*Machine. config*).</span><span class="sxs-lookup"><span data-stu-id="540a8-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="540a8-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="540a8-132">**MachineToApplication**</span></span><br><span data-ttu-id="540a8-133">Zezwala na używanie sekcji w pliku konfiguracji komputera lub pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="540a8-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="540a8-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="540a8-134">**allowLocation**</span></span>   | <span data-ttu-id="540a8-135">Określa, czy sekcja może być używana w **\<lokalizacji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="540a8-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="540a8-136">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="540a8-136">Use one of the following values:</span></span><br><br><span data-ttu-id="540a8-137">**true**</span><span class="sxs-lookup"><span data-stu-id="540a8-137">**true**</span></span><br><span data-ttu-id="540a8-138">Zezwala na używanie sekcji w **\<lokalizacji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="540a8-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="540a8-139">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="540a8-139">This is the default.</span></span><br><span data-ttu-id="540a8-140">**false**</span><span class="sxs-lookup"><span data-stu-id="540a8-140">**false**</span></span><br><span data-ttu-id="540a8-141">Nie zezwala na używanie sekcji w **\<lokalizacji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="540a8-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="540a8-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="540a8-142">Parent elements</span></span>

|     | <span data-ttu-id="540a8-143">Opis</span><span class="sxs-lookup"><span data-stu-id="540a8-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="540a8-144"> **\<configSections >** Postaci</span><span class="sxs-lookup"><span data-stu-id="540a8-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="540a8-145">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="540a8-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="540a8-146"> **\<sekcji >** Postaci</span><span class="sxs-lookup"><span data-stu-id="540a8-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="540a8-147">Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="540a8-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="540a8-148">**\<sekcja >** jest elementem podrzędnym **\<configSections >** lub **\<** , ale nie obu.</span><span class="sxs-lookup"><span data-stu-id="540a8-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="540a8-149">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="540a8-149">Child elements</span></span>

<span data-ttu-id="540a8-150">None</span><span class="sxs-lookup"><span data-stu-id="540a8-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="540a8-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="540a8-151">Remarks</span></span>

<span data-ttu-id="540a8-152">Deklarowanie sekcji konfiguracji zasadniczo definiuje nowy element pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="540a8-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="540a8-153">Nowy element zawiera ustawienia, które są używane przez sekcję konfiguracyjną (czyli klasy implementującej interfejs <xref:System.Configuration.IConfigurationSectionHandler>).</span><span class="sxs-lookup"><span data-stu-id="540a8-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="540a8-154">Atrybuty i elementy podrzędne zdefiniowanej sekcji zależą od procedury obsługi sekcji używanej do odczytywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="540a8-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="540a8-155">Deklarowanie procedury obsługi sekcji konfiguracji w pliku *Machine. config* umożliwia korzystanie z sekcji konfiguracji w dowolnym pliku konfiguracyjnym aplikacji na tym komputerze, chyba że atrybut **AllowDefinition** określa inaczej.</span><span class="sxs-lookup"><span data-stu-id="540a8-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="540a8-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="540a8-156">Example</span></span>

<span data-ttu-id="540a8-157">Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracyjną i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="540a8-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="540a8-158">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="540a8-158">Configuration file</span></span>

<span data-ttu-id="540a8-159">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="540a8-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="540a8-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="540a8-160">See also</span></span>

- [<span data-ttu-id="540a8-161">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="540a8-161">Configuration file schema for the .NET Framework</span></span>](index.md)
