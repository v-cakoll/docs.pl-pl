---
title: Wykonywanie równoczesne i wewnątrzprocesowe
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 5ca2f03576946a23b3133bbe7532d46c4ad758ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181663"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="67b7f-102">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="67b7f-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="67b7f-103">Począwszy od programu .NET Framework 4, można użyć hostingu obok siebie w trakcie procesu, aby uruchomić wiele wersji środowiska wykonawczego języka wspólnego (CLR) w jednym procesie.</span><span class="sxs-lookup"><span data-stu-id="67b7f-103">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="67b7f-104">Domyślnie zarządzane składniki COM są uruchamiane z wersją programu .NET Framework, z którą zostały zbudowane, niezależnie od wersji programu .NET Framework, która jest ładowana dla procesu.</span><span class="sxs-lookup"><span data-stu-id="67b7f-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="67b7f-105">Tło</span><span class="sxs-lookup"><span data-stu-id="67b7f-105">Background</span></span>  
 <span data-ttu-id="67b7f-106">.NET Framework zawsze zapewniał hosting side-by-side dla aplikacji kodu zarządzanego, ale przed programem .NET Framework 4 nie zapewniał tej funkcji dla zarządzanych składników COM.</span><span class="sxs-lookup"><span data-stu-id="67b7f-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="67b7f-107">W przeszłości zarządzane składniki COM, które zostały załadowane do procesu, zostały uruchomione z wersją środowiska wykonawczego, która została już załadowana, lub z najnowszą zainstalowaną wersją programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67b7f-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="67b7f-108">Jeśli ta wersja nie jest zgodna ze składnikiem COM, składnik zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="67b7f-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="67b7f-109">.NET Framework 4 zapewnia nowe podejście do hostingu side-by-side, który zapewnia następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="67b7f-109">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="67b7f-110">Zainstalowanie nowej wersji programu .NET Framework nie ma wpływu na istniejące aplikacje.</span><span class="sxs-lookup"><span data-stu-id="67b7f-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="67b7f-111">Aplikacje są uruchamiane względem wersji programu .NET Framework, z których zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="67b7f-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="67b7f-112">Nie używają nowej wersji programu .NET Framework, chyba że zostanie to wyraźnie skierowane.</span><span class="sxs-lookup"><span data-stu-id="67b7f-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="67b7f-113">Jednak jest łatwiejsze dla aplikacji do przejścia do korzystania z nowej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67b7f-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="67b7f-114">Wpływ na użytkowników i programistów</span><span class="sxs-lookup"><span data-stu-id="67b7f-114">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="67b7f-115">**Użytkownicy końcowi i administratorzy systemu**.</span><span class="sxs-lookup"><span data-stu-id="67b7f-115">**End users and system administrators**.</span></span> <span data-ttu-id="67b7f-116">Ci użytkownicy mogą teraz mieć większą pewność, że podczas instalowania nowej wersji środowiska wykonawczego, niezależnie lub z aplikacją, nie będzie to miało wpływu na ich komputery.</span><span class="sxs-lookup"><span data-stu-id="67b7f-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="67b7f-117">Istniejące aplikacje będą nadal działać tak jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="67b7f-117">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="67b7f-118">**Deweloperzy aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="67b7f-118">**Application developers**.</span></span> <span data-ttu-id="67b7f-119">Hosting side-by-side nie ma prawie żadnego wpływu na deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67b7f-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="67b7f-120">Domyślnie aplikacje zawsze są uruchamiane względem wersji programu .NET Framework, na których zostały zbudowane; to się nie zmieniło.</span><span class="sxs-lookup"><span data-stu-id="67b7f-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="67b7f-121">Jednak deweloperzy mogą zastąpić to zachowanie i skierować aplikację do uruchomienia w ramach nowszej wersji programu .NET Framework (zobacz [scenariusz 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="67b7f-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="67b7f-122">**Deweloperzy bibliotek i konsumenci**.</span><span class="sxs-lookup"><span data-stu-id="67b7f-122">**Library developers and consumers**.</span></span> <span data-ttu-id="67b7f-123">Hosting side-by-side nie rozwiązuje problemów ze zgodnością, z którymi borykają się deweloperzy biblioteki.</span><span class="sxs-lookup"><span data-stu-id="67b7f-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="67b7f-124">Biblioteka, która jest ładowana bezpośrednio przez aplikację — za <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> pośrednictwem bezpośredniego odwołania lub wywołania <xref:System.AppDomain> — nadal używa środowiska wykonawczego, do którego jest ładowana.</span><span class="sxs-lookup"><span data-stu-id="67b7f-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="67b7f-125">Należy przetestować biblioteki na wszystkich wersjach programu .NET Framework, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="67b7f-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="67b7f-126">Jeśli aplikacja jest kompilowana przy użyciu środowiska uruchomieniowego .NET Framework 4, ale zawiera bibliotekę, która została zbudowana przy użyciu wcześniejszego środowiska wykonawczego, biblioteka ta będzie również używać środowiska uruchomieniowego .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="67b7f-126">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="67b7f-127">Jeśli jednak masz aplikację, która została zbudowana przy użyciu wcześniejszego środowiska uruchomieniowego i biblioteki, która została zbudowana przy użyciu programu .NET Framework 4, należy wymusić na aplikacji również użycie programu .NET Framework 4 (zobacz [scenariusz 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="67b7f-127">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="67b7f-128">**Zarządzali deweloperami składników COM**.</span><span class="sxs-lookup"><span data-stu-id="67b7f-128">**Managed COM component developers**.</span></span> <span data-ttu-id="67b7f-129">W przeszłości zarządzane składniki COM były automatycznie uruchamiane przy użyciu najnowszej wersji środowiska wykonawczego zainstalowanego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="67b7f-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="67b7f-130">Teraz można wykonać składniki COM względem wersji środowiska wykonawczego, z których zostały zbudowane.</span><span class="sxs-lookup"><span data-stu-id="67b7f-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="67b7f-131">Jak pokazano w poniższej tabeli, komponenty, które zostały zbudowane z .NET Framework w wersji 1.1, mogą być uruchamiane obok komponentów w wersji 4, ale nie mogą działać z komponentami w wersji 2.0, 3.0 lub 3.5, ponieważ hosting side-by-side nie jest dostępny dla tych, które nie są dostępne dla tych, którzy nie są dostępni. Wersje.</span><span class="sxs-lookup"><span data-stu-id="67b7f-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="67b7f-132">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="67b7f-132">.NET Framework version</span></span>|<span data-ttu-id="67b7f-133">1.1</span><span class="sxs-lookup"><span data-stu-id="67b7f-133">1.1</span></span>|<span data-ttu-id="67b7f-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="67b7f-134">2.0 - 3.5</span></span>|<span data-ttu-id="67b7f-135">4</span><span class="sxs-lookup"><span data-stu-id="67b7f-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="67b7f-136">1.1</span><span class="sxs-lookup"><span data-stu-id="67b7f-136">1.1</span></span>|<span data-ttu-id="67b7f-137">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="67b7f-137">Not applicable</span></span>|<span data-ttu-id="67b7f-138">Nie</span><span class="sxs-lookup"><span data-stu-id="67b7f-138">No</span></span>|<span data-ttu-id="67b7f-139">Tak</span><span class="sxs-lookup"><span data-stu-id="67b7f-139">Yes</span></span>|  
    |<span data-ttu-id="67b7f-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="67b7f-140">2.0 - 3.5</span></span>|<span data-ttu-id="67b7f-141">Nie</span><span class="sxs-lookup"><span data-stu-id="67b7f-141">No</span></span>|<span data-ttu-id="67b7f-142">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="67b7f-142">Not applicable</span></span>|<span data-ttu-id="67b7f-143">Tak</span><span class="sxs-lookup"><span data-stu-id="67b7f-143">Yes</span></span>|  
    |<span data-ttu-id="67b7f-144">4</span><span class="sxs-lookup"><span data-stu-id="67b7f-144">4</span></span>|<span data-ttu-id="67b7f-145">Tak</span><span class="sxs-lookup"><span data-stu-id="67b7f-145">Yes</span></span>|<span data-ttu-id="67b7f-146">Tak</span><span class="sxs-lookup"><span data-stu-id="67b7f-146">Yes</span></span>|<span data-ttu-id="67b7f-147">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="67b7f-147">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="67b7f-148">.NET Framework wersje 3.0 i 3.5 są tworzone przyrostowo w wersji 2.0 i nie trzeba uruchamiać obok siebie.</span><span class="sxs-lookup"><span data-stu-id="67b7f-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="67b7f-149">Są to z natury tej samej wersji.</span><span class="sxs-lookup"><span data-stu-id="67b7f-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="67b7f-150">Typowe scenariusze hostingu side-by-side</span><span class="sxs-lookup"><span data-stu-id="67b7f-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="67b7f-151">**Scenariusz 1:** Natywna aplikacja, która używa składników COM utworzonych we wcześniejszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67b7f-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="67b7f-152">Zainstalowano wersje programu .NET Framework: program .NET Framework 4 i wszystkie inne wersje programu .NET Framework używane przez składniki COM.</span><span class="sxs-lookup"><span data-stu-id="67b7f-152">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="67b7f-153">Co zrobić: W tym scenariuszu nic nie rób.</span><span class="sxs-lookup"><span data-stu-id="67b7f-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="67b7f-154">Składniki COM będą uruchamiane z wersją programu .NET Framework, w których zostały zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="67b7f-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="67b7f-155">**Scenariusz 2:** Zarządzana aplikacja zbudowana z .NET Framework 2.0 SP1, który wolisz uruchomić z .NET Framework 2.0, ale są chętni do uruchomienia w programie .NET Framework 4, jeśli wersja 2.0 nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="67b7f-155">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="67b7f-156">Zainstalowano wersje programu .NET Framework: wcześniejsza wersja programu .NET Framework i programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="67b7f-156">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="67b7f-157">Co należy zrobić: W [pliku konfiguracji aplikacji](../configure-apps/index.md) w katalogu aplikacji użyj elementu [ \<> uruchamiania](../configure-apps/file-schema/startup/startup-element.md) i [ \<obsługiwanego elementu>runtime](../configure-apps/file-schema/startup/supportedruntime-element.md) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="67b7f-157">What to do: In the [application configuration file](../configure-apps/index.md) in the application directory, use the [\<startup> element](../configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="67b7f-158">**Scenariusz 3:** Natywna aplikacja, która używa składników COM utworzonych z wcześniejszymi wersjami programu .NET Framework, które mają być uruchamiane za pomocą programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="67b7f-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="67b7f-159">Zainstalowano wersje programu .NET Framework: program .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="67b7f-159">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="67b7f-160">Co należy zrobić: W pliku konfiguracji aplikacji w `<startup>` katalogu aplikacji `useLegacyV2RuntimeActivationPolicy` użyj elementu `true` z `<supportedRuntime>` atrybutem ustawionym do i zestawu elementów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="67b7f-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="67b7f-161">Przykład</span><span class="sxs-lookup"><span data-stu-id="67b7f-161">Example</span></span>  
 <span data-ttu-id="67b7f-162">W poniższym przykładzie pokazano niezarządzanego hosta COM, który jest uruchomiony składnik COM zarządzane przy użyciu wersji programu .NET Framework, który składnik został skompilowany do użycia.</span><span class="sxs-lookup"><span data-stu-id="67b7f-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="67b7f-163">Aby uruchomić poniższy przykład, skompiluj i zarejestruj następujący zarządzany składnik COM przy użyciu programu .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="67b7f-163">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="67b7f-164">Aby zarejestrować składnik, w menu **Projekt** kliknij polecenie **Właściwości**, kliknij kartę **Kompilacja,** a następnie zaznacz pole wyboru **Zarejestruj się dla współdziałania COM.**</span><span class="sxs-lookup"><span data-stu-id="67b7f-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
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
  
 <span data-ttu-id="67b7f-165">Skompiluj następującą niezarządzaną aplikację C++, która aktywuje obiekt COM, który jest tworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="67b7f-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67b7f-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67b7f-166">See also</span></span>

- [<span data-ttu-id="67b7f-167">\<element> uruchamiania</span><span class="sxs-lookup"><span data-stu-id="67b7f-167">\<startup> Element</span></span>](../configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="67b7f-168">\<supportedRuntime> Element</span><span class="sxs-lookup"><span data-stu-id="67b7f-168">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
