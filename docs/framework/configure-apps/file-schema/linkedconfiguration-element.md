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
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087964"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="df5d1-102">\<element > linkedConfiguration</span><span class="sxs-lookup"><span data-stu-id="df5d1-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="df5d1-103">Określa plik konfiguracji, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="df5d1-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="df5d1-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="df5d1-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="df5d1-105">&nbsp;&nbsp;[ **\<zestawubinding >** ](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="df5d1-105">&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="df5d1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="df5d1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="df5d1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="df5d1-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="df5d1-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="df5d1-108">Attribute</span></span>

|           | <span data-ttu-id="df5d1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="df5d1-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="df5d1-110">**Tag**</span><span class="sxs-lookup"><span data-stu-id="df5d1-110">**href**</span></span>  | <span data-ttu-id="df5d1-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="df5d1-111">Required attribute.</span></span><br><br><span data-ttu-id="df5d1-112">Adres URL pliku konfiguracji, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="df5d1-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="df5d1-113">Jedynym formatem obsługiwanym przez atrybut **href** jest `file://`.</span><span class="sxs-lookup"><span data-stu-id="df5d1-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="df5d1-114">Obsługiwane są pliki lokalne i pliki UNC.</span><span class="sxs-lookup"><span data-stu-id="df5d1-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="df5d1-115">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="df5d1-115">Parent element</span></span>

|     | <span data-ttu-id="df5d1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="df5d1-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="df5d1-117"> **\<zestawubinding >** Postaci</span><span class="sxs-lookup"><span data-stu-id="df5d1-117">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="df5d1-118">Określa zasady powiązań zestawów na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="df5d1-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="df5d1-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="df5d1-119">Child elements</span></span>

<span data-ttu-id="df5d1-120">Brak</span><span class="sxs-lookup"><span data-stu-id="df5d1-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="df5d1-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df5d1-121">Remarks</span></span>

<span data-ttu-id="df5d1-122">Element **\<linkedConfiguration >** upraszcza obsługę zestawów składników.</span><span class="sxs-lookup"><span data-stu-id="df5d1-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="df5d1-123">Jeśli co najmniej jedna aplikacja korzysta z zestawu, który ma plik konfiguracji znajdujący się w dobrze znanej lokalizacji, pliki konfiguracyjne aplikacji korzystających z zestawu mogą używać elementu **\<linkedConfiguration >** do dołączenia pliku konfiguracji zestawu, zamiast bezpośredniego umieszczania informacji o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="df5d1-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="df5d1-124">Gdy zestaw składników jest serwisowany, aktualizacja wspólnego pliku konfiguracji zawiera zaktualizowane informacje o konfiguracji do wszystkich aplikacji, które korzystają z zestawu.</span><span class="sxs-lookup"><span data-stu-id="df5d1-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="df5d1-125">Element **\<linkedConfiguration >** nie jest obsługiwany w przypadku aplikacji z manifestami równoległymi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="df5d1-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="df5d1-126">Zastosowanie połączonych plików konfiguracji podlega następującym zasadom:</span><span class="sxs-lookup"><span data-stu-id="df5d1-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="df5d1-127">Ustawienia w zawartych plikach konfiguracji mają wpływ tylko na zasady powiązań modułu ładującego i są używane tylko przez moduł ładujący.</span><span class="sxs-lookup"><span data-stu-id="df5d1-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="df5d1-128">Dołączone pliki konfiguracji mogą mieć ustawienia inne niż zasady powiązań, ale te ustawienia nie mają żadnego efektu.</span><span class="sxs-lookup"><span data-stu-id="df5d1-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="df5d1-129">Jedynym formatem obsługiwanym dla atrybutu `href` jest `file://`.</span><span class="sxs-lookup"><span data-stu-id="df5d1-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="df5d1-130">Obsługiwane są pliki lokalne i pliki UNC.</span><span class="sxs-lookup"><span data-stu-id="df5d1-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="df5d1-131">Brak ograniczeń liczby połączonych konfiguracji na plik konfiguracyjny.</span><span class="sxs-lookup"><span data-stu-id="df5d1-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="df5d1-132">Wszystkie połączone pliki konfiguracji są scalane w celu utworzenia jednego pliku, podobnie do zachowania dyrektywy `#include` w C/C++.</span><span class="sxs-lookup"><span data-stu-id="df5d1-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="df5d1-133">Element **\<linkedConfiguration >** jest dozwolony tylko w plikach konfiguracji aplikacji; jest on ignorowany w *pliku Machine. config*.</span><span class="sxs-lookup"><span data-stu-id="df5d1-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="df5d1-134">Odwołania cykliczne są wykrywane i kończone.</span><span class="sxs-lookup"><span data-stu-id="df5d1-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="df5d1-135">Oznacza to, że jeśli **\<linkedConfiguration >** elementy serii plików konfiguracyjnych tworzą pętlę, pętla zostanie wykryta i zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="df5d1-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="df5d1-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="df5d1-136">Example</span></span>

<span data-ttu-id="df5d1-137">Poniższy przykład pokazuje, jak dołączyć plik konfiguracji z lokalnego dysku twardego:</span><span class="sxs-lookup"><span data-stu-id="df5d1-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="df5d1-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df5d1-138">See also</span></span>

- [<span data-ttu-id="df5d1-139"> **\<zestawubinding >** Postaci</span><span class="sxs-lookup"><span data-stu-id="df5d1-139">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="df5d1-140">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="df5d1-140">Configuration file schema for the .NET Framework</span></span>](index.md)
