---
title: Wykonywanie równoczesne i wewnątrzprocesowe
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d9d77ef20090e007e22a0d2f90b29f32ff94b46
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911116"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="c06e6-102">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="c06e6-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="c06e6-103">Począwszy od .NET Framework 4, można użyć w procesie równoczesnego hostowania do uruchamiania wielu wersji środowiska uruchomieniowego języka wspólnego (CLR) w ramach jednego procesu.</span><span class="sxs-lookup"><span data-stu-id="c06e6-103">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="c06e6-104">Domyślnie zarządzane składniki COM są uruchamiane z .NET Framework wersją, z którą zostały skompilowane, niezależnie od wersji .NET Framework, która jest ładowana dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="c06e6-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="c06e6-105">Tło</span><span class="sxs-lookup"><span data-stu-id="c06e6-105">Background</span></span>  
 <span data-ttu-id="c06e6-106">.NET Framework zawsze udostępnia hosting równoczesny dla aplikacji z kodem zarządzanym, ale przed .NET Framework 4, nie zapewniał on funkcji zarządzanych składników COM.</span><span class="sxs-lookup"><span data-stu-id="c06e6-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="c06e6-107">W przeszłości zarządzane składniki COM, które zostały załadowane do procesu, działały z wersją środowiska uruchomieniowego, które zostało już załadowane lub z najnowszą zainstalowaną wersją .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c06e6-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="c06e6-108">Jeśli ta wersja nie jest zgodna ze składnikiem COM, składnik ten nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="c06e6-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="c06e6-109">.NET Framework 4 zawiera nowe podejście do hostingu równoczesnego, które zapewnia następujące działania:</span><span class="sxs-lookup"><span data-stu-id="c06e6-109">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="c06e6-110">Zainstalowanie nowej wersji .NET Framework nie ma wpływu na istniejące aplikacje.</span><span class="sxs-lookup"><span data-stu-id="c06e6-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="c06e6-111">Aplikacje działają w porównaniu z wersją .NET Framework, z którą zostały skompilowane.</span><span class="sxs-lookup"><span data-stu-id="c06e6-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="c06e6-112">Nie używają nowej wersji .NET Framework, chyba że jest to wyraźnie ukierunkowane.</span><span class="sxs-lookup"><span data-stu-id="c06e6-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="c06e6-113">Jest to jednak łatwiejsze w aplikacjach do przechodzenia do korzystania z nowej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c06e6-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="c06e6-114">Efekty dla użytkowników i deweloperów</span><span class="sxs-lookup"><span data-stu-id="c06e6-114">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="c06e6-115">**Użytkownicy końcowi i Administratorzy systemu**.</span><span class="sxs-lookup"><span data-stu-id="c06e6-115">**End users and system administrators**.</span></span> <span data-ttu-id="c06e6-116">Ci użytkownicy mogą teraz mieć większą pewność, że podczas instalowania nowej wersji środowiska uruchomieniowego niezależnie lub z aplikacją nie będą mieć wpływu na komputery.</span><span class="sxs-lookup"><span data-stu-id="c06e6-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="c06e6-117">Istniejące aplikacje będą nadal działać tak jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="c06e6-117">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="c06e6-118">**Deweloperzy aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="c06e6-118">**Application developers**.</span></span> <span data-ttu-id="c06e6-119">Hosting równoległy nie ma prawie żadnego wpływu na deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c06e6-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="c06e6-120">Domyślnie aplikacje są zawsze uruchamiane w porównaniu z wersją .NET Framework, w których zostały skompilowane; Ta zmiana nie została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="c06e6-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="c06e6-121">Deweloperzy mogą jednak zastąpić to zachowanie i skierować aplikację do uruchamiania w nowszej wersji .NET Framework (patrz [Scenariusz 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="c06e6-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="c06e6-122">**Deweloperzy biblioteki i konsumenci**.</span><span class="sxs-lookup"><span data-stu-id="c06e6-122">**Library developers and consumers**.</span></span> <span data-ttu-id="c06e6-123">Hosting równoległy nie rozwiązuje problemów ze zgodnością, które są używane przez deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c06e6-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="c06e6-124">Biblioteka, która jest bezpośrednio ładowana przez aplikację — albo za pośrednictwem bezpośredniego odwołania lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> wywołania — kontynuuje używanie środowiska uruchomieniowego, <xref:System.AppDomain> który jest ładowany do.</span><span class="sxs-lookup"><span data-stu-id="c06e6-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="c06e6-125">Należy przetestować biblioteki dla wszystkich wersji .NET Framework, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c06e6-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="c06e6-126">Jeśli aplikacja jest kompilowana przy użyciu środowiska uruchomieniowego .NET Framework 4, ale zawiera bibliotekę, która została skompilowana przy użyciu wcześniejszego środowiska uruchomieniowego, biblioteka będzie używać środowiska uruchomieniowego .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c06e6-126">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="c06e6-127">Jeśli jednak masz aplikację, która została skompilowana przy użyciu wcześniejszego środowiska uruchomieniowego i biblioteki, która została skompilowana przy użyciu .NET Framework 4, musisz wymusić, aby aplikacja korzystała również z .NET Framework 4 (patrz [Scenariusz 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="c06e6-127">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="c06e6-128">**Zarządzani Deweloperzy składników modelu COM**.</span><span class="sxs-lookup"><span data-stu-id="c06e6-128">**Managed COM component developers**.</span></span> <span data-ttu-id="c06e6-129">W przeszłości zarządzane składniki COM zostały automatycznie uruchomione przy użyciu najnowszej wersji środowiska uruchomieniowego zainstalowanej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c06e6-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="c06e6-130">Teraz można wykonywać składniki COM względem wersji środowiska uruchomieniowego, które zostały skompilowane przy użyciu programu.</span><span class="sxs-lookup"><span data-stu-id="c06e6-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="c06e6-131">Zgodnie z poniższą tabelą składniki, które zostały skompilowane przy użyciu .NET Framework w wersji 1,1 mogą działać obok składników w wersji 4, ale nie mogą być uruchamiane z wersjami 2,0, 3,0 lub 3,5, ponieważ nie są dostępne wersje.</span><span class="sxs-lookup"><span data-stu-id="c06e6-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="c06e6-132">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c06e6-132">.NET Framework version</span></span>|<span data-ttu-id="c06e6-133">1.1</span><span class="sxs-lookup"><span data-stu-id="c06e6-133">1.1</span></span>|<span data-ttu-id="c06e6-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="c06e6-134">2.0 - 3.5</span></span>|<span data-ttu-id="c06e6-135">4</span><span class="sxs-lookup"><span data-stu-id="c06e6-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="c06e6-136">1.1</span><span class="sxs-lookup"><span data-stu-id="c06e6-136">1.1</span></span>|<span data-ttu-id="c06e6-137">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="c06e6-137">Not applicable</span></span>|<span data-ttu-id="c06e6-138">Nie</span><span class="sxs-lookup"><span data-stu-id="c06e6-138">No</span></span>|<span data-ttu-id="c06e6-139">Tak</span><span class="sxs-lookup"><span data-stu-id="c06e6-139">Yes</span></span>|  
    |<span data-ttu-id="c06e6-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="c06e6-140">2.0 - 3.5</span></span>|<span data-ttu-id="c06e6-141">Nie</span><span class="sxs-lookup"><span data-stu-id="c06e6-141">No</span></span>|<span data-ttu-id="c06e6-142">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="c06e6-142">Not applicable</span></span>|<span data-ttu-id="c06e6-143">Tak</span><span class="sxs-lookup"><span data-stu-id="c06e6-143">Yes</span></span>|  
    |<span data-ttu-id="c06e6-144">4</span><span class="sxs-lookup"><span data-stu-id="c06e6-144">4</span></span>|<span data-ttu-id="c06e6-145">Tak</span><span class="sxs-lookup"><span data-stu-id="c06e6-145">Yes</span></span>|<span data-ttu-id="c06e6-146">Tak</span><span class="sxs-lookup"><span data-stu-id="c06e6-146">Yes</span></span>|<span data-ttu-id="c06e6-147">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="c06e6-147">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c06e6-148">.NET Framework wersje 3,0 i 3,5 są kompilowane przyrostowo w wersji 2,0 i nie muszą być uruchamiane obok siebie.</span><span class="sxs-lookup"><span data-stu-id="c06e6-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="c06e6-149">Są one w tej samej wersji.</span><span class="sxs-lookup"><span data-stu-id="c06e6-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="c06e6-150">Typowe scenariusze hostingu równoczesnego</span><span class="sxs-lookup"><span data-stu-id="c06e6-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="c06e6-151">**Scenariusz 1:** Aplikacja natywna, która korzysta ze składników COM utworzonych przy użyciu wcześniejszych wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c06e6-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="c06e6-152">Zainstalowane wersje .NET Framework: .NET Framework 4 i wszystkie pozostałe wersje .NET Framework używane przez składniki COM.</span><span class="sxs-lookup"><span data-stu-id="c06e6-152">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="c06e6-153">Co należy zrobić: W tym scenariuszu nic nie rób.</span><span class="sxs-lookup"><span data-stu-id="c06e6-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="c06e6-154">Składniki COM będą działać z wersją .NET Framework, w których zostały zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="c06e6-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="c06e6-155">**Scenariusz 2**: Aplikacja zarządzana utworzona przy użyciu .NET Framework 2,0 SP1, która ma być uruchamiana z .NET Framework 2,0, ale chce działać na .NET Framework 4, jeśli wersja 2,0 nie jest obecna.</span><span class="sxs-lookup"><span data-stu-id="c06e6-155">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="c06e6-156">Zainstalowane wersje .NET Framework: Starsza wersja .NET Framework i .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c06e6-156">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="c06e6-157">Co należy zrobić: W [pliku konfiguracji aplikacji](../../../docs/framework/configure-apps/index.md) w katalogu aplikacji użyj [ \<elementu >](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) [ \<Start i zestawu elementów > supportedRuntime](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c06e6-157">What to do: In the [application configuration file](../../../docs/framework/configure-apps/index.md) in the application directory, use the [\<startup> element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="c06e6-158">**Scenariusz 3:** Aplikacja natywna korzystająca ze składników COM utworzonych przy użyciu wcześniejszych wersji .NET Framework, które mają być uruchamiane z .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c06e6-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="c06e6-159">Zainstalowane wersje .NET Framework: .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c06e6-159">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="c06e6-160">Co należy zrobić: W pliku `<startup>` konfiguracyjnym aplikacji w katalogu aplikacji użyj elementu `useLegacyV2RuntimeActivationPolicy` z `<supportedRuntime>` atrybutem ustawionym na `true` i element set w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c06e6-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="c06e6-161">Przykład</span><span class="sxs-lookup"><span data-stu-id="c06e6-161">Example</span></span>  
 <span data-ttu-id="c06e6-162">Poniższy przykład ilustruje niezarządzany host COM, na którym działa zarządzany składnik COM przy użyciu wersji .NET Framework, do której składnik został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="c06e6-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="c06e6-163">Aby uruchomić Poniższy przykład, skompiluj i zarejestruj następujący zarządzany składnik COM przy użyciu .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="c06e6-163">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="c06e6-164">Aby zarejestrować składnik, w menu **projekt** kliknij polecenie **Właściwości**, kliknij kartę **kompilacja** , a następnie zaznacz pole wyboru **Zarejestruj dla międzyoperacyjności modelu COM** .</span><span class="sxs-lookup"><span data-stu-id="c06e6-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
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
  
 <span data-ttu-id="c06e6-165">Skompiluj następującą niezarządzaną C++ aplikację, która aktywuje obiekt com, który został utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c06e6-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c06e6-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c06e6-166">See also</span></span>

- [<span data-ttu-id="c06e6-167">\<> uruchomienia — element</span><span class="sxs-lookup"><span data-stu-id="c06e6-167">\<startup> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="c06e6-168">\<supportedRuntime, element ></span><span class="sxs-lookup"><span data-stu-id="c06e6-168">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
