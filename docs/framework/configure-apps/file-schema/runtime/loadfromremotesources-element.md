---
title: <loadFromRemoteSources>, element
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154065"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="1d84d-102">\<element> loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="1d84d-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="1d84d-103">Określa, czy zestawy ładowane ze źródeł zdalnych powinny mieć pełne zaufanie do programu .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="1d84d-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1d84d-104">Jeśli zostałeś przekierowany do tego artykułu z powodu komunikatu o błędzie na liście błędów projektu programu Visual Studio lub błędu kompilacji, zobacz [Jak: Użyj zestawu z sieci Web w programie Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1d84d-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
<span data-ttu-id="1d84d-105">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1d84d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1d84d-106">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="1d84d-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="1d84d-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span><span class="sxs-lookup"><span data-stu-id="1d84d-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d84d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d84d-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d84d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d84d-109">Attributes and elements</span></span>
 <span data-ttu-id="1d84d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d84d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d84d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d84d-111">Attributes</span></span>  
  
|<span data-ttu-id="1d84d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1d84d-112">Attribute</span></span>|<span data-ttu-id="1d84d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1d84d-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1d84d-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1d84d-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="1d84d-115">Określa, czy zestaw, który jest ładowany ze źródła zdalnego powinny mieć pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="1d84d-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1d84d-116">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="1d84d-116">enabled attribute</span></span>  
  
|<span data-ttu-id="1d84d-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="1d84d-117">Value</span></span>|<span data-ttu-id="1d84d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="1d84d-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1d84d-119">Nie udzielaj pełnego zaufania do aplikacji ze źródeł zdalnych.</span><span class="sxs-lookup"><span data-stu-id="1d84d-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="1d84d-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="1d84d-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="1d84d-121">Zapewnij pełne zaufanie aplikacjom ze źródeł zdalnych.</span><span class="sxs-lookup"><span data-stu-id="1d84d-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d84d-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d84d-122">Child elements</span></span>  
 <span data-ttu-id="1d84d-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="1d84d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d84d-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d84d-124">Parent elements</span></span>  
  
|<span data-ttu-id="1d84d-125">Element</span><span class="sxs-lookup"><span data-stu-id="1d84d-125">Element</span></span>|<span data-ttu-id="1d84d-126">Opis</span><span class="sxs-lookup"><span data-stu-id="1d84d-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1d84d-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1d84d-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1d84d-128">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1d84d-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d84d-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d84d-129">Remarks</span></span>

<span data-ttu-id="1d84d-130">W .NET Framework 3.5 i wcześniejszych wersjach, jeśli załadować zestaw z lokalizacji zdalnej, kod w zestawie działa w częściowym zaufaniu z zestawem dotacji, który zależy od strefy, z której jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="1d84d-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="1d84d-131">Na przykład jeśli załadować zestaw z witryny sieci Web, jest ładowany do strefy Internet i przyznane zestaw uprawnień Internet.</span><span class="sxs-lookup"><span data-stu-id="1d84d-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="1d84d-132">Innymi słowy, jest on wykonywany w piaskownicy internetowej.</span><span class="sxs-lookup"><span data-stu-id="1d84d-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="1d84d-133">Począwszy od .NET Framework 4, zasady zabezpieczeń dostępu do kodu (CAS) jest wyłączona i zestawy są ładowane w pełnym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="1d84d-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="1d84d-134">Zwykle dałoby to pełne zaufanie do zestawów <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> załadowanych metodą, która wcześniej była w trybie piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="1d84d-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="1d84d-135">Aby temu zapobiec, możliwość uruchamiania kodu w zestawach załadowanych ze źródła zdalnego jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="1d84d-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="1d84d-136">Domyślnie, jeśli spróbujesz załadować <xref:System.IO.FileLoadException> zestaw zdalny, zostanie wyświetlony komunikat o wyjątku, następujący:</span><span class="sxs-lookup"><span data-stu-id="1d84d-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

<span data-ttu-id="1d84d-137">Aby załadować zestaw i wykonać jego kod, należy:</span><span class="sxs-lookup"><span data-stu-id="1d84d-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="1d84d-138">Jawnie utworzyć piaskownicę dla zestawu (zobacz [Jak: Uruchom częściowo zaufany kod w piaskownicy](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span><span class="sxs-lookup"><span data-stu-id="1d84d-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="1d84d-139">Uruchom kod zestawu w pełnym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="1d84d-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="1d84d-140">Można to zrobić, `<loadFromRemoteSources>` konfigurując element.</span><span class="sxs-lookup"><span data-stu-id="1d84d-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="1d84d-141">Umożliwia określenie, że zestawy, które są uruchamiane w częściowym zaufaniu we wcześniejszych wersjach programu .NET Framework, są teraz uruchamiane w pełnym zaufaniu w programach .NET Framework 4 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="1d84d-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d84d-142">Jeśli zestaw nie powinien być uruchamiany w pełnym zaufaniu, nie należy ustawiać tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1d84d-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="1d84d-143">Zamiast tego należy utworzyć <xref:System.AppDomain> piaskownicy, w którym mają być ładowane złożenia.</span><span class="sxs-lookup"><span data-stu-id="1d84d-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="1d84d-144">Atrybut `enabled` `<loadFromRemoteSources>` elementu jest skuteczny tylko wtedy, gdy zabezpieczenia dostępu do kodu (CAS) jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="1d84d-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="1d84d-145">Domyślnie zasady CAS są wyłączone w .NET Framework 4 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="1d84d-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="1d84d-146">Jeśli ustawisz, `enabled` `true`zestawy zdalne są przyznawane pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="1d84d-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="1d84d-147">Jeśli `enabled` nie jest `true`ustawiona na , a <xref:System.IO.FileLoadException> jest wyrzucany pod jednym z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="1d84d-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="1d84d-148">Zachowanie piaskownicy bieżącej domeny różni się od jego zachowania w .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="1d84d-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="1d84d-149">Wymaga to wyłączenia zasad CAS, a bieżąca domena nie jest piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="1d84d-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="1d84d-150">Załadowany zestaw nie pochodzi `MyComputer` ze strefy.</span><span class="sxs-lookup"><span data-stu-id="1d84d-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="1d84d-151">Ustawienie `<loadFromRemoteSources>` elementu, `true` aby zapobiec ten wyjątek z zgłaszanych.</span><span class="sxs-lookup"><span data-stu-id="1d84d-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="1d84d-152">Umożliwia określenie, że nie są zależne od środowiska wykonawczego języka wspólnego do piaskownicy załadowanych zestawów dla zabezpieczeń i że mogą one być dozwolone do wykonywania w pełnym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="1d84d-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="1d84d-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d84d-153">Notes</span></span>

- <span data-ttu-id="1d84d-154">W .NET Framework 4.5 i nowszych wersjach zestawy w lokalnych udziałach sieciowych są domyślnie uruchamiane w pełnym zaufaniu; nie trzeba włączać `<loadFromRemoteSources>` elementu.</span><span class="sxs-lookup"><span data-stu-id="1d84d-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="1d84d-155">Jeśli aplikacja została skopiowana z sieci Web, jest oflagowana przez system Windows jako aplikacja sieci web, nawet jeśli znajduje się na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="1d84d-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="1d84d-156">Można zmienić to oznaczenie, zmieniając jego właściwości `<loadFromRemoteSources>` pliku lub można użyć elementu do przyznania pełnego zaufania zestawu.</span><span class="sxs-lookup"><span data-stu-id="1d84d-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="1d84d-157">Alternatywnie można użyć <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metody, aby załadować zestaw lokalny, który system operacyjny oflagował jako załadowany z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1d84d-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="1d84d-158">Możesz uzyskać <xref:System.IO.FileLoadException> w aplikacji, która jest uruchomiona w aplikacji Windows Virtual PC.</span><span class="sxs-lookup"><span data-stu-id="1d84d-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="1d84d-159">Może się to zdarzyć podczas próby załadowania pliku z połączonych folderów na komputerze hostingowym.</span><span class="sxs-lookup"><span data-stu-id="1d84d-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="1d84d-160">Może również wystąpić podczas próby załadowania pliku z folderu połączonego za pomocą [usług pulpitu zdalnego](/windows/win32/termserv/terminal-services-portal) (usług terminalowych).</span><span class="sxs-lookup"><span data-stu-id="1d84d-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](/windows/win32/termserv/terminal-services-portal) (Terminal Services).</span></span> <span data-ttu-id="1d84d-161">Aby uniknąć wyjątku, ustaw `enabled` na `true`.</span><span class="sxs-lookup"><span data-stu-id="1d84d-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="1d84d-162">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1d84d-162">Configuration file</span></span>

<span data-ttu-id="1d84d-163">Ten element jest zwykle używany w pliku konfiguracji aplikacji, ale może być używany w innych plikach konfiguracyjnych w zależności od kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1d84d-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="1d84d-164">Aby uzyskać więcej informacji, zobacz artykuł [Więcej niejawnych zastosowań zasad CAS: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) w blogu .NET Security.</span><span class="sxs-lookup"><span data-stu-id="1d84d-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="1d84d-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d84d-165">Example</span></span>

<span data-ttu-id="1d84d-166">W poniższym przykładzie pokazano, jak udzielić pełnego zaufania do zestawów załadowanych ze źródeł zdalnych.</span><span class="sxs-lookup"><span data-stu-id="1d84d-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="1d84d-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d84d-167">See also</span></span>

- [<span data-ttu-id="1d84d-168">Więcej niejawnych zastosowań zasad CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="1d84d-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [<span data-ttu-id="1d84d-169">Porady: uruchamianie częściowo zaufanego kodu w bibliotece</span><span class="sxs-lookup"><span data-stu-id="1d84d-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="1d84d-170">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1d84d-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1d84d-171">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1d84d-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
