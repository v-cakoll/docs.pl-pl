---
title: '&lt;linkedconfiguration —&gt; — element'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e5c8449e72414775c40ced2c344e12d5137ac03f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546416"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="52600-102">\<linkedConfiguration> element</span><span class="sxs-lookup"><span data-stu-id="52600-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="52600-103">Określa wymagający uwzględnienia plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="52600-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="52600-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="52600-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="52600-105">&nbsp;&nbsp;[**\<assemblybinding — >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="52600-105">&nbsp;&nbsp;[**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="52600-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="52600-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="52600-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="52600-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="52600-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="52600-108">Attribute</span></span>

|           | <span data-ttu-id="52600-109">Opis</span><span class="sxs-lookup"><span data-stu-id="52600-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="52600-110">**href**</span><span class="sxs-lookup"><span data-stu-id="52600-110">**href**</span></span>  | <span data-ttu-id="52600-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="52600-111">Required attribute.</span></span><br><br><span data-ttu-id="52600-112">Adres URL pliku konfiguracji, aby uwzględnić.</span><span class="sxs-lookup"><span data-stu-id="52600-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="52600-113">Jedynym obsługiwanym formatem do **href** atrybut jest `file://`.</span><span class="sxs-lookup"><span data-stu-id="52600-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="52600-114">Obsługiwane są pliki lokalne i plików UNC.</span><span class="sxs-lookup"><span data-stu-id="52600-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="52600-115">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="52600-115">Parent element</span></span>

|     | <span data-ttu-id="52600-116">Opis</span><span class="sxs-lookup"><span data-stu-id="52600-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="52600-117">**\<assemblybinding — >** — Element</span><span class="sxs-lookup"><span data-stu-id="52600-117">**\<assemblyBinding>** Element</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="52600-118">Określa politykę powiązania zestawu na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="52600-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="52600-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="52600-119">Child elements</span></span>

<span data-ttu-id="52600-120">Brak</span><span class="sxs-lookup"><span data-stu-id="52600-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="52600-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52600-121">Remarks</span></span>

<span data-ttu-id="52600-122"> *\*\<Linkedconfiguration — >** element upraszcza obsługę techniczną dla zestawów składników.</span><span class="sxs-lookup"><span data-stu-id="52600-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="52600-123">Co najmniej jednej aplikacji, użycie zestawu, który zawiera plik konfiguracji znajdujących się w lokalizacji, dobrze znanego, pliki konfiguracji aplikacji, które używają zestawu można użyć  **\<linkedconfiguration — >** element, aby uwzględnić plik konfiguracji zestawu, a nie bezpośrednio w tym informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="52600-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="52600-124">Gdy zestaw składników jest obsługiwany, aktualizowanie wspólnego pliku konfiguracji informacje zaktualizowanej konfiguracji do wszystkich aplikacji korzystających z zestawu.</span><span class="sxs-lookup"><span data-stu-id="52600-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="52600-125"> *\*\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o Windows side-by-side manifestów.</span><span class="sxs-lookup"><span data-stu-id="52600-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="52600-126">Użycie powiązane pliki konfiguracji decydują następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="52600-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="52600-127">Ustawienia w plikach konfiguracyjnych uwzględnione tylko wpływa na zasady tworzenia powiązań modułu ładującego i są używane tylko przez moduł ładujący.</span><span class="sxs-lookup"><span data-stu-id="52600-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="52600-128">Pliki dołączone konfiguracji może mieć ustawienia inne niż powiązanie zasad, ale te ustawienia nie mają żadnego efektu.</span><span class="sxs-lookup"><span data-stu-id="52600-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="52600-129">Jedynym obsługiwanym formatem do `href` atrybut jest `file://`.</span><span class="sxs-lookup"><span data-stu-id="52600-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="52600-130">Obsługiwane są pliki lokalne i plików UNC.</span><span class="sxs-lookup"><span data-stu-id="52600-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="52600-131">Brak bez ograniczenia na liczbę połączonych konfiguracji każdego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="52600-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="52600-132">Wszystkie powiązane pliki konfiguracji są scalane w celu utworzenia jeden plik, podobne do zachowania `#include` dyrektywy języka C/C++.</span><span class="sxs-lookup"><span data-stu-id="52600-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="52600-133"> *\*\<Linkedconfiguration — >** element jest dozwolony tylko w plikach konfiguracji aplikacji; jest ignorowana w \*Machine.config\*.</span><span class="sxs-lookup"><span data-stu-id="52600-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="52600-134">Odwołania cykliczne są wykrywane i zakończone.</span><span class="sxs-lookup"><span data-stu-id="52600-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="52600-135">Oznacza to jeśli  **\<linkedconfiguration — >** elementy szeregu plików konfiguracyjnych tworzą pętli, pętla jest wykrywany i zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="52600-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="52600-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="52600-136">Example</span></span>

<span data-ttu-id="52600-137">Poniższy przykład pokazuje, jak dołączyć plik konfiguracji z lokalnego dysku twardego:</span><span class="sxs-lookup"><span data-stu-id="52600-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="52600-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52600-138">See also</span></span>

- [<span data-ttu-id="52600-139">**\<assemblybinding — >** — Element</span><span class="sxs-lookup"><span data-stu-id="52600-139">**\<assemblyBinding>** Element</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="52600-140">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52600-140">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
