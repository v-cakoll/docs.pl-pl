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
manager: markl
ms.openlocfilehash: 71769efa1233fc8a693219dc02ae56ea39c164e7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743800"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="8559b-102">\<linkedconfiguration — > — element</span><span class="sxs-lookup"><span data-stu-id="8559b-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="8559b-103">Określa plik konfiguracji do uwzględnienia.</span><span class="sxs-lookup"><span data-stu-id="8559b-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="8559b-104">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8559b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="8559b-105">&nbsp;&nbsp;[**\<assemblybinding — >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="8559b-105">&nbsp;&nbsp;[**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="8559b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedconfiguration — >**</span><span class="sxs-lookup"><span data-stu-id="8559b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8559b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8559b-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="8559b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8559b-108">Attribute</span></span>

|           | <span data-ttu-id="8559b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8559b-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="8559b-110">**href**</span><span class="sxs-lookup"><span data-stu-id="8559b-110">**href**</span></span>  | <span data-ttu-id="8559b-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8559b-111">Required attribute.</span></span><br><br><span data-ttu-id="8559b-112">Adres URL pliku konfiguracji, aby uwzględnić.</span><span class="sxs-lookup"><span data-stu-id="8559b-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="8559b-113">Jedynym obsługiwanym formatem do **href** atrybutu `file://`.</span><span class="sxs-lookup"><span data-stu-id="8559b-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="8559b-114">Lokalnych plików i plików UNC są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="8559b-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="8559b-115">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="8559b-115">Parent element</span></span>

|     | <span data-ttu-id="8559b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8559b-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8559b-117">**\<assemblybinding — >** — Element</span><span class="sxs-lookup"><span data-stu-id="8559b-117">**\<assemblyBinding>** Element</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="8559b-118">Określa zestaw powiązania zasad na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8559b-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8559b-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8559b-119">Child elements</span></span>

<span data-ttu-id="8559b-120">Brak</span><span class="sxs-lookup"><span data-stu-id="8559b-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="8559b-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8559b-121">Remarks</span></span>

<span data-ttu-id="8559b-122">**\<Linkedconfiguration — >** element upraszcza obsługi dla zestawów składników.</span><span class="sxs-lookup"><span data-stu-id="8559b-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="8559b-123">Użycie zestawu, który zawiera plik konfiguracji znajdujących się w dobrze znanej lokalizacji, co najmniej jednej aplikacji można użyć pliki konfiguracji aplikacji, które używają zestawu  **\<linkedconfiguration — >** element do uwzględnienia w pliku konfiguracji zestawu, a nie bezpośrednio w tym informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8559b-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="8559b-124">Gdy zestaw składników jest obsługiwana, aktualizowania typowych plik konfiguracji zawiera informacje zaktualizowanej konfiguracji we wszystkich aplikacjach korzystających z zestawu.</span><span class="sxs-lookup"><span data-stu-id="8559b-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="8559b-125">**\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o manifestów side-by-side systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8559b-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="8559b-126">Następujące reguły kontrolować używanie powiązane pliki konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="8559b-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="8559b-127">Ustawień w plikach konfiguracji dołączone tylko wpływa na zasady powiązanie modułu ładującego i są używane tylko przez moduł ładujący.</span><span class="sxs-lookup"><span data-stu-id="8559b-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="8559b-128">Pliki konfiguracji dołączone może mieć ustawienia inne niż powiązanie zasady, ale te ustawienia nie ma żadnego efektu.</span><span class="sxs-lookup"><span data-stu-id="8559b-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="8559b-129">Jedynym obsługiwanym formatem do `href` atrybutu `file://`.</span><span class="sxs-lookup"><span data-stu-id="8559b-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="8559b-130">Lokalnych plików i plików UNC są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="8559b-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="8559b-131">Brak ograniczeń dotyczących liczba połączonych konfiguracji dla każdego pliku konfiguracji nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="8559b-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="8559b-132">Wszystkie powiązane pliki konfiguracji zostaną scalone tworzą jeden plik podobne do zachowania `#include` dyrektywy języka C/C++.</span><span class="sxs-lookup"><span data-stu-id="8559b-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="8559b-133">**\<Linkedconfiguration — >** element jest dozwolony tylko w plikach konfiguracji aplikacji; jest ignorowana w *Machine.config*.</span><span class="sxs-lookup"><span data-stu-id="8559b-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="8559b-134">Odwołania cykliczne są wykrywane i zakończone.</span><span class="sxs-lookup"><span data-stu-id="8559b-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="8559b-135">Oznacza to, że jeśli  **\<linkedconfiguration — >** elementy z szeregu plików konfiguracyjnych tworzą pętlę, pętli są wykrywane i zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="8559b-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="8559b-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="8559b-136">Example</span></span>

<span data-ttu-id="8559b-137">Poniższy przykład przedstawia sposób pliku konfiguracji z lokalnego dysku twardego obejmują:</span><span class="sxs-lookup"><span data-stu-id="8559b-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8559b-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8559b-138">See also</span></span>

<span data-ttu-id="8559b-139">[**\<assemblybinding — >** — Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="8559b-139">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
[<span data-ttu-id="8559b-140">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8559b-140">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
