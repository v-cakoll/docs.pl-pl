---
title: Wykonywanie równoczesne i wewnątrzprocesowe
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee9eb30d6966d8162b29286140c068d854f7911c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="in-process-side-by-side-execution"></a>Wykonywanie równoczesne i wewnątrzprocesowe
Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć w trakcie side-by-side hosting do uruchamiania wielu wersji środowisko uruchomieniowe języka wspólnego (CLR) w ramach jednego procesu. Domyślnie zarządzane składniki COM działać z wersją .NET Framework, które ich nie zostały skompilowane, niezależnie od wersji programu .NET Framework, który jest ładowany do procesu.  
  
## <a name="background"></a>Tło  
 .NET Framework zawsze ma podany side-by-side hosting dla zarządzanego kodu aplikacji, ale przed wysłaniem [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], nie zapewniają te funkcje składników COM zarządzanych. W przeszłości zarządzane składniki COM, które zostały załadowane do procesu został uruchomiony z wersją środowiska uruchomieniowego, który został już załadowany lub z najnowszej zainstalowanej wersji programu .NET Framework. Jeśli ta wersja nie jest zgodny z składnika modelu COM, składnik nie powiedzie się.  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Udostępnia nowe podejście do hostingu side-by-side, który zapewnia następujące:  
  
-   Instalowanie nowej wersji programu .NET Framework nie ma wpływu na istniejące aplikacje.  
  
-   Aplikacje są uruchamiane z wersją programu .NET Framework, które zostały skompilowane. Używają nowej wersji programu .NET Framework, chyba że wyraźnie skierowane w tym celu. Jednak jest łatwiejsze do przejścia aplikacji przy użyciu nowej wersji programu .NET Framework.  
  
## <a name="effects-on-users-and-developers"></a>Wpływ na użytkowników i deweloperów  
  
-   **Użytkownicy końcowi i Administratorzy systemu**. Ci użytkownicy mają teraz większa pewność, że przy instalacji nowej wersji środowiska uruchomieniowego można niezależnie lub za pomocą aplikacji, jego zostanie nie mają wpływu na swoich komputerach. Istniejące aplikacje będą nadal działać tak jak przed.  
  
-   **Deweloperzy aplikacji**. Hosting Side-by-side prawie nie ma wpływu na deweloperzy aplikacji. Domyślnie aplikacje zawsze uruchamiana w wersji programu .NET Framework, że zostały zbudowane na; nie została zmieniona. Jednak deweloperzy mogą zmienić to zachowanie i skierować aplikację do uruchamiania w nowszej wersji programu .NET Framework (zobacz [Scenariusz 2](#scenarios)).  
  
-   **Biblioteka deweloperów i konsumentów**. Hosting Side-by-side nie rozwiązuje problemy ze zgodnością napotykane przez deweloperów biblioteki. Biblioteki, która jest bezpośrednio ładowany przez aplikację — poprzez bezpośrednie odwołanie lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> wywołać — będzie później nadal używać środowiska wykonawczego o <xref:System.AppDomain> został załadowany. Należy przetestować bibliotek względem wszystkich wersji platformy .NET, które mają być obsługiwane. Jeśli aplikacja została skompilowana przy użyciu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] środowiska uruchomieniowego zawiera jednak bibliotekę został zbudowany przy użyciu wcześniejszych środowiska uruchomieniowego, użyje tej biblioteki [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] również w czasie wykonywania. Jednak jeśli masz aplikację, która została skompilowana przy użyciu wcześniejszych środowiska uruchomieniowego i biblioteki, który został utworzony przy użyciu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], należy wymusić aplikacji można również użyć [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (zobacz [Scenariusz 3](#scenarios)).  
  
-   **Zarządzane deweloperzy składnika COM**. W przeszłości zarządzane składniki COM automatycznie została uruchomiona przy użyciu najnowszej wersji środowiska uruchomieniowego zainstalowany na komputerze. Można teraz wykonać składniki modelu COM z wersją środowiska uruchomieniowego, które zostały skompilowane.  
  
     Jak pokazano w poniższej tabeli, składników, które nie zostały skompilowane dla platformy .NET Framework w wersji 1.1 można uruchomić równolegle składniki w wersji 4, ale ich nie można uruchomić w wersji 2.0, 3.0 lub 3.5 składników, ponieważ side-by-side hostingu nie jest dostępna dla osób wersje.  
  
    |Wersja programu .NET Framework|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Nie dotyczy|Nie|Tak|  
    |2.0 - 3.5|Nie|Nie dotyczy|Tak|  
    |4|Tak|Tak|Nie dotyczy|  
  
> [!NOTE]
>  Wersje programu .NET framework 3.0 i 3.5 są tworzone przyrostowo w wersji 2.0 i nie trzeba uruchomić obok siebie. Są z założenia tej samej wersji.  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a>Typowe scenariusze hostingu Side-by-Side  
  
-   **Scenariusz 1:** aplikacji natywnej używającej składniki COM utworzone we wcześniejszych wersjach programu .NET Framework.  
  
     Zainstalowane wersje .NET framework: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] i wszystkich wersji platformy .NET używanego przez składniki COM.  
  
     Co należy zrobić: W tym scenariuszu, nic nie rób. Składniki modelu COM będą uruchamiane z wersją programu .NET Framework w zarejestrowani z.  
  
-   **Scenariusz 2**: zarządzanych aplikacji skompilowanej za pomocą [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] , który chcesz uruchomić z [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ale nie jest gotowa do uruchomienia na [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Jeśli nie jest w wersji 2.0.  
  
     Zainstalowane wersje .NET framework: starszej wersji programu .NET Framework i [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Co należy zrobić: W [pliku konfiguracji aplikacji](../../../docs/framework/configure-apps/index.md) w katalogu aplikacji, użyj [ \<uruchamiania > element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) i [ \<supportedRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) ustawione w następujący sposób:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
-   **Scenariusz 3:** natywnych aplikacji, która używa składniki COM utworzone we wcześniejszych wersjach programu .NET Framework, która ma zostać uruchomione z [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Zainstalowane wersje .NET framework: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Co należy zrobić: W pliku konfiguracyjnym aplikacji w katalogu aplikacji, użyj `<startup>` element z `useLegacyV2RuntimeActivationPolicy` ustawić atrybutu `true` i `<supportedRuntime>` element ustawiony w następujący sposób:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano niezarządzane COM host, na którym działa zarządzanego składnika modelu COM przy użyciu wersji programu .NET Framework, która składnik został skompilowany do użycia.  
  
 Aby uruchomić poniższy przykład, kompilowania i zarejestrować następujące zarządzanych za pomocą składnika COM [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]. Aby zarejestrować składnika, na **projektu** menu, kliknij przycisk **właściwości**, kliknij przycisk **kompilacji** , a następnie wybierz **Zarejestruj dla międzyoperacyjności z modelem COM**pole wyboru.  
  
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
  
 Kompiluj następujące niezarządzanej aplikacji C++, które aktywuje obiektu COM, który jest utworzony w poprzednim przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [\<Uruchamianie > — Element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
 [\<supportedRuntime > — Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
