---
title: '&lt;loadFromRemoteSources&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0d442f71a0e2fc7deacd9aaa02cfba7b66f2349
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a><span data-ttu-id="28eeb-102">&lt;loadFromRemoteSources&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="28eeb-102">&lt;loadFromRemoteSources&gt; Element</span></span>
<span data-ttu-id="28eeb-103">Określa, czy zestawy ze źródła zdalnego należy przyznać pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="28eeb-103">Specifies whether assemblies from remote sources should be granted full trust.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28eeb-104">Jeśli były kierowane do tego tematu, z powodu komunikat o błędzie na liście błędów projektu programu Visual Studio lub błąd kompilacji, zobacz [porady: Użyj zestawu z sieci Web w programie Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).</span><span class="sxs-lookup"><span data-stu-id="28eeb-104">If you were directed to this topic because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).</span></span>  
  
 <span data-ttu-id="28eeb-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="28eeb-105">\<configuration></span></span>  
<span data-ttu-id="28eeb-106">\<runtime></span><span class="sxs-lookup"><span data-stu-id="28eeb-106">\<runtime></span></span>  
<span data-ttu-id="28eeb-107">\<loadFromRemoteSources ></span><span class="sxs-lookup"><span data-stu-id="28eeb-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28eeb-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="28eeb-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28eeb-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="28eeb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="28eeb-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="28eeb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28eeb-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28eeb-111">Attributes</span></span>  
  
|<span data-ttu-id="28eeb-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28eeb-112">Attribute</span></span>|<span data-ttu-id="28eeb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="28eeb-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="28eeb-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="28eeb-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="28eeb-115">Określa, czy zestaw, który jest ładowany ze źródła zdalnego należy przyznać pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="28eeb-115">Specifies whether an assembly that is loaded from remote sources should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="28eeb-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="28eeb-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="28eeb-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="28eeb-117">Value</span></span>|<span data-ttu-id="28eeb-118">Opis</span><span class="sxs-lookup"><span data-stu-id="28eeb-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="28eeb-119">Nie przyznać pełne zaufanie do aplikacji z zdalnych źródeł.</span><span class="sxs-lookup"><span data-stu-id="28eeb-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="28eeb-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="28eeb-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="28eeb-121">Przyznać pełne zaufanie do aplikacji z zdalnych źródeł.</span><span class="sxs-lookup"><span data-stu-id="28eeb-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28eeb-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="28eeb-122">Child Elements</span></span>  
 <span data-ttu-id="28eeb-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="28eeb-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28eeb-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="28eeb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="28eeb-125">Element</span><span class="sxs-lookup"><span data-stu-id="28eeb-125">Element</span></span>|<span data-ttu-id="28eeb-126">Opis</span><span class="sxs-lookup"><span data-stu-id="28eeb-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="28eeb-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28eeb-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="28eeb-128">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28eeb-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28eeb-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28eeb-129">Remarks</span></span>  
 <span data-ttu-id="28eeb-130">.NET Framework w wersji 3.5 i wcześniejszymi wersjami Jeśli załadować zestawu z lokalizacji zdalnej, zestaw może działać częściowo zaufany za pomocą zestaw uprawnień, która była uzależniona od strefy, w której została załadowana.</span><span class="sxs-lookup"><span data-stu-id="28eeb-130">In the .NET Framework version 3.5 and earlier versions, if you loaded an assembly from a remote location, the assembly would run partially trusted with a grant set that depended on the zone in which it was loaded.</span></span> <span data-ttu-id="28eeb-131">Na przykład jeśli zestaw jest ładowany z witryny internetowej, jego został załadowany w strefie Internet i przyznane zestaw uprawnień internetowych.</span><span class="sxs-lookup"><span data-stu-id="28eeb-131">For example, if you loaded an assembly from a website, it was loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="28eeb-132">Innymi słowy wykonane w piaskownicy Internet.</span><span class="sxs-lookup"><span data-stu-id="28eeb-132">In other words, it executed in an Internet sandbox.</span></span> <span data-ttu-id="28eeb-133">Jeśli zostanie podjęta próba uruchomienia tego zestawu [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i nowszych wersjach, jest zgłaszany wyjątek; musi być jawnie tworzenia piaskownicy dla zestawu (zobacz [porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), lub uruchomić go w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="28eeb-133">If you try to run that assembly in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later versions, an exception is thrown; you must either explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), or run it in full trust.</span></span>  
  
 <span data-ttu-id="28eeb-134">`<loadFromRemoteSources>` Element umożliwia określenie, czy zestawy, które powinny zostać uruchomione częściowo zaufany w starszych wersjach programu .NET Framework są uruchamiane w pełni zaufane w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="28eeb-134">The `<loadFromRemoteSources>` element lets you specify that the assemblies that would have run partially trusted in earlier versions of the .NET Framework are to be run fully trusted in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="28eeb-135">Domyślnie zdalne zestawy nie są uruchamiane w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszych.</span><span class="sxs-lookup"><span data-stu-id="28eeb-135">By default, remote assemblies do not run in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span> <span data-ttu-id="28eeb-136">Do uruchamiania zdalnego zestawu, należy uruchomić go jako w pełni zaufany lub Utwórz piaskownicy <xref:System.AppDomain> do uruchamiania go.</span><span class="sxs-lookup"><span data-stu-id="28eeb-136">To run a remote assembly, you must either run it as fully trusted or create a sandboxed <xref:System.AppDomain> in which to run it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28eeb-137">W [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], zestawy w udziałach sieci lokalnej są domyślnie uruchamiane przy pełnym zaufaniu; nie należy włączyć `<loadFromRemoteSources>` elementu.</span><span class="sxs-lookup"><span data-stu-id="28eeb-137">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblies on local network shares are run as full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28eeb-138">Jeśli aplikacja został skopiowany z sieci web, jego oflagowane przez system Windows jako aplikacji sieci web, nawet wtedy, gdy znajduje się on na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="28eeb-138">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="28eeb-139">Określenie, że można zmienić, zmieniając właściwości pliku lub skorzystać z `<loadFromRemoteSources>` element, aby udzielić zestawu pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="28eeb-139">You can change that designation by changing the file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="28eeb-140">Alternatywnie, można użyć <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metody można załadować zestawu lokalnego, który system operacyjny został oznaczony jako załadowanych z sieci web.</span><span class="sxs-lookup"><span data-stu-id="28eeb-140">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>  
  
 <span data-ttu-id="28eeb-141">`enabled` Atrybutu dla tego elementu jest efektywne tylko wtedy, gdy zabezpieczenia dostępu kodu (CAS) jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="28eeb-141">The `enabled` attribute for this element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="28eeb-142">Domyślnie urzędów certyfikacji zasad jest wyłączone w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="28eeb-142">By default, CAS policy is disabled in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="28eeb-143">Jeśli ustawisz `enabled` do `true`, zdalne aplikacje są udzielane pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="28eeb-143">If you set `enabled` to `true`, remote applications are granted full trust.</span></span>  
  
 <span data-ttu-id="28eeb-144">Jeśli `<loadFromRemoteSources>``enabled` nie jest ustawiony na `true`, jest zwracany wyjątek w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="28eeb-144">If `<loadFromRemoteSources>``enabled` is not set to `true`, an exception is thrown under the following conditions:</span></span>  
  
-   <span data-ttu-id="28eeb-145">Zachowanie sandboxing bieżącej domeny różni się od jego zachowanie w [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28eeb-145">The sandboxing behavior of the current domain is different from its behavior in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span> <span data-ttu-id="28eeb-146">Wymaga to zasad CAS, które mają zostać wyłączone, a bieżąca domena nie powinien być w trybie piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="28eeb-146">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>  
  
-   <span data-ttu-id="28eeb-147">Trwa ładowanie zestawu nie pochodzi z `MyComputer` strefy.</span><span class="sxs-lookup"><span data-stu-id="28eeb-147">The assembly being loaded is not from the `MyComputer` zone.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28eeb-148">Mogą wystąpić <xref:System.IO.FileLoadException> w aplikacji Windows Virtual PC podczas próby załadowania pliku z połączonego folderów na komputerze hostingu.</span><span class="sxs-lookup"><span data-stu-id="28eeb-148">You may get a <xref:System.IO.FileLoadException> in a Windows Virtual PC application when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="28eeb-149">Ten błąd może również wystąpić, gdy próbuje załadować plik z folderu połączone za pośrednictwem [usług pulpitu zdalnego](http://go.microsoft.com/fwlink/?LinkId=182775) (usług terminalowych).</span><span class="sxs-lookup"><span data-stu-id="28eeb-149">This error may also occur when you try to load a file from a folder linked over [Remote Desktop Services](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="28eeb-150">Aby zapobiec wyjątek, ustaw `enabled` do `true`.</span><span class="sxs-lookup"><span data-stu-id="28eeb-150">To avoid the exception, set `enabled` to `true`.</span></span>  
  
 <span data-ttu-id="28eeb-151">Ustawienie `<loadFromRemoteSources>` elementu `true` uniemożliwia tego wyjątku z został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="28eeb-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="28eeb-152">Umożliwia określenie, że użytkownik nie używają środowisko uruchomieniowe języka wspólnego do piaskownicy załadowanych zestawów zabezpieczeń i mogą być dozwolone do wykonania jako pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="28eeb-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute as full trust.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="28eeb-153">Zestaw nie należy uruchamiać w trybie pełnego zaufania, nie należy ustawiać ten element konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="28eeb-153">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="28eeb-154">Zamiast tego utwórz piaskownicy <xref:System.AppDomain> w którym można załadować zestawu.</span><span class="sxs-lookup"><span data-stu-id="28eeb-154">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="28eeb-155">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="28eeb-155">Configuration File</span></span>  
 <span data-ttu-id="28eeb-156">Ten element jest zwykle używana w pliku konfiguracji aplikacji, ale mogą być używane w inne pliki konfiguracji, w zależności od kontekstu.</span><span class="sxs-lookup"><span data-stu-id="28eeb-156">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="28eeb-157">Aby uzyskać więcej informacji, zobacz artykuł [więcej niejawne korzysta z zasad CAS: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) w blogu .NET zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="28eeb-157">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28eeb-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="28eeb-158">Example</span></span>  
 <span data-ttu-id="28eeb-159">Poniższy przykład pokazuje, jak można przyznać pełne zaufanie do aplikacji z zdalnych źródeł.</span><span class="sxs-lookup"><span data-stu-id="28eeb-159">The following example shows how to grant full trust to applications from remote sources.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="28eeb-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28eeb-160">See Also</span></span>  
 [<span data-ttu-id="28eeb-161">Więcej niejawne używa zasad CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="28eeb-161">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [<span data-ttu-id="28eeb-162">Porady: uruchamianie częściowo zaufanego kodu w bibliotece</span><span class="sxs-lookup"><span data-stu-id="28eeb-162">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [<span data-ttu-id="28eeb-163">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="28eeb-163">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="28eeb-164">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="28eeb-164">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
