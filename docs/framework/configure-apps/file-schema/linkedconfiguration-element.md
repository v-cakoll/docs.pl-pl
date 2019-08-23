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
ms.openlocfilehash: a0b56ac66302f11c59c149197a84bb96691282a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921014"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="e28e2-102">\<linkedConfiguration, element ></span><span class="sxs-lookup"><span data-stu-id="e28e2-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="e28e2-103">Określa plik konfiguracji, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="e28e2-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="e28e2-104">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e28e2-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="e28e2-105">&nbsp;&nbsp;[ **\<> zestawubinding**](assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="e28e2-105">&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="e28e2-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="e28e2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e28e2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e28e2-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="e28e2-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e28e2-108">Attribute</span></span>

|           | <span data-ttu-id="e28e2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e28e2-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="e28e2-110">**Tag**</span><span class="sxs-lookup"><span data-stu-id="e28e2-110">**href**</span></span>  | <span data-ttu-id="e28e2-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="e28e2-111">Required attribute.</span></span><br><br><span data-ttu-id="e28e2-112">Adres URL pliku konfiguracji, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="e28e2-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="e28e2-113">Jedynym formatem obsługiwanym przez atrybut **href** jest `file://`.</span><span class="sxs-lookup"><span data-stu-id="e28e2-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="e28e2-114">Obsługiwane są pliki lokalne i pliki UNC.</span><span class="sxs-lookup"><span data-stu-id="e28e2-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="e28e2-115">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="e28e2-115">Parent element</span></span>

|     | <span data-ttu-id="e28e2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e28e2-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e28e2-117">assemblyBinding — element >  **\<** </span><span class="sxs-lookup"><span data-stu-id="e28e2-117">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="e28e2-118">Określa zasady powiązań zestawów na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e28e2-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e28e2-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e28e2-119">Child elements</span></span>

<span data-ttu-id="e28e2-120">Brak</span><span class="sxs-lookup"><span data-stu-id="e28e2-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="e28e2-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e28e2-121">Remarks</span></span>

<span data-ttu-id="e28e2-122">**\<Linkedconfiguration — >** element upraszcza obsługę techniczną dla zestawów składników.</span><span class="sxs-lookup"><span data-stu-id="e28e2-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="e28e2-123">Co najmniej jednej aplikacji, użycie zestawu, który zawiera plik konfiguracji znajdujących się w lokalizacji, dobrze znanego, pliki konfiguracji aplikacji, które używają zestawu można użyć **\<linkedconfiguration — >** element, aby uwzględnić plik konfiguracji zestawu, a nie bezpośrednio w tym informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e28e2-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="e28e2-124">Gdy zestaw składników jest serwisowany, aktualizacja wspólnego pliku konfiguracji zawiera zaktualizowane informacje o konfiguracji do wszystkich aplikacji, które korzystają z zestawu.</span><span class="sxs-lookup"><span data-stu-id="e28e2-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="e28e2-125">**\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o Windows side-by-side manifestów.</span><span class="sxs-lookup"><span data-stu-id="e28e2-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="e28e2-126">Zastosowanie połączonych plików konfiguracji podlega następującym zasadom:</span><span class="sxs-lookup"><span data-stu-id="e28e2-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="e28e2-127">Ustawienia w zawartych plikach konfiguracji mają wpływ tylko na zasady powiązań modułu ładującego i są używane tylko przez moduł ładujący.</span><span class="sxs-lookup"><span data-stu-id="e28e2-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="e28e2-128">Dołączone pliki konfiguracji mogą mieć ustawienia inne niż zasady powiązań, ale te ustawienia nie mają żadnego efektu.</span><span class="sxs-lookup"><span data-stu-id="e28e2-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="e28e2-129">Jedynym formatem obsługiwanym przez `href` atrybut jest. `file://`</span><span class="sxs-lookup"><span data-stu-id="e28e2-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="e28e2-130">Obsługiwane są pliki lokalne i pliki UNC.</span><span class="sxs-lookup"><span data-stu-id="e28e2-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="e28e2-131">Brak ograniczeń liczby połączonych konfiguracji na plik konfiguracyjny.</span><span class="sxs-lookup"><span data-stu-id="e28e2-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="e28e2-132">Wszystkie połączone pliki konfiguracji są scalane w celu utworzenia jednego pliku, podobnie jak w przypadku `#include` zachowania dyrektywy w językuC++C/.</span><span class="sxs-lookup"><span data-stu-id="e28e2-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="e28e2-133">**\<Linkedconfiguration — >** element jest dozwolony tylko w plikach konfiguracji aplikacji; jest ignorowana w *Machine.config*.</span><span class="sxs-lookup"><span data-stu-id="e28e2-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="e28e2-134">Odwołania cykliczne są wykrywane i kończone.</span><span class="sxs-lookup"><span data-stu-id="e28e2-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="e28e2-135">Oznacza to jeśli **\<linkedconfiguration — >** elementy szeregu plików konfiguracyjnych tworzą pętli, pętla jest wykrywany i zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="e28e2-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="e28e2-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="e28e2-136">Example</span></span>

<span data-ttu-id="e28e2-137">Poniższy przykład pokazuje, jak dołączyć plik konfiguracji z lokalnego dysku twardego:</span><span class="sxs-lookup"><span data-stu-id="e28e2-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e28e2-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e28e2-138">See also</span></span>

- [<span data-ttu-id="e28e2-139">assemblyBinding — element >  **\<** </span><span class="sxs-lookup"><span data-stu-id="e28e2-139">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="e28e2-140">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e28e2-140">Configuration file schema for the .NET Framework</span></span>](index.md)
