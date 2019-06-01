---
title: Wykonywanie równoczesne i wewnątrzprocesowe
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: adf2e3e3d10f4f32952dbca270be4ca0924d0b73
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457266"
---
# <a name="in-process-side-by-side-execution"></a>Wykonywanie równoczesne i wewnątrzprocesowe
Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć w trakcie side-by-side hostingu do uruchamiania wielu wersji środowiska uruchomieniowego języka wspólnego (CLR) w ramach jednego procesu. Domyślnie zarządzane składniki COM, uruchom z .NET Framework w wersji, które zostały skompilowane, niezależnie od wersji programu .NET Framework, który jest ładowany do procesu.  
  
## <a name="background"></a>Tło  
 .NET Framework zawsze ma pod warunkiem side-by-side hostowania dotycząca aplikacje kodu zarządzanego, ale przed .NET Framework 4 nie zapewniają tej funkcji dla składników COM zarządzanych. W przeszłości zarządzanych składników COM, które zostały załadowane do procesu został uruchomiony z wersją środowiska uruchomieniowego, który został już załadowany lub z najnowszej zainstalowanej wersji programu .NET Framework. Jeśli ta wersja nie jest zgodny ze składnikiem COM, składnik może zakończyć się niepowodzeniem.  
  
 .NET Framework 4 zawiera nowe podejście do hostingu side-by-side, które gwarantuje, że następujące czynności:  
  
- Instalowanie nowej wersji programu .NET Framework nie ma wpływu na istniejące aplikacje.  
  
- Aplikacje są uruchamiane z wersją programu .NET Framework, które zostały skompilowane. Używają nowej wersji programu .NET Framework, chyba że wyraźnie kierowany Aby to zrobić. Jednak jest łatwiej aplikacji do przejścia do korzystania z nowej wersji programu .NET Framework.  
  
## <a name="effects-on-users-and-developers"></a>Wpływ na użytkowników i deweloperów  
  
- **Użytkownicy końcowi i Administratorzy systemu**. Ci użytkownicy mogą teraz mają większą pewność, że przy instalacji nowej wersji środowiska uruchomieniowego, niezależnie od siebie lub za pomocą aplikacji, nie będzie mieć żadnego wpływu na swoich komputerach. Istniejące aplikacje, będą w dalszym ciągu działać tak jak przed.  
  
- **Deweloperzy aplikacji**. Hosting Side-by-side prawie nie ma wpływu na deweloperów aplikacji. Domyślnie aplikacje zawsze uruchamiana w wersji programu .NET Framework, w których zostały zbudowane; to nie została zmieniona. Jednakże, deweloperzy mogą zmienić to zachowanie i skierować aplikację do uruchamiania w nowszej wersji programu .NET Framework (zobacz [Scenariusz 2](#scenarios)).  
  
- **Deweloperów bibliotek i konsumentów**. Side-by-side hostingu nie rozwiązuje problemy ze zgodnością napotykane przez deweloperów biblioteki. Biblioteka, która jest ładowane bezpośrednio przez aplikację — za pośrednictwem bezpośredniego odwołania lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> wywołania — będzie później nadal używać środowiska uruchomieniowego <xref:System.AppDomain> jest ładowany. Należy przetestować bibliotek względem wszystkich wersji programu .NET Framework, które mają być obsługiwane. Jeśli aplikacja jest skompilowana przy użyciu środowiska uruchomieniowego .NET Framework 4, ale zawiera bibliotekę, który został zbudowany przy użyciu starszych środowiska uruchomieniowego, tej biblioteki będzie używać .NET Framework 4 środowisko uruchomieniowe także. Jednak jeśli masz aplikację, która została skompilowana przy użyciu starszych środowisko uruchomieniowe i Biblioteka, który został zbudowany przy użyciu programu .NET Framework 4, należy wymusić aplikacji również używać programu .NET Framework 4 (zobacz [Scenariusz 3](#scenarios)).  
  
- **Zarządzane Deweloperzy składników COM**. W przeszłości składniki COM zarządzane automatycznie została uruchomiona przy użyciu najnowszej wersji środowiska uruchomieniowego zainstalowanego na komputerze. Można teraz wykonać składników modelu COM z wersją środowiska uruchomieniowego, które zostały skompilowane.  
  
     Jak pokazano w poniższej tabeli, składników, które zostały utworzone przy użyciu platformy .NET Framework w wersji 1.1, można uruchomić równolegle składniki w wersji 4, ale nie działają one w wersji 2.0, 3.0 lub 3.5 składników, ponieważ side-by-side hostingu nie jest dostępny dla osób wersje.  
  
    |Wersja programu .NET Framework|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Nie dotyczy|Nie|Yes|  
    |2.0 - 3.5|Nie|Nie dotyczy|Tak|  
    |4|Yes|Yes|Nie dotyczy|  
  
> [!NOTE]
>  Wersje programu .NET framework 3.0 i 3.5 są tworzone przyrostowo w wersji 2.0 i nie trzeba uruchamiać równolegle. Te założenia mają taką samą wersję.  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a>Typowe scenariusze Side-by-Side hostingu  
  
- **Scenariusz 1:** Aplikacji natywnej używającej składniki COM, utworzone w starszych wersjach programu .NET Framework.  
  
     Zainstalowane wersje programu .NET framework: .NET Framework 4 i wszystkich innych wersji systemu .NET Framework używanego przez składniki COM.  
  
     Co należy zrobić: W tym scenariuszu nic nie rób. Składniki COM będą uruchamiane przy użyciu wersji programu .NET Framework zostały zarejestrowane w usłudze.  
  
- **Scenariusz 2**: Zarządzana aplikacja skompilowana przy użyciu [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] , którego chcesz użyć uruchomić program z [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ale są gotowi do uruchamiania na .NET Framework 4 nie jest w wersji 2.0.  
  
     Zainstalowane wersje programu .NET framework: Wcześniejszej wersji programu .NET Framework i .NET Framework 4.  
  
     Co należy zrobić: W [pliku konfiguracji aplikacji](../../../docs/framework/configure-apps/index.md) w katalogu aplikacji za pomocą [ \<uruchamiania > element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) i [ \<supportedRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) ustawione w następujący sposób:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- **Scenariusz 3:** Aplikacji natywnej używającej składniki COM, utworzone w starszych wersjach programu .NET Framework, która ma zostać uruchomiony za pomocą programu .NET Framework 4.  
  
     Zainstalowane wersje programu .NET framework: .NET Framework 4.  
  
     Co należy zrobić: W pliku konfiguracyjnym aplikacji w katalogu aplikacji, należy użyć `<startup>` element z `useLegacyV2RuntimeActivationPolicy` ustawioną wartość atrybutu `true` i `<supportedRuntime>` element jest ustawiony w następujący sposób:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano niezarządzany host COM, działającego zarządzanego składnika COM za pomocą wersji programu .NET Framework, który składnik był skompilowany do użycia.  
  
 Z poniższego przykładu, kompilowania i zarejestrowania następujących zarządzanych za pomocą składnika COM [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]. Można zarejestrować składnika, na **projektu** menu, kliknij przycisk **właściwości**, kliknij przycisk **kompilacji** , a następnie wybierz pozycję **Zarejestruj dla współdziałania COM**pole wyboru.  
  
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
  
 Skompiluj następujący niezarządzanej aplikacji C++, które uaktywnia się obiekt COM, który jest tworzony w poprzednim przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [\<Uruchamianie > Element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
- [\<supportedRuntime> Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
