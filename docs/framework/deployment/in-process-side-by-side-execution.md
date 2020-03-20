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
# <a name="in-process-side-by-side-execution"></a>Wykonywanie równoczesne i wewnątrzprocesowe
Począwszy od programu .NET Framework 4, można użyć hostingu obok siebie w trakcie procesu, aby uruchomić wiele wersji środowiska wykonawczego języka wspólnego (CLR) w jednym procesie. Domyślnie zarządzane składniki COM są uruchamiane z wersją programu .NET Framework, z którą zostały zbudowane, niezależnie od wersji programu .NET Framework, która jest ładowana dla procesu.  
  
## <a name="background"></a>Tło  
 .NET Framework zawsze zapewniał hosting side-by-side dla aplikacji kodu zarządzanego, ale przed programem .NET Framework 4 nie zapewniał tej funkcji dla zarządzanych składników COM. W przeszłości zarządzane składniki COM, które zostały załadowane do procesu, zostały uruchomione z wersją środowiska wykonawczego, która została już załadowana, lub z najnowszą zainstalowaną wersją programu .NET Framework. Jeśli ta wersja nie jest zgodna ze składnikiem COM, składnik zakończy się niepowodzeniem.  
  
 .NET Framework 4 zapewnia nowe podejście do hostingu side-by-side, który zapewnia następujące funkcje:  
  
- Zainstalowanie nowej wersji programu .NET Framework nie ma wpływu na istniejące aplikacje.  
  
- Aplikacje są uruchamiane względem wersji programu .NET Framework, z których zostały utworzone. Nie używają nowej wersji programu .NET Framework, chyba że zostanie to wyraźnie skierowane. Jednak jest łatwiejsze dla aplikacji do przejścia do korzystania z nowej wersji programu .NET Framework.  
  
## <a name="effects-on-users-and-developers"></a>Wpływ na użytkowników i programistów  
  
- **Użytkownicy końcowi i administratorzy systemu**. Ci użytkownicy mogą teraz mieć większą pewność, że podczas instalowania nowej wersji środowiska wykonawczego, niezależnie lub z aplikacją, nie będzie to miało wpływu na ich komputery. Istniejące aplikacje będą nadal działać tak jak poprzednio.  
  
- **Deweloperzy aplikacji**. Hosting side-by-side nie ma prawie żadnego wpływu na deweloperów aplikacji. Domyślnie aplikacje zawsze są uruchamiane względem wersji programu .NET Framework, na których zostały zbudowane; to się nie zmieniło. Jednak deweloperzy mogą zastąpić to zachowanie i skierować aplikację do uruchomienia w ramach nowszej wersji programu .NET Framework (zobacz [scenariusz 2](#scenarios)).  
  
- **Deweloperzy bibliotek i konsumenci**. Hosting side-by-side nie rozwiązuje problemów ze zgodnością, z którymi borykają się deweloperzy biblioteki. Biblioteka, która jest ładowana bezpośrednio przez aplikację — za <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> pośrednictwem bezpośredniego odwołania lub wywołania <xref:System.AppDomain> — nadal używa środowiska wykonawczego, do którego jest ładowana. Należy przetestować biblioteki na wszystkich wersjach programu .NET Framework, które mają być obsługiwane. Jeśli aplikacja jest kompilowana przy użyciu środowiska uruchomieniowego .NET Framework 4, ale zawiera bibliotekę, która została zbudowana przy użyciu wcześniejszego środowiska wykonawczego, biblioteka ta będzie również używać środowiska uruchomieniowego .NET Framework 4. Jeśli jednak masz aplikację, która została zbudowana przy użyciu wcześniejszego środowiska uruchomieniowego i biblioteki, która została zbudowana przy użyciu programu .NET Framework 4, należy wymusić na aplikacji również użycie programu .NET Framework 4 (zobacz [scenariusz 3](#scenarios)).  
  
- **Zarządzali deweloperami składników COM**. W przeszłości zarządzane składniki COM były automatycznie uruchamiane przy użyciu najnowszej wersji środowiska wykonawczego zainstalowanego na komputerze. Teraz można wykonać składniki COM względem wersji środowiska wykonawczego, z których zostały zbudowane.  
  
     Jak pokazano w poniższej tabeli, komponenty, które zostały zbudowane z .NET Framework w wersji 1.1, mogą być uruchamiane obok komponentów w wersji 4, ale nie mogą działać z komponentami w wersji 2.0, 3.0 lub 3.5, ponieważ hosting side-by-side nie jest dostępny dla tych, które nie są dostępne dla tych, którzy nie są dostępni. Wersje.  
  
    |Wersja programu .NET Framework|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Nie dotyczy|Nie|Tak|  
    |2.0 - 3.5|Nie|Nie dotyczy|Tak|  
    |4|Tak|Tak|Nie dotyczy|  
  
> [!NOTE]
> .NET Framework wersje 3.0 i 3.5 są tworzone przyrostowo w wersji 2.0 i nie trzeba uruchamiać obok siebie. Są to z natury tej samej wersji.  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a>Typowe scenariusze hostingu side-by-side  
  
- **Scenariusz 1:** Natywna aplikacja, która używa składników COM utworzonych we wcześniejszych wersjach programu .NET Framework.  
  
     Zainstalowano wersje programu .NET Framework: program .NET Framework 4 i wszystkie inne wersje programu .NET Framework używane przez składniki COM.  
  
     Co zrobić: W tym scenariuszu nic nie rób. Składniki COM będą uruchamiane z wersją programu .NET Framework, w których zostały zarejestrowane.  
  
- **Scenariusz 2:** Zarządzana aplikacja zbudowana z .NET Framework 2.0 SP1, który wolisz uruchomić z .NET Framework 2.0, ale są chętni do uruchomienia w programie .NET Framework 4, jeśli wersja 2.0 nie jest obecny.  
  
     Zainstalowano wersje programu .NET Framework: wcześniejsza wersja programu .NET Framework i programu .NET Framework 4.  
  
     Co należy zrobić: W [pliku konfiguracji aplikacji](../configure-apps/index.md) w katalogu aplikacji użyj elementu [ \<> uruchamiania](../configure-apps/file-schema/startup/startup-element.md) i [ \<obsługiwanego elementu>runtime](../configure-apps/file-schema/startup/supportedruntime-element.md) w następujący sposób:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- **Scenariusz 3:** Natywna aplikacja, która używa składników COM utworzonych z wcześniejszymi wersjami programu .NET Framework, które mają być uruchamiane za pomocą programu .NET Framework 4.  
  
     Zainstalowano wersje programu .NET Framework: program .NET Framework 4.  
  
     Co należy zrobić: W pliku konfiguracji aplikacji w `<startup>` katalogu aplikacji `useLegacyV2RuntimeActivationPolicy` użyj elementu `true` z `<supportedRuntime>` atrybutem ustawionym do i zestawu elementów w następujący sposób:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano niezarządzanego hosta COM, który jest uruchomiony składnik COM zarządzane przy użyciu wersji programu .NET Framework, który składnik został skompilowany do użycia.  
  
 Aby uruchomić poniższy przykład, skompiluj i zarejestruj następujący zarządzany składnik COM przy użyciu programu .NET Framework 3.5. Aby zarejestrować składnik, w menu **Projekt** kliknij polecenie **Właściwości**, kliknij kartę **Kompilacja,** a następnie zaznacz pole wyboru **Zarejestruj się dla współdziałania COM.**  
  
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
  
 Skompiluj następującą niezarządzaną aplikację C++, która aktywuje obiekt COM, który jest tworzony w poprzednim przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [\<element> uruchamiania](../configure-apps/file-schema/startup/startup-element.md)
- [\<supportedRuntime> Element](../configure-apps/file-schema/startup/supportedruntime-element.md)
