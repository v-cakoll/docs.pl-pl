---
title: <loadFromRemoteSources>, element
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568129f30267b212737ec8aa688cf882e19bbff
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675312"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="ba454-102">\<loadfromremotesources — > element</span><span class="sxs-lookup"><span data-stu-id="ba454-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="ba454-103">Określa, czy zestawy, ładowane z zdalnych źródeł może być przyznany pełnego zaufania w programie .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="ba454-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="ba454-104">Jeśli były kierowane do tego artykułu, ze względu na komunikat o błędzie na liście błędów projektu programu Visual Studio lub błąd kompilacji, zobacz [jak: Użyj zestawu z sieci Web w programie Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ba454-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
 <span data-ttu-id="ba454-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ba454-105">\<configuration></span></span>  
<span data-ttu-id="ba454-106">\<runtime></span><span class="sxs-lookup"><span data-stu-id="ba454-106">\<runtime></span></span>  
<span data-ttu-id="ba454-107">\<loadFromRemoteSources></span><span class="sxs-lookup"><span data-stu-id="ba454-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba454-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba454-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba454-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ba454-109">Attributes and elements</span></span>
 <span data-ttu-id="ba454-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ba454-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba454-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ba454-111">Attributes</span></span>  
  
|<span data-ttu-id="ba454-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ba454-112">Attribute</span></span>|<span data-ttu-id="ba454-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ba454-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ba454-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ba454-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ba454-115">Określa, czy zestaw, który jest ładowany ze źródła zdalnego należy przyznać pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="ba454-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ba454-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="ba454-116">enabled attribute</span></span>  
  
|<span data-ttu-id="ba454-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="ba454-117">Value</span></span>|<span data-ttu-id="ba454-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ba454-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ba454-119">Nie przyznawaj pełnego zaufania do aplikacji ze zdalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="ba454-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="ba454-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="ba454-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ba454-121">Przyznać pełne zaufanie do aplikacji ze zdalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="ba454-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba454-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ba454-122">Child elements</span></span>  
 <span data-ttu-id="ba454-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="ba454-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba454-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ba454-124">Parent elements</span></span>  
  
|<span data-ttu-id="ba454-125">Element</span><span class="sxs-lookup"><span data-stu-id="ba454-125">Element</span></span>|<span data-ttu-id="ba454-126">Opis</span><span class="sxs-lookup"><span data-stu-id="ba454-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ba454-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba454-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ba454-128">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ba454-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba454-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba454-129">Remarks</span></span>

<span data-ttu-id="ba454-130">W .NET Framework 3.5 i wcześniejszymi wersjami Jeśli zestaw jest ładowany z lokalizacji zdalnej, kod w zestawie jest uruchamiany w częściowej relacji zaufania z zestaw uprawnień, który zależy od strefy, z której jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="ba454-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="ba454-131">Na przykład jeśli zestaw jest ładowany z witryny sieci Web, go jest ładowany do strefy Internet i przyznane Internet zestaw uprawnień.</span><span class="sxs-lookup"><span data-stu-id="ba454-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="ba454-132">Innymi słowy wykonuje w piaskownicy Internet.</span><span class="sxs-lookup"><span data-stu-id="ba454-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="ba454-133">Począwszy od programu .NET Framework 4, zasady zabezpieczenia dostępu kodu jest wyłączona, a zestawy są ładowane w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="ba454-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="ba454-134">Zazwyczaj, to czy przyznać pełne zaufanie do zestawy, ładowane z <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodę, która wcześniej była piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="ba454-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="ba454-135">Aby temu zapobiec, możliwość uruchamiania kodu w zestawy, ładowane ze źródła zdalnego jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="ba454-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="ba454-136">Domyślnie, jeśli użytkownik podejmie próbę załadowania zestawu zdalnego <xref:System.IO.FileLoadException> z komunikatem o wyjątku, jak jest generowany, następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ba454-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

<span data-ttu-id="ba454-137">Aby załadować zestaw i wykonywanie kodu, należy:</span><span class="sxs-lookup"><span data-stu-id="ba454-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="ba454-138">Jawnie utworzyć piaskownicy dla zestawu (zobacz [jak: Uruchamianie częściowo zaufanego kodu w piaskownicy](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span><span class="sxs-lookup"><span data-stu-id="ba454-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="ba454-139">Uruchom kod zestawu w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="ba454-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="ba454-140">Możesz to zrobić, konfigurując `<loadFromRemoteSources>` elementu.</span><span class="sxs-lookup"><span data-stu-id="ba454-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="ba454-141">Dzięki temu można określić, że zestawy, które działają w częściowej relacji zaufania we wcześniejszych wersjach programu .NET Framework jest teraz uruchomione w trybie pełnego zaufania w .NET Framework 4 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="ba454-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba454-142">Jeśli zestaw nie jest uruchamiany w trybie pełnego zaufania, ten element konfiguracji nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="ba454-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="ba454-143">Zamiast tego utworzyć piaskownicy <xref:System.AppDomain> w którym można załadować zestawu.</span><span class="sxs-lookup"><span data-stu-id="ba454-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="ba454-144">`enabled` Atrybutu dla `<loadFromRemoteSources>` element jest efektywne tylko wtedy, gdy zabezpieczenia dostępu kodu (CAS) jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="ba454-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="ba454-145">Domyślnie urzędy certyfikacji zasad jest wyłączona w .NET Framework 4 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="ba454-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="ba454-146">Jeśli ustawisz `enabled` do `true`, zdalne zespoły są udzielane pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="ba454-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="ba454-147">Jeśli `enabled` nie jest ustawiony na `true`, <xref:System.IO.FileLoadException> jest zgłaszany w ramach jednej z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="ba454-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="ba454-148">Zachowanie piaskownicy bieżącej domeny różni się od jego zachowanie w programie .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="ba454-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="ba454-149">Wymaga to urzędów certyfikacji zasad jest wyłączona, a bieżąca domena nie należy go w trybie piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="ba454-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="ba454-150">Nie jest ładowany zestaw `MyComputer` strefy.</span><span class="sxs-lookup"><span data-stu-id="ba454-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="ba454-151">Ustawienie `<loadFromRemoteSources>` elementu `true` zapobiega ten wyjątek z zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="ba454-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="ba454-152">Pozwala określić, że nie polegasz na środowisko uruchomieniowe języka wspólnego do izolowanego załadowanych zestawów dla zabezpieczeń i mogą być dozwolone do wykonania w pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="ba454-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="ba454-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba454-153">Notes</span></span>

- <span data-ttu-id="ba454-154">W .NET Framework 4.5 i nowsze wersje zestawy w udziałach sieci lokalnej są uruchamiane w trybie pełnego zaufania domyślnie; nie trzeba włączyć `<loadFromRemoteSources>` elementu.</span><span class="sxs-lookup"><span data-stu-id="ba454-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="ba454-155">Jeśli wniosek został skopiowany z sieci web, jego zostanie oflagowana przez Windows jako aplikacji sieci web, nawet wtedy, gdy znajduje się na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="ba454-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="ba454-156">Oznaczenie tego można zmienić, zmieniając jego właściwości pliku, lub możesz użyć `<loadFromRemoteSources>` elementu, aby przyznać zestawu pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="ba454-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="ba454-157">Alternatywnie, można użyć <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metodę, aby załadować zestaw lokalnego, który system operacyjny został oznaczony jako załadowaniu z sieci web.</span><span class="sxs-lookup"><span data-stu-id="ba454-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="ba454-158">Możesz otrzymać <xref:System.IO.FileLoadException> w aplikacji, która działa w aplikacji Windows Virtual PC.</span><span class="sxs-lookup"><span data-stu-id="ba454-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="ba454-159">Może to nastąpić podczas próby załadowania pliku z połączonych folderów na komputerze hostingu.</span><span class="sxs-lookup"><span data-stu-id="ba454-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="ba454-160">Może również wystąpić podczas próby załadowania pliku z folderem połączone za pośrednictwem [usług pulpitu zdalnego](https://go.microsoft.com/fwlink/?LinkId=182775) (usług terminalowych).</span><span class="sxs-lookup"><span data-stu-id="ba454-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="ba454-161">Aby zapobiec wyjątek, ustaw `enabled` do `true`.</span><span class="sxs-lookup"><span data-stu-id="ba454-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="ba454-162">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ba454-162">Configuration file</span></span>

<span data-ttu-id="ba454-163">Ten element jest zwykle używana w pliku konfiguracyjnym aplikacji, ale mogą być używane w inne pliki konfiguracji, w zależności od kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ba454-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="ba454-164">Aby uzyskać więcej informacji, zobacz artykuł [więcej niejawne korzysta z urzędów certyfikacji zasad: loadfromremotesources —](https://go.microsoft.com/fwlink/p/?LinkId=266839) w blogu dotyczącym zabezpieczeń .NET.</span><span class="sxs-lookup"><span data-stu-id="ba454-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="ba454-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba454-165">Example</span></span>

<span data-ttu-id="ba454-166">Poniższy przykład pokazuje, jak udzielić pełnym zaufaniu zestawy, ładowane z zdalnych źródeł.</span><span class="sxs-lookup"><span data-stu-id="ba454-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="ba454-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba454-167">See also</span></span>

- [<span data-ttu-id="ba454-168">Więcej niejawne zastosowania zasady CAS: loadfromremotesources —</span><span class="sxs-lookup"><span data-stu-id="ba454-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [<span data-ttu-id="ba454-169">Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy</span><span class="sxs-lookup"><span data-stu-id="ba454-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="ba454-170">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ba454-170">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ba454-171">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ba454-171">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
