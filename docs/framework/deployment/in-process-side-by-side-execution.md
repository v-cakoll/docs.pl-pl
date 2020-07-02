---
title: Wykonywanie równoczesne i wewnątrzprocesowe
description: Obsługa w procesie równoczesnego wykonywania wielu wersji środowiska uruchomieniowego języka wspólnego (CLR) w pojedynczym procesie platformy .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 078f2eaada8fac57138bef22d46218ef2ccda835
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622604"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="bfbe1-103">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="bfbe1-103">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="bfbe1-104">Począwszy od .NET Framework 4, można użyć w procesie równoczesnego hostowania do uruchamiania wielu wersji środowiska uruchomieniowego języka wspólnego (CLR) w ramach jednego procesu.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-104">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="bfbe1-105">Domyślnie zarządzane składniki COM są uruchamiane z .NET Framework wersją, z którą zostały skompilowane, niezależnie od wersji .NET Framework, która jest ładowana dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-105">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="bfbe1-106">Tło</span><span class="sxs-lookup"><span data-stu-id="bfbe1-106">Background</span></span>  
 <span data-ttu-id="bfbe1-107">.NET Framework zawsze udostępnia hosting równoczesny dla aplikacji z kodem zarządzanym, ale przed .NET Framework 4, nie zapewniał on funkcji zarządzanych składników COM.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-107">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="bfbe1-108">W przeszłości zarządzane składniki COM, które zostały załadowane do procesu, działały z wersją środowiska uruchomieniowego, które zostało już załadowane lub z najnowszą zainstalowaną wersją .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-108">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="bfbe1-109">Jeśli ta wersja nie jest zgodna ze składnikiem COM, składnik ten nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-109">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="bfbe1-110">.NET Framework 4 zawiera nowe podejście do hostingu równoczesnego, które zapewnia następujące działania:</span><span class="sxs-lookup"><span data-stu-id="bfbe1-110">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="bfbe1-111">Zainstalowanie nowej wersji .NET Framework nie ma wpływu na istniejące aplikacje.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-111">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="bfbe1-112">Aplikacje działają w porównaniu z wersją .NET Framework, z którą zostały skompilowane.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-112">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="bfbe1-113">Nie używają nowej wersji .NET Framework, chyba że jest to wyraźnie ukierunkowane.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-113">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="bfbe1-114">Jest to jednak łatwiejsze w aplikacjach do przechodzenia do korzystania z nowej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-114">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="bfbe1-115">Efekty dla użytkowników i deweloperów</span><span class="sxs-lookup"><span data-stu-id="bfbe1-115">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="bfbe1-116">**Użytkownicy końcowi i Administratorzy systemu**.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-116">**End users and system administrators**.</span></span> <span data-ttu-id="bfbe1-117">Ci użytkownicy mogą teraz mieć większą pewność, że podczas instalowania nowej wersji środowiska uruchomieniowego niezależnie lub z aplikacją nie będą mieć wpływu na komputery.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-117">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="bfbe1-118">Istniejące aplikacje będą nadal działać tak jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-118">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="bfbe1-119">**Deweloperzy aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-119">**Application developers**.</span></span> <span data-ttu-id="bfbe1-120">Hosting równoległy nie ma prawie żadnego wpływu na deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-120">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="bfbe1-121">Domyślnie aplikacje są zawsze uruchamiane w porównaniu z wersją .NET Framework, w których zostały skompilowane; Ta zmiana nie została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-121">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="bfbe1-122">Deweloperzy mogą jednak zastąpić to zachowanie i skierować aplikację do uruchamiania w nowszej wersji .NET Framework (patrz [Scenariusz 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="bfbe1-122">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="bfbe1-123">**Deweloperzy biblioteki i konsumenci**.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-123">**Library developers and consumers**.</span></span> <span data-ttu-id="bfbe1-124">Hosting równoległy nie rozwiązuje problemów ze zgodnością, które są używane przez deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-124">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="bfbe1-125">Biblioteka, która jest bezpośrednio ładowana przez aplikację — albo za pośrednictwem bezpośredniego odwołania lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> wywołania — kontynuuje używanie środowiska uruchomieniowego, który <xref:System.AppDomain> jest ładowany do.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-125">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="bfbe1-126">Należy przetestować biblioteki dla wszystkich wersji .NET Framework, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-126">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="bfbe1-127">Jeśli aplikacja jest kompilowana przy użyciu środowiska uruchomieniowego .NET Framework 4, ale zawiera bibliotekę, która została skompilowana przy użyciu wcześniejszego środowiska uruchomieniowego, biblioteka będzie używać środowiska uruchomieniowego .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-127">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="bfbe1-128">Jeśli jednak masz aplikację, która została skompilowana przy użyciu wcześniejszego środowiska uruchomieniowego i biblioteki, która została skompilowana przy użyciu .NET Framework 4, musisz wymusić, aby aplikacja korzystała również z .NET Framework 4 (patrz [Scenariusz 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="bfbe1-128">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="bfbe1-129">**Zarządzani Deweloperzy składników modelu COM**.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-129">**Managed COM component developers**.</span></span> <span data-ttu-id="bfbe1-130">W przeszłości zarządzane składniki COM zostały automatycznie uruchomione przy użyciu najnowszej wersji środowiska uruchomieniowego zainstalowanej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-130">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="bfbe1-131">Teraz można wykonywać składniki COM względem wersji środowiska uruchomieniowego, które zostały skompilowane przy użyciu programu.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-131">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="bfbe1-132">Zgodnie z poniższą tabelą składniki, które zostały skompilowane przy użyciu .NET Framework w wersji 1,1 mogą działać obok składników w wersji 4, ale nie mogą być uruchamiane z wersjami 2,0, 3,0 lub 3,5, ponieważ nie są dostępne dla tych wersji.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-132">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="bfbe1-133">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bfbe1-133">.NET Framework version</span></span>|<span data-ttu-id="bfbe1-134">1.1</span><span class="sxs-lookup"><span data-stu-id="bfbe1-134">1.1</span></span>|<span data-ttu-id="bfbe1-135">2,0 – 3,5</span><span class="sxs-lookup"><span data-stu-id="bfbe1-135">2.0 - 3.5</span></span>|<span data-ttu-id="bfbe1-136">4</span><span class="sxs-lookup"><span data-stu-id="bfbe1-136">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="bfbe1-137">1.1</span><span class="sxs-lookup"><span data-stu-id="bfbe1-137">1.1</span></span>|<span data-ttu-id="bfbe1-138">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="bfbe1-138">Not applicable</span></span>|<span data-ttu-id="bfbe1-139">Nie</span><span class="sxs-lookup"><span data-stu-id="bfbe1-139">No</span></span>|<span data-ttu-id="bfbe1-140">Yes</span><span class="sxs-lookup"><span data-stu-id="bfbe1-140">Yes</span></span>|  
    |<span data-ttu-id="bfbe1-141">2,0 – 3,5</span><span class="sxs-lookup"><span data-stu-id="bfbe1-141">2.0 - 3.5</span></span>|<span data-ttu-id="bfbe1-142">Nie</span><span class="sxs-lookup"><span data-stu-id="bfbe1-142">No</span></span>|<span data-ttu-id="bfbe1-143">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="bfbe1-143">Not applicable</span></span>|<span data-ttu-id="bfbe1-144">Tak</span><span class="sxs-lookup"><span data-stu-id="bfbe1-144">Yes</span></span>|  
    |<span data-ttu-id="bfbe1-145">4</span><span class="sxs-lookup"><span data-stu-id="bfbe1-145">4</span></span>|<span data-ttu-id="bfbe1-146">Yes</span><span class="sxs-lookup"><span data-stu-id="bfbe1-146">Yes</span></span>|<span data-ttu-id="bfbe1-147">Tak</span><span class="sxs-lookup"><span data-stu-id="bfbe1-147">Yes</span></span>|<span data-ttu-id="bfbe1-148">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="bfbe1-148">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="bfbe1-149">.NET Framework wersje 3,0 i 3,5 są kompilowane przyrostowo w wersji 2,0 i nie muszą być uruchamiane obok siebie.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-149">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="bfbe1-150">Są one w tej samej wersji.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-150">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="bfbe1-151">Typowe scenariusze hostingu równoczesnego</span><span class="sxs-lookup"><span data-stu-id="bfbe1-151">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="bfbe1-152">**Scenariusz 1:** Aplikacja natywna, która korzysta ze składników COM utworzonych przy użyciu wcześniejszych wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-152">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="bfbe1-153">Zainstalowane wersje .NET Framework: .NET Framework 4 i wszystkie pozostałe wersje .NET Framework używane przez składniki COM.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-153">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="bfbe1-154">Co należy zrobić: w tym scenariuszu nic nie rób.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-154">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="bfbe1-155">Składniki COM będą działać z wersją .NET Framework, w których zostały zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-155">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="bfbe1-156">**Scenariusz 2**: zarządzana aplikacja skompilowana z .NET Framework 2,0 SP1, którą wolisz uruchomić przy użyciu .NET Framework 2,0, ale chcemy działać na .NET Framework 4, jeśli wersja 2,0 nie jest obecna.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-156">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="bfbe1-157">Zainstalowane wersje .NET Framework: wcześniejsza wersja .NET Framework i .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-157">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="bfbe1-158">Co należy zrobić: w [pliku konfiguracji aplikacji](../configure-apps/index.md) w katalogu aplikacji użyj [ \<startup> elementu](../configure-apps/file-schema/startup/startup-element.md) i zestawu [ \<supportedRuntime> elementów](../configure-apps/file-schema/startup/supportedruntime-element.md) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bfbe1-158">What to do: In the [application configuration file](../configure-apps/index.md) in the application directory, use the [\<startup> element](../configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="bfbe1-159">**Scenariusz 3:** Aplikacja natywna korzystająca ze składników COM utworzonych przy użyciu wcześniejszych wersji .NET Framework, które mają być uruchamiane z .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-159">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="bfbe1-160">Zainstalowane wersje .NET Framework: .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-160">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="bfbe1-161">Co należy zrobić: w pliku konfiguracji aplikacji w katalogu aplikacji użyj `<startup>` elementu z `useLegacyV2RuntimeActivationPolicy` atrybutem ustawionym na `true` i `<supportedRuntime>` zestaw elementów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bfbe1-161">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="bfbe1-162">Przykład</span><span class="sxs-lookup"><span data-stu-id="bfbe1-162">Example</span></span>  
 <span data-ttu-id="bfbe1-163">Poniższy przykład ilustruje niezarządzany host COM, na którym działa zarządzany składnik COM przy użyciu wersji .NET Framework, do której składnik został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-163">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="bfbe1-164">Aby uruchomić Poniższy przykład, skompiluj i zarejestruj następujący zarządzany składnik COM przy użyciu .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-164">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="bfbe1-165">Aby zarejestrować składnik, w menu **projekt** kliknij polecenie **Właściwości**, kliknij kartę **kompilacja** , a następnie zaznacz pole wyboru **Zarejestruj dla międzyoperacyjności modelu COM** .</span><span class="sxs-lookup"><span data-stu-id="bfbe1-165">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
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
  
 <span data-ttu-id="bfbe1-166">Skompiluj następującą niezarządzaną aplikację C++, która aktywuje obiekt COM, który został utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bfbe1-166">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bfbe1-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfbe1-167">See also</span></span>

- [<span data-ttu-id="bfbe1-168">\<startup>Postaci</span><span class="sxs-lookup"><span data-stu-id="bfbe1-168">\<startup> Element</span></span>](../configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="bfbe1-169">\<supportedRuntime>Postaci</span><span class="sxs-lookup"><span data-stu-id="bfbe1-169">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
