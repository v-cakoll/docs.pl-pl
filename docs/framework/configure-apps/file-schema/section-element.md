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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153736"
---
# <a name="section-element"></a><span data-ttu-id="4b042-102">\<section>, element</span><span class="sxs-lookup"><span data-stu-id="4b042-102">\<section> element</span></span>

<span data-ttu-id="4b042-103">Zawiera deklarację sekcji konfiguracyjnej.</span><span class="sxs-lookup"><span data-stu-id="4b042-103">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="4b042-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b042-104">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="4b042-105">Wymagane atrybuty</span><span class="sxs-lookup"><span data-stu-id="4b042-105">Required attributes</span></span>

|           | <span data-ttu-id="4b042-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4b042-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4b042-107">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="4b042-107">**name**</span></span>  | <span data-ttu-id="4b042-108">Określa nazwę sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4b042-108">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="4b042-109">**Wprowadź**</span><span class="sxs-lookup"><span data-stu-id="4b042-109">**type**</span></span>  | <span data-ttu-id="4b042-110">Określa nazwę klasy procedury obsługi sekcji konfiguracji, która odczytuje sekcję z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="4b042-110">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="4b042-111">Wartość typu ma składnię "w pełni kwalifikowana-sekcja-Handler-class-name, Simple-Assembly-Name".</span><span class="sxs-lookup"><span data-stu-id="4b042-111">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="4b042-112">Prosta nazwa zestawu to główna nazwa pliku bez rozszerzenia pliku *dll* .</span><span class="sxs-lookup"><span data-stu-id="4b042-112">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="4b042-113">Atrybuty opcjonalne</span><span class="sxs-lookup"><span data-stu-id="4b042-113">Optional attributes</span></span>

<span data-ttu-id="4b042-114">Następujące atrybuty są stosowane tylko w przypadku aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4b042-114">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="4b042-115">System konfiguracji ignoruje te atrybuty dla innych typów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4b042-115">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="4b042-116">Opis</span><span class="sxs-lookup"><span data-stu-id="4b042-116">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="4b042-117">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="4b042-117">**allowDefinition**</span></span> | <span data-ttu-id="4b042-118">Określa plik konfiguracji, w którym można użyć sekcji.</span><span class="sxs-lookup"><span data-stu-id="4b042-118">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="4b042-119">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="4b042-119">Use one of the following values:</span></span><br><br><span data-ttu-id="4b042-120">**Tam**</span><span class="sxs-lookup"><span data-stu-id="4b042-120">**Everywhere**</span></span><br><span data-ttu-id="4b042-121">Zezwala na używanie sekcji w dowolnym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="4b042-121">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="4b042-122">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="4b042-122">This is the default.</span></span><br><span data-ttu-id="4b042-123">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="4b042-123">**MachineOnly**</span></span><br><span data-ttu-id="4b042-124">Zezwala na użycie sekcji tylko w pliku konfiguracji komputera (*Machine. config*).</span><span class="sxs-lookup"><span data-stu-id="4b042-124">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="4b042-125">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="4b042-125">**MachineToApplication**</span></span><br><span data-ttu-id="4b042-126">Zezwala na używanie sekcji w pliku konfiguracji komputera lub pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4b042-126">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="4b042-127">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="4b042-127">**allowLocation**</span></span>   | <span data-ttu-id="4b042-128">Określa, czy sekcja może być używana w obrębie **\<location>** elementu.</span><span class="sxs-lookup"><span data-stu-id="4b042-128">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="4b042-129">Użyj jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="4b042-129">Use one of the following values:</span></span><br><br><span data-ttu-id="4b042-130">**oznacza**</span><span class="sxs-lookup"><span data-stu-id="4b042-130">**true**</span></span><br><span data-ttu-id="4b042-131">Zezwala na używanie sekcji w obrębie **\<location>** elementu.</span><span class="sxs-lookup"><span data-stu-id="4b042-131">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="4b042-132">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="4b042-132">This is the default.</span></span><br><span data-ttu-id="4b042-133">**false**</span><span class="sxs-lookup"><span data-stu-id="4b042-133">**false**</span></span><br><span data-ttu-id="4b042-134">Nie zezwala na używanie sekcji w obrębie **\<location>** elementu.</span><span class="sxs-lookup"><span data-stu-id="4b042-134">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="4b042-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4b042-135">Parent elements</span></span>

|     | <span data-ttu-id="4b042-136">Opis</span><span class="sxs-lookup"><span data-stu-id="4b042-136">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4b042-137">**\<configSections>** Postaci</span><span class="sxs-lookup"><span data-stu-id="4b042-137">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="4b042-138">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4b042-138">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="4b042-139">**\<sectionGroup>** Postaci</span><span class="sxs-lookup"><span data-stu-id="4b042-139">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="4b042-140">Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="4b042-140">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="4b042-141">**\<section>** Element jest elementem podrzędnym jednego **\<configSections>** lub, **\<sectionGroup>** ale nie obu.</span><span class="sxs-lookup"><span data-stu-id="4b042-141">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="4b042-142">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4b042-142">Child elements</span></span>

<span data-ttu-id="4b042-143">Brak</span><span class="sxs-lookup"><span data-stu-id="4b042-143">None</span></span>

## <a name="remarks"></a><span data-ttu-id="4b042-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b042-144">Remarks</span></span>

<span data-ttu-id="4b042-145">Deklarowanie sekcji konfiguracji zasadniczo definiuje nowy element pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4b042-145">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="4b042-146">Nowy element zawiera ustawienia, które są używane przez sekcję konfiguracyjną (czyli klasy implementującej <xref:System.Configuration.IConfigurationSectionHandler> interfejs).</span><span class="sxs-lookup"><span data-stu-id="4b042-146">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="4b042-147">Atrybuty i elementy podrzędne zdefiniowanej sekcji zależą od procedury obsługi sekcji używanej do odczytywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="4b042-147">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="4b042-148">Deklarowanie procedury obsługi sekcji konfiguracji w pliku *Machine. config* umożliwia korzystanie z sekcji konfiguracji w dowolnym pliku konfiguracyjnym aplikacji na tym komputerze, chyba że atrybut **AllowDefinition** określa inaczej.</span><span class="sxs-lookup"><span data-stu-id="4b042-148">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="4b042-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b042-149">Example</span></span>

<span data-ttu-id="4b042-150">Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracyjną i zdefiniować ustawienia dla tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="4b042-150">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="4b042-151">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4b042-151">Configuration file</span></span>

<span data-ttu-id="4b042-152">Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4b042-152">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b042-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b042-153">See also</span></span>

- [<span data-ttu-id="4b042-154">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4b042-154">Configuration file schema for the .NET Framework</span></span>](index.md)
