---
title: Wykonywanie równoczesne i wewnątrzprocesowe
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89dfe697f49e8144d15586cc9c1075f69d1f3a07
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816055"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="5d115-102">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="5d115-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="5d115-103">Począwszy od programu .NET Framework 4, możesz użyć w trakcie side-by-side hostingu do uruchamiania wielu wersji środowiska uruchomieniowego języka wspólnego (CLR) w ramach jednego procesu.</span><span class="sxs-lookup"><span data-stu-id="5d115-103">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="5d115-104">Domyślnie zarządzane składniki COM, uruchom z .NET Framework w wersji, które zostały skompilowane, niezależnie od wersji programu .NET Framework, który jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="5d115-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="5d115-105">Tło</span><span class="sxs-lookup"><span data-stu-id="5d115-105">Background</span></span>  
 <span data-ttu-id="5d115-106">.NET Framework zawsze ma pod warunkiem side-by-side hostowania dotycząca aplikacje kodu zarządzanego, ale przed .NET Framework 4 nie zapewniają tej funkcji dla składników COM zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="5d115-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="5d115-107">W przeszłości zarządzanych składników COM, które zostały załadowane do procesu został uruchomiony z wersją środowiska uruchomieniowego, który został już załadowany lub z najnowszej zainstalowanej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d115-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="5d115-108">Jeśli ta wersja nie jest zgodny ze składnikiem COM, składnik może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5d115-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="5d115-109">.NET Framework 4 zawiera nowe podejście do hostingu side-by-side, które gwarantuje, że następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5d115-109">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="5d115-110">Instalowanie nowej wersji programu .NET Framework nie ma wpływu na istniejące aplikacje.</span><span class="sxs-lookup"><span data-stu-id="5d115-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="5d115-111">Aplikacje są uruchamiane z wersją programu .NET Framework, które zostały skompilowane.</span><span class="sxs-lookup"><span data-stu-id="5d115-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="5d115-112">Używają nowej wersji programu .NET Framework, chyba że wyraźnie kierowany Aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="5d115-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="5d115-113">Jednak jest łatwiej aplikacji do przejścia do korzystania z nowej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d115-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="5d115-114">Wpływ na użytkowników i deweloperów</span><span class="sxs-lookup"><span data-stu-id="5d115-114">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="5d115-115">**Użytkownicy końcowi i Administratorzy systemu**.</span><span class="sxs-lookup"><span data-stu-id="5d115-115">**End users and system administrators**.</span></span> <span data-ttu-id="5d115-116">Ci użytkownicy mogą teraz mają większą pewność, że przy instalacji nowej wersji środowiska uruchomieniowego, niezależnie od siebie lub za pomocą aplikacji, nie będzie mieć żadnego wpływu na swoich komputerach.</span><span class="sxs-lookup"><span data-stu-id="5d115-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="5d115-117">Istniejące aplikacje, będą w dalszym ciągu działać tak jak przed.</span><span class="sxs-lookup"><span data-stu-id="5d115-117">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="5d115-118">**Deweloperzy aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="5d115-118">**Application developers**.</span></span> <span data-ttu-id="5d115-119">Hosting Side-by-side prawie nie ma wpływu na deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d115-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="5d115-120">Domyślnie aplikacje zawsze uruchamiana w wersji programu .NET Framework, w których zostały zbudowane; to nie została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="5d115-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="5d115-121">Jednakże, deweloperzy mogą zmienić to zachowanie i skierować aplikację do uruchamiania w nowszej wersji programu .NET Framework (zobacz [Scenariusz 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="5d115-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="5d115-122">**Deweloperów bibliotek i konsumentów**.</span><span class="sxs-lookup"><span data-stu-id="5d115-122">**Library developers and consumers**.</span></span> <span data-ttu-id="5d115-123">Side-by-side hostingu nie rozwiązuje problemy ze zgodnością napotykane przez deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5d115-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="5d115-124">Biblioteka, która jest ładowane bezpośrednio przez aplikację — za pośrednictwem bezpośredniego odwołania lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> wywołania — będzie później nadal używać środowiska uruchomieniowego <xref:System.AppDomain> jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="5d115-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="5d115-125">Należy przetestować bibliotek względem wszystkich wersji programu .NET Framework, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5d115-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="5d115-126">Jeśli aplikacja jest skompilowana przy użyciu środowiska uruchomieniowego .NET Framework 4, ale zawiera bibliotekę, który został zbudowany przy użyciu starszych środowiska uruchomieniowego, tej biblioteki będzie używać .NET Framework 4 środowisko uruchomieniowe także.</span><span class="sxs-lookup"><span data-stu-id="5d115-126">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="5d115-127">Jednak jeśli masz aplikację, która została skompilowana przy użyciu starszych środowisko uruchomieniowe i Biblioteka, który został zbudowany przy użyciu programu .NET Framework 4, należy wymusić aplikacji również używać programu .NET Framework 4 (zobacz [Scenariusz 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="5d115-127">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="5d115-128">**Zarządzane Deweloperzy składników COM**.</span><span class="sxs-lookup"><span data-stu-id="5d115-128">**Managed COM component developers**.</span></span> <span data-ttu-id="5d115-129">W przeszłości składniki COM zarządzane automatycznie została uruchomiona przy użyciu najnowszej wersji środowiska uruchomieniowego zainstalowanego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5d115-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="5d115-130">Można teraz wykonać składników modelu COM z wersją środowiska uruchomieniowego, które zostały skompilowane.</span><span class="sxs-lookup"><span data-stu-id="5d115-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="5d115-131">Jak pokazano w poniższej tabeli, składników, które zostały utworzone przy użyciu platformy .NET Framework w wersji 1.1, można uruchomić równolegle składniki w wersji 4, ale nie działają one w wersji 2.0, 3.0 lub 3.5 składników, ponieważ side-by-side hostingu nie jest dostępny dla osób wersje.</span><span class="sxs-lookup"><span data-stu-id="5d115-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="5d115-132">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5d115-132">.NET Framework version</span></span>|<span data-ttu-id="5d115-133">1.1</span><span class="sxs-lookup"><span data-stu-id="5d115-133">1.1</span></span>|<span data-ttu-id="5d115-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="5d115-134">2.0 - 3.5</span></span>|<span data-ttu-id="5d115-135">4</span><span class="sxs-lookup"><span data-stu-id="5d115-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="5d115-136">1.1</span><span class="sxs-lookup"><span data-stu-id="5d115-136">1.1</span></span>|<span data-ttu-id="5d115-137">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="5d115-137">Not applicable</span></span>|<span data-ttu-id="5d115-138">Nie</span><span class="sxs-lookup"><span data-stu-id="5d115-138">No</span></span>|<span data-ttu-id="5d115-139">Tak</span><span class="sxs-lookup"><span data-stu-id="5d115-139">Yes</span></span>|  
    |<span data-ttu-id="5d115-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="5d115-140">2.0 - 3.5</span></span>|<span data-ttu-id="5d115-141">Nie</span><span class="sxs-lookup"><span data-stu-id="5d115-141">No</span></span>|<span data-ttu-id="5d115-142">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="5d115-142">Not applicable</span></span>|<span data-ttu-id="5d115-143">Tak</span><span class="sxs-lookup"><span data-stu-id="5d115-143">Yes</span></span>|  
    |<span data-ttu-id="5d115-144">4</span><span class="sxs-lookup"><span data-stu-id="5d115-144">4</span></span>|<span data-ttu-id="5d115-145">Yes</span><span class="sxs-lookup"><span data-stu-id="5d115-145">Yes</span></span>|<span data-ttu-id="5d115-146">Yes</span><span class="sxs-lookup"><span data-stu-id="5d115-146">Yes</span></span>|<span data-ttu-id="5d115-147">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="5d115-147">Not applicable</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="5d115-148">Wersje programu .NET framework 3.0 i 3.5 są tworzone przyrostowo w wersji 2.0 i nie trzeba uruchamiać równolegle.</span><span class="sxs-lookup"><span data-stu-id="5d115-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="5d115-149">Te założenia mają taką samą wersję.</span><span class="sxs-lookup"><span data-stu-id="5d115-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="5d115-150">Typowe scenariusze Side-by-Side hostingu</span><span class="sxs-lookup"><span data-stu-id="5d115-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="5d115-151">**Scenariusz 1:** Aplikacji natywnej używającej składniki COM, utworzone w starszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d115-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="5d115-152">Zainstalowane wersje programu .NET framework: .NET Framework 4 i wszystkich innych wersji systemu .NET Framework używanego przez składniki COM.</span><span class="sxs-lookup"><span data-stu-id="5d115-152">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="5d115-153">Co należy zrobić: W tym scenariuszu nic nie rób.</span><span class="sxs-lookup"><span data-stu-id="5d115-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="5d115-154">Składniki COM będą uruchamiane przy użyciu wersji programu .NET Framework zostały zarejestrowane w usłudze.</span><span class="sxs-lookup"><span data-stu-id="5d115-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="5d115-155">**Scenariusz 2**: Zarządzana aplikacja skompilowana przy użyciu platformy .NET Framework 2.0 z dodatkiem SP1, który chcesz uruchomić z [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ale są gotowi do uruchamiania na .NET Framework 4 nie jest w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="5d115-155">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="5d115-156">Zainstalowane wersje programu .NET framework: Wcześniejszej wersji programu .NET Framework i .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5d115-156">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="5d115-157">Co należy zrobić: W [pliku konfiguracji aplikacji](../../../docs/framework/configure-apps/index.md) w katalogu aplikacji za pomocą [ \<uruchamiania > element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) i [ \<supportedRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) ustawione w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5d115-157">What to do: In the [application configuration file](../../../docs/framework/configure-apps/index.md) in the application directory, use the [\<startup> element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="5d115-158">**Scenariusz 3:** Aplikacji natywnej używającej składniki COM, utworzone w starszych wersjach programu .NET Framework, która ma zostać uruchomiony za pomocą programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5d115-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="5d115-159">Zainstalowane wersje programu .NET framework: .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5d115-159">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="5d115-160">Co należy zrobić: W pliku konfiguracyjnym aplikacji w katalogu aplikacji, należy użyć `<startup>` element z `useLegacyV2RuntimeActivationPolicy` ustawioną wartość atrybutu `true` i `<supportedRuntime>` element jest ustawiony w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5d115-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="5d115-161">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d115-161">Example</span></span>  
 <span data-ttu-id="5d115-162">W poniższym przykładzie pokazano niezarządzany host COM, działającego zarządzanego składnika COM za pomocą wersji programu .NET Framework, który składnik był skompilowany do użycia.</span><span class="sxs-lookup"><span data-stu-id="5d115-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="5d115-163">Aby uruchomić poniższy przykład, skompiluj i zarejestruj poniższe zarządzanego składnika COM za pomocą programu .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="5d115-163">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="5d115-164">Można zarejestrować składnika, na **projektu** menu, kliknij przycisk **właściwości**, kliknij przycisk **kompilacji** , a następnie wybierz pozycję **Zarejestruj dla współdziałania COM**pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="5d115-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="5d115-165">Skompiluj następujący niezarządzanej aplikacji C++, które uaktywnia się obiekt COM, który jest tworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5d115-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
```cpp
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
  
## <a name="see-also"></a><span data-ttu-id="5d115-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d115-166">See also</span></span>

- [<span data-ttu-id="5d115-167">\<Uruchamianie > Element</span><span class="sxs-lookup"><span data-stu-id="5d115-167">\<startup> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="5d115-168">\<supportedRuntime> Element</span><span class="sxs-lookup"><span data-stu-id="5d115-168">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
