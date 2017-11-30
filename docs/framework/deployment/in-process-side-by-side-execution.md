---
title: "Wykonywanie równoczesne i wewnątrzprocesowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fa65be2eee481e20231bacb5d0861fa3d2c03f92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="52587-102">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="52587-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="52587-103">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć w trakcie side-by-side hosting do uruchamiania wielu wersji środowisko uruchomieniowe języka wspólnego (CLR) w ramach jednego procesu.</span><span class="sxs-lookup"><span data-stu-id="52587-103">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="52587-104">Domyślnie zarządzane składniki COM działać z wersją .NET Framework, które ich nie zostały skompilowane, niezależnie od wersji programu .NET Framework, który jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="52587-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="52587-105">Tło</span><span class="sxs-lookup"><span data-stu-id="52587-105">Background</span></span>  
 <span data-ttu-id="52587-106">.NET Framework zawsze ma podany side-by-side hosting dla zarządzanego kodu aplikacji, ale przed wysłaniem [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], nie zapewniają te funkcje składników COM zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="52587-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="52587-107">W przeszłości zarządzane składniki COM, które zostały załadowane do procesu został uruchomiony z wersją środowiska uruchomieniowego, który został już załadowany lub z najnowszej zainstalowanej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52587-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="52587-108">Jeśli ta wersja nie jest zgodny z składnika modelu COM, składnik nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="52587-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="52587-109">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Udostępnia nowe podejście do hostingu side-by-side, który zapewnia następujące:</span><span class="sxs-lookup"><span data-stu-id="52587-109">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
-   <span data-ttu-id="52587-110">Instalowanie nowej wersji programu .NET Framework nie ma wpływu na istniejące aplikacje.</span><span class="sxs-lookup"><span data-stu-id="52587-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
-   <span data-ttu-id="52587-111">Aplikacje są uruchamiane z wersją programu .NET Framework, które zostały skompilowane.</span><span class="sxs-lookup"><span data-stu-id="52587-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="52587-112">Używają nowej wersji programu .NET Framework, chyba że wyraźnie skierowane w tym celu.</span><span class="sxs-lookup"><span data-stu-id="52587-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="52587-113">Jednak jest łatwiejsze do przejścia aplikacji przy użyciu nowej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52587-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="52587-114">Wpływ na użytkowników i deweloperów</span><span class="sxs-lookup"><span data-stu-id="52587-114">Effects on Users and Developers</span></span>  
  
-   <span data-ttu-id="52587-115">**Użytkownicy końcowi i Administratorzy systemu**.</span><span class="sxs-lookup"><span data-stu-id="52587-115">**End users and system administrators**.</span></span> <span data-ttu-id="52587-116">Ci użytkownicy mają teraz większa pewność, że przy instalacji nowej wersji środowiska uruchomieniowego można niezależnie lub za pomocą aplikacji, jego zostanie nie mają wpływu na swoich komputerach.</span><span class="sxs-lookup"><span data-stu-id="52587-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="52587-117">Istniejące aplikacje będą nadal działać tak jak przed.</span><span class="sxs-lookup"><span data-stu-id="52587-117">Existing applications will continue to run as they did before.</span></span>  
  
-   <span data-ttu-id="52587-118">**Deweloperzy aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="52587-118">**Application developers**.</span></span> <span data-ttu-id="52587-119">Hosting Side-by-side prawie nie ma wpływu na deweloperzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52587-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="52587-120">Domyślnie aplikacje zawsze uruchamiana w wersji programu .NET Framework, że zostały zbudowane na; nie została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="52587-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="52587-121">Jednak deweloperzy mogą zmienić to zachowanie i skierować aplikację do uruchamiania w nowszej wersji programu .NET Framework (zobacz [Scenariusz 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="52587-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
-   <span data-ttu-id="52587-122">**Biblioteka deweloperów i konsumentów**.</span><span class="sxs-lookup"><span data-stu-id="52587-122">**Library developers and consumers**.</span></span> <span data-ttu-id="52587-123">Hosting Side-by-side nie rozwiązuje problemy ze zgodnością napotykane przez deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="52587-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="52587-124">Biblioteki, która jest bezpośrednio ładowany przez aplikację — poprzez bezpośrednie odwołanie lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> wywołać — będzie później nadal używać środowiska wykonawczego o <xref:System.AppDomain> został załadowany.</span><span class="sxs-lookup"><span data-stu-id="52587-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="52587-125">Należy przetestować bibliotek względem wszystkich wersji platformy .NET, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="52587-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="52587-126">Jeśli aplikacja została skompilowana przy użyciu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] środowiska uruchomieniowego zawiera jednak bibliotekę został zbudowany przy użyciu wcześniejszych środowiska uruchomieniowego, użyje tej biblioteki [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] również w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="52587-126">If an application is compiled using the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime but includes a library that was built using an earlier runtime, that library will use the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime as well.</span></span> <span data-ttu-id="52587-127">Jednak jeśli masz aplikację, która została skompilowana przy użyciu wcześniejszych środowiska uruchomieniowego i biblioteki, który został utworzony przy użyciu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], należy wymusić aplikacji można również użyć [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (zobacz [Scenariusz 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="52587-127">However, if you have an application that was built using an earlier runtime and a library that was built using the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], you must force your application to also use the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (see [scenario 3](#scenarios)).</span></span>  
  
-   <span data-ttu-id="52587-128">**Zarządzane deweloperzy składnika COM**.</span><span class="sxs-lookup"><span data-stu-id="52587-128">**Managed COM component developers**.</span></span> <span data-ttu-id="52587-129">W przeszłości zarządzane składniki COM automatycznie została uruchomiona przy użyciu najnowszej wersji środowiska uruchomieniowego zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="52587-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="52587-130">Można teraz wykonać składniki modelu COM z wersją środowiska uruchomieniowego, które zostały skompilowane.</span><span class="sxs-lookup"><span data-stu-id="52587-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="52587-131">Jak pokazano w poniższej tabeli, składników, które nie zostały skompilowane dla platformy .NET Framework w wersji 1.1 można uruchomić równolegle składniki w wersji 4, ale ich nie można uruchomić w wersji 2.0, 3.0 lub 3.5 składników, ponieważ side-by-side hostingu nie jest dostępna dla osób wersje.</span><span class="sxs-lookup"><span data-stu-id="52587-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="52587-132">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52587-132">.NET Framework version</span></span>|<span data-ttu-id="52587-133">1.1</span><span class="sxs-lookup"><span data-stu-id="52587-133">1.1</span></span>|<span data-ttu-id="52587-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="52587-134">2.0 - 3.5</span></span>|<span data-ttu-id="52587-135">4</span><span class="sxs-lookup"><span data-stu-id="52587-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="52587-136">1.1</span><span class="sxs-lookup"><span data-stu-id="52587-136">1.1</span></span>|<span data-ttu-id="52587-137">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="52587-137">Not applicable</span></span>|<span data-ttu-id="52587-138">Nie</span><span class="sxs-lookup"><span data-stu-id="52587-138">No</span></span>|<span data-ttu-id="52587-139">Tak</span><span class="sxs-lookup"><span data-stu-id="52587-139">Yes</span></span>|  
    |<span data-ttu-id="52587-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="52587-140">2.0 - 3.5</span></span>|<span data-ttu-id="52587-141">Nie</span><span class="sxs-lookup"><span data-stu-id="52587-141">No</span></span>|<span data-ttu-id="52587-142">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="52587-142">Not applicable</span></span>|<span data-ttu-id="52587-143">Tak</span><span class="sxs-lookup"><span data-stu-id="52587-143">Yes</span></span>|  
    |<span data-ttu-id="52587-144">4</span><span class="sxs-lookup"><span data-stu-id="52587-144">4</span></span>|<span data-ttu-id="52587-145">Tak</span><span class="sxs-lookup"><span data-stu-id="52587-145">Yes</span></span>|<span data-ttu-id="52587-146">Tak</span><span class="sxs-lookup"><span data-stu-id="52587-146">Yes</span></span>|<span data-ttu-id="52587-147">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="52587-147">Not applicable</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="52587-148">Wersje programu .NET framework 3.0 i 3.5 są tworzone przyrostowo w wersji 2.0 i nie trzeba uruchomić obok siebie.</span><span class="sxs-lookup"><span data-stu-id="52587-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="52587-149">Są z założenia tej samej wersji.</span><span class="sxs-lookup"><span data-stu-id="52587-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="52587-150">Typowe scenariusze hostingu Side-by-Side</span><span class="sxs-lookup"><span data-stu-id="52587-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
-   <span data-ttu-id="52587-151">**Scenariusz 1:** aplikacji natywnej używającej składniki COM utworzone we wcześniejszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52587-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="52587-152">Zainstalowane wersje .NET framework: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] i wszystkich wersji platformy .NET używanego przez składniki COM.</span><span class="sxs-lookup"><span data-stu-id="52587-152">.NET Framework versions installed: The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="52587-153">Co należy zrobić: W tym scenariuszu, nic nie rób.</span><span class="sxs-lookup"><span data-stu-id="52587-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="52587-154">Składniki modelu COM będą uruchamiane z wersją programu .NET Framework w zarejestrowani z.</span><span class="sxs-lookup"><span data-stu-id="52587-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
-   <span data-ttu-id="52587-155">**Scenariusz 2**: zarządzanych aplikacji skompilowanej za pomocą [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] , który chcesz uruchomić z [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ale nie jest gotowa do uruchomienia na [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Jeśli nie jest w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="52587-155">**Scenario 2**: Managed application built with the [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] that you would prefer to run with the [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], but are willing to run on the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="52587-156">Zainstalowane wersje .NET framework: starszej wersji programu .NET Framework i [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52587-156">.NET Framework versions installed: An earlier version of the .NET Framework and the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="52587-157">Co należy zrobić: W [pliku konfiguracji aplikacji](../../../docs/framework/configure-apps/index.md) w katalogu aplikacji, użyj [ \<uruchamiania > element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) i [ \<supportedRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) ustawione w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="52587-157">What to do: In the [application configuration file](../../../docs/framework/configure-apps/index.md) in the application directory, use the [\<startup> element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="52587-158">**Scenariusz 3:** natywnych aplikacji, która używa składniki COM utworzone we wcześniejszych wersjach programu .NET Framework, która ma zostać uruchomione z [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52587-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="52587-159">Zainstalowane wersje .NET framework: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52587-159">.NET Framework versions installed: The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="52587-160">Co należy zrobić: W pliku konfiguracyjnym aplikacji w katalogu aplikacji, użyj `<startup>` element z `useLegacyV2RuntimeActivationPolicy` ustawić atrybutu `true` i `<supportedRuntime>` element ustawiony w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="52587-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="52587-161">Przykład</span><span class="sxs-lookup"><span data-stu-id="52587-161">Example</span></span>  
 <span data-ttu-id="52587-162">W poniższym przykładzie pokazano niezarządzane COM host, na którym działa zarządzanego składnika modelu COM przy użyciu wersji programu .NET Framework, która składnik został skompilowany do użycia.</span><span class="sxs-lookup"><span data-stu-id="52587-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="52587-163">Aby uruchomić poniższy przykład, kompilowania i zarejestrować następujące zarządzanych za pomocą składnika COM [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52587-163">To run the following example, compile and register the following managed COM component using the [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].</span></span> <span data-ttu-id="52587-164">Aby zarejestrować składnika, na **projektu** menu, kliknij przycisk **właściwości**, kliknij przycisk **kompilacji** , a następnie wybierz **Zarejestruj dla międzyoperacyjności z modelem COM**pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="52587-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="52587-165">Kompiluj następujące niezarządzanej aplikacji C++, które aktywuje obiektu COM, który jest utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="52587-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
```  
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");   
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="52587-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52587-166">See Also</span></span>  
 [<span data-ttu-id="52587-167">\<Uruchamianie > — Element</span><span class="sxs-lookup"><span data-stu-id="52587-167">\<startup> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
 [<span data-ttu-id="52587-168">\<supportedRuntime > — Element</span><span class="sxs-lookup"><span data-stu-id="52587-168">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
