---
title: <loadFromRemoteSources>, element
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8e8663bf9d119007eb7d3771d16d55b1aa54856
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663606"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="672a4-102">\<loadFromRemoteSources, element ></span><span class="sxs-lookup"><span data-stu-id="672a4-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="672a4-103">Określa, czy zestawy ładowane ze źródeł zdalnych powinny mieć przyznane pełne zaufanie w .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="672a4-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="672a4-104">Jeśli nastąpiło przekierowanie do tego artykułu z powodu komunikatu o błędzie na liście błędów projektu programu Visual Studio lub błędu kompilacji, zobacz [How to: Użyj zestawu z sieci Web w programie Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="672a4-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
 <span data-ttu-id="672a4-105">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="672a4-105">\<configuration></span></span>  
<span data-ttu-id="672a4-106">\<runtime></span><span class="sxs-lookup"><span data-stu-id="672a4-106">\<runtime></span></span>  
<span data-ttu-id="672a4-107">\<loadFromRemoteSources></span><span class="sxs-lookup"><span data-stu-id="672a4-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="672a4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="672a4-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="672a4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="672a4-109">Attributes and elements</span></span>
 <span data-ttu-id="672a4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="672a4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="672a4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="672a4-111">Attributes</span></span>  
  
|<span data-ttu-id="672a4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="672a4-112">Attribute</span></span>|<span data-ttu-id="672a4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="672a4-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="672a4-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="672a4-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="672a4-115">Określa, czy zestaw, który jest ładowany ze źródła zdalnego, powinien mieć przyznane pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="672a4-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="672a4-116">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="672a4-116">enabled attribute</span></span>  
  
|<span data-ttu-id="672a4-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="672a4-117">Value</span></span>|<span data-ttu-id="672a4-118">Opis</span><span class="sxs-lookup"><span data-stu-id="672a4-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="672a4-119">Nie należy przyznawać pełnego zaufania do aplikacji ze źródeł zdalnych.</span><span class="sxs-lookup"><span data-stu-id="672a4-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="672a4-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="672a4-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="672a4-121">Przyznaj pełne zaufanie do aplikacji ze źródeł zdalnych.</span><span class="sxs-lookup"><span data-stu-id="672a4-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="672a4-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="672a4-122">Child elements</span></span>  
 <span data-ttu-id="672a4-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="672a4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="672a4-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="672a4-124">Parent elements</span></span>  
  
|<span data-ttu-id="672a4-125">Element</span><span class="sxs-lookup"><span data-stu-id="672a4-125">Element</span></span>|<span data-ttu-id="672a4-126">Opis</span><span class="sxs-lookup"><span data-stu-id="672a4-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="672a4-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="672a4-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="672a4-128">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="672a4-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="672a4-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="672a4-129">Remarks</span></span>

<span data-ttu-id="672a4-130">W .NET Framework 3,5 i starszych wersjach, Jeśli ładujesz zestaw z lokalizacji zdalnej, kod w zestawie jest uruchamiany w częściowej relacji zaufania z zestawem uprawnień, który zależy od strefy, z której jest załadowana.</span><span class="sxs-lookup"><span data-stu-id="672a4-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="672a4-131">Na przykład, Jeśli ładujesz zestaw z witryny sieci Web, zostanie on załadowany do strefy Internet i przyznany zestaw uprawnień internetowych.</span><span class="sxs-lookup"><span data-stu-id="672a4-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="672a4-132">Innymi słowy, jest wykonywana w piaskownicy internetowej.</span><span class="sxs-lookup"><span data-stu-id="672a4-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="672a4-133">Począwszy od .NET Framework 4, zasady zabezpieczeń dostępu kodu (CAS) są wyłączone, a zestawy są ładowane w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="672a4-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="672a4-134">Zwykle pozwala to na pełne zaufanie do zestawów ładowanych przy użyciu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody, która wcześniej była w trybie piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="672a4-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="672a4-135">Aby tego uniknąć, możliwość uruchamiania kodu w zestawach załadowanych ze zdalnego źródła jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="672a4-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="672a4-136">Domyślnie, jeśli próbujesz załadować zestaw zdalny, <xref:System.IO.FileLoadException> zostanie zgłoszony komunikat o wyjątku podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="672a4-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

<span data-ttu-id="672a4-137">Aby załadować zestaw i wykonać jego kod, musisz:</span><span class="sxs-lookup"><span data-stu-id="672a4-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="672a4-138">Jawnie Utwórz piaskownicę dla zestawu (zobacz [How to: Uruchom częściowo zaufany kod w piaskownicy](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span><span class="sxs-lookup"><span data-stu-id="672a4-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="672a4-139">Uruchom kod zestawu w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="672a4-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="672a4-140">W tym celu należy skonfigurować `<loadFromRemoteSources>` element.</span><span class="sxs-lookup"><span data-stu-id="672a4-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="672a4-141">Pozwala określić, że zestawy, które działają w częściowej relacji zaufania we wcześniejszych wersjach .NET Framework, są teraz uruchamiane w trybie pełnego zaufania w .NET Framework 4 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="672a4-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="672a4-142">Jeśli zestaw nie powinien działać w trybie pełnego zaufania, nie ustawiaj tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="672a4-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="672a4-143">Zamiast tego należy utworzyć piaskownicę <xref:System.AppDomain> , w której ma zostać załadowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="672a4-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="672a4-144">`enabled` Atrybut`<loadFromRemoteSources>` dla elementu jest obowiązujący tylko wtedy, gdy zabezpieczenia dostępu kodu (CAS) są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="672a4-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="672a4-145">Domyślnie zasady CAS są wyłączone w .NET Framework 4 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="672a4-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="672a4-146">Jeśli ustawisz `enabled` `true`opcję, zdalne zestawy mają przyznane pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="672a4-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="672a4-147">Jeśli `enabled` parametr nie jest ustawiony `true`na, <xref:System.IO.FileLoadException> zwracany jest następujący warunek:</span><span class="sxs-lookup"><span data-stu-id="672a4-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="672a4-148">Zachowanie w piaskownicy bieżącej domeny różni się od zachowania w .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="672a4-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="672a4-149">Wymaga to wyłączenia zasad CAS i bieżącej domeny nie należy do piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="672a4-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="672a4-150">Ładowany zestaw nie `MyComputer` należy do strefy.</span><span class="sxs-lookup"><span data-stu-id="672a4-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="672a4-151">Ustawianie elementu `<loadFromRemoteSources>` , aby `true` zapobiec zgłaszaniu tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="672a4-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="672a4-152">Pozwala to określić, że nie korzystasz z aparatu plików wykonywalnych języka wspólnego do piaskownicy załadowanych zestawów pod kątem zabezpieczeń, i że mogą one być wykonywane w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="672a4-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="672a4-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="672a4-153">Notes</span></span>

- <span data-ttu-id="672a4-154">W .NET Framework 4,5 i nowszych wersjach zestawy w lokalnych udziałach sieciowych są domyślnie uruchamiane w trybie pełnego zaufania; nie musisz włączać `<loadFromRemoteSources>` elementu.</span><span class="sxs-lookup"><span data-stu-id="672a4-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="672a4-155">Jeśli aplikacja została skopiowana z sieci Web, jest oflagowana przez system Windows jako aplikacja sieci Web, nawet jeśli znajduje się na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="672a4-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="672a4-156">Można zmienić to oznaczenie, zmieniając jego właściwości pliku, lub można użyć `<loadFromRemoteSources>` elementu, aby nadać zestawowi pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="672a4-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="672a4-157">Alternatywnie można użyć <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metody do załadowania lokalnego zestawu, który został oflagowany przez system operacyjny jako załadowany z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="672a4-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="672a4-158">Użytkownik może uzyskać dostęp <xref:System.IO.FileLoadException> do aplikacji działającej w aplikacji na komputerze wirtualnym z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="672a4-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="672a4-159">Taka sytuacja może wystąpić podczas próby załadowania pliku z folderów połączonych na komputerze hostującym.</span><span class="sxs-lookup"><span data-stu-id="672a4-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="672a4-160">Może również wystąpić podczas próby załadowania pliku z folderu połączonego za pośrednictwem [usługi pulpitu zdalnego](https://go.microsoft.com/fwlink/?LinkId=182775) (usługi terminalowe).</span><span class="sxs-lookup"><span data-stu-id="672a4-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="672a4-161">Aby uniknąć wyjątku, ustaw `enabled` jako. `true`</span><span class="sxs-lookup"><span data-stu-id="672a4-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="672a4-162">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="672a4-162">Configuration file</span></span>

<span data-ttu-id="672a4-163">Ten element jest zazwyczaj używany w pliku konfiguracyjnym aplikacji, ale może być używany w innych plikach konfiguracji w zależności od kontekstu.</span><span class="sxs-lookup"><span data-stu-id="672a4-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="672a4-164">Aby uzyskać więcej informacji, zobacz artykuł [bardziej niejawne zastosowania zasad CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) w blogu dotyczącym zabezpieczeń programu .NET.</span><span class="sxs-lookup"><span data-stu-id="672a4-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="672a4-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="672a4-165">Example</span></span>

<span data-ttu-id="672a4-166">Poniższy przykład pokazuje, jak udzielić pełnego zaufania do zestawów ładowanych ze źródeł zdalnych.</span><span class="sxs-lookup"><span data-stu-id="672a4-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="672a4-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="672a4-167">See also</span></span>

- [<span data-ttu-id="672a4-168">Bardziej niejawne zastosowania zasad CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="672a4-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [<span data-ttu-id="672a4-169">Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy</span><span class="sxs-lookup"><span data-stu-id="672a4-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="672a4-170">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="672a4-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="672a4-171">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="672a4-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
