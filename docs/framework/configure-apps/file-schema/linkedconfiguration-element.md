---
title: <linkedConfiguration>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
ms.openlocfilehash: 14ee2275ecf690ab16ffaabd71fbbe7e1a4897bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087964"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="2707e-102">\<linkedConfiguration>, element</span><span class="sxs-lookup"><span data-stu-id="2707e-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="2707e-103">Określa plik konfiguracji, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="2707e-103">Specifies a configuration file to include.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a><span data-ttu-id="2707e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2707e-104">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="2707e-105">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2707e-105">Attribute</span></span>

|           | <span data-ttu-id="2707e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2707e-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="2707e-107">**Tag**</span><span class="sxs-lookup"><span data-stu-id="2707e-107">**href**</span></span>  | <span data-ttu-id="2707e-108">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="2707e-108">Required attribute.</span></span><br><br><span data-ttu-id="2707e-109">Adres URL pliku konfiguracji, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="2707e-109">The URL of the configuration file to include.</span></span> <span data-ttu-id="2707e-110">Jedynym formatem obsługiwanym przez atrybut **href** jest `file://` .</span><span class="sxs-lookup"><span data-stu-id="2707e-110">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="2707e-111">Obsługiwane są pliki lokalne i pliki UNC.</span><span class="sxs-lookup"><span data-stu-id="2707e-111">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="2707e-112">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="2707e-112">Parent element</span></span>

|     | <span data-ttu-id="2707e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2707e-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2707e-114">**\<assemblyBinding>** Postaci</span><span class="sxs-lookup"><span data-stu-id="2707e-114">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="2707e-115">Określa zasady powiązań zestawów na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2707e-115">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2707e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2707e-116">Child elements</span></span>

<span data-ttu-id="2707e-117">Brak</span><span class="sxs-lookup"><span data-stu-id="2707e-117">None</span></span>

## <a name="remarks"></a><span data-ttu-id="2707e-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2707e-118">Remarks</span></span>

<span data-ttu-id="2707e-119">**\<linkedConfiguration>** Element upraszcza obsługę zestawów składników.</span><span class="sxs-lookup"><span data-stu-id="2707e-119">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="2707e-120">Jeśli co najmniej jedna aplikacja korzysta z zestawu, który ma plik konfiguracji znajdujący się w dobrze znanej lokalizacji, pliki konfiguracyjne aplikacji korzystających z zestawu mogą używać **\<linkedConfiguration>** elementu do dołączenia pliku konfiguracji zestawu, a nie bezpośredniego uwzględnienia informacji o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2707e-120">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="2707e-121">Gdy zestaw składników jest serwisowany, aktualizacja wspólnego pliku konfiguracji zawiera zaktualizowane informacje o konfiguracji do wszystkich aplikacji, które korzystają z zestawu.</span><span class="sxs-lookup"><span data-stu-id="2707e-121">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="2707e-122">**\<linkedConfiguration>** Element nie jest obsługiwany w przypadku aplikacji z manifestami równoległymi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2707e-122">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="2707e-123">Zastosowanie połączonych plików konfiguracji podlega następującym zasadom:</span><span class="sxs-lookup"><span data-stu-id="2707e-123">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="2707e-124">Ustawienia w zawartych plikach konfiguracji mają wpływ tylko na zasady powiązań modułu ładującego i są używane tylko przez moduł ładujący.</span><span class="sxs-lookup"><span data-stu-id="2707e-124">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="2707e-125">Dołączone pliki konfiguracji mogą mieć ustawienia inne niż zasady powiązań, ale te ustawienia nie mają żadnego efektu.</span><span class="sxs-lookup"><span data-stu-id="2707e-125">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="2707e-126">Jedynym formatem obsługiwanym przez `href` atrybut jest `file://` .</span><span class="sxs-lookup"><span data-stu-id="2707e-126">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="2707e-127">Obsługiwane są pliki lokalne i pliki UNC.</span><span class="sxs-lookup"><span data-stu-id="2707e-127">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="2707e-128">Brak ograniczeń liczby połączonych konfiguracji na plik konfiguracyjny.</span><span class="sxs-lookup"><span data-stu-id="2707e-128">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="2707e-129">Wszystkie połączone pliki konfiguracji są scalane w celu utworzenia jednego pliku, podobnie jak zachowanie `#include` dyrektywy w C/C++.</span><span class="sxs-lookup"><span data-stu-id="2707e-129">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="2707e-130">**\<linkedConfiguration>** Element jest dozwolony tylko w plikach konfiguracji aplikacji; jest ignorowany w *pliku Machine. config*.</span><span class="sxs-lookup"><span data-stu-id="2707e-130">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="2707e-131">Odwołania cykliczne są wykrywane i kończone.</span><span class="sxs-lookup"><span data-stu-id="2707e-131">Circular references are detected and terminated.</span></span> <span data-ttu-id="2707e-132">Oznacza to, że jeśli **\<linkedConfiguration>** elementy serii plików konfiguracji tworzą pętlę, pętla zostanie wykryta i zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="2707e-132">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="2707e-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="2707e-133">Example</span></span>

<span data-ttu-id="2707e-134">Poniższy przykład pokazuje, jak dołączyć plik konfiguracji z lokalnego dysku twardego:</span><span class="sxs-lookup"><span data-stu-id="2707e-134">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2707e-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2707e-135">See also</span></span>

- [<span data-ttu-id="2707e-136">**\<assemblyBinding>** Postaci</span><span class="sxs-lookup"><span data-stu-id="2707e-136">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="2707e-137">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2707e-137">Configuration file schema for the .NET Framework</span></span>](index.md)
