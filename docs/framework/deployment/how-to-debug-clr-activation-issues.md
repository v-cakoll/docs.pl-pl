---
title: 'Porady: debugowanie problemów aktywacji środowiska CLR'
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89724e9a322f2f28dbe5d18ae697acbdd0a32d8e
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2018
ms.locfileid: "50744473"
---
# <a name="how-to-debug-clr-activation-issues"></a>Porady: debugowanie problemów aktywacji środowiska CLR
Jeśli wystąpią problemy podczas uzyskiwania aplikację do uruchamiania w odpowiedniej wersji środowiska uruchomieniowego języka wspólnego (CLR), można wyświetlać i debugowania dzienniki aktywacji środowiska CLR. Te dzienniki może być bardzo przydatne podczas ustalania głównej przyczyny problemu aktywacji, kiedy aplikacja różnych wersji środowiska CLR ładuje, niż oczekiwano lub w ogóle nie jest ładowana środowiska CLR. [Błędy inicjowania programu .NET Framework: Zarządzanie środowiska użytkownika](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) tym artykule omówiono środowisko CLR nie został znaleziony dla aplikacji.  
  
 Rejestrowanie aktywacji środowiska CLR może być włączone całego systemu za pomocą klucza rejestru HKEY_LOCAL_MACHINE lub zmienną środowiskową systemu. Dziennik zostanie wygenerowany, aż do wpisu rejestru lub zmiennej środowiskowej zostanie usunięty. Alternatywnie można użyć użytkownika lub zmiennej środowiskowej proces lokalny Aby włączyć rejestrowanie za pomocą innego zakresu i czasu trwania.  
  
 Dzienniki aktywacji środowiska CLR, nie należy mylić z [dzienniki powiązań zestawów](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), które są zupełnie innego.  
  
## <a name="to-enable-clr-activation-logging"></a>Aby włączyć rejestrowanie aktywacji środowiska CLR  
  
#### <a name="using-the-registry"></a>Za pomocą rejestru  
  
1.  W Edytorze rejestru przejdź do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (na komputerze 32-bitowa) lub HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Folder NETFramework (na komputerze 64-bitowych).  
  
2.  Dodaj wartość ciągu o nazwie `CLRLoadLogDir`i ustaw ją na pełną ścieżkę istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.  
  
 Aktywacja rejestrowania pozostanie włączona, dopóki nie usuniesz wartość ciągu.  
  
#### <a name="using-an-environment-variable"></a>Za pomocą zmiennej środowiskowej  
  
-   Ustaw `COMPLUS_CLRLoadLogDir` zmienną środowiskową na ciąg, który reprezentuje pełną ścieżkę istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.  
  
     Zakres Określa, jak ustawić zmienną środowiskową:  
  
    -   Jeśli zostanie ustawiona na poziomie systemu, aktywacji rejestrowanie jest włączone dla wszystkich aplikacji .NET Framework na tym komputerze, do momentu usunięcia zmiennej środowiskowej.  
  
    -   Jeśli zostanie ustawiona na poziomie użytkownika, aktywacji rejestrowanie jest włączone tylko dla bieżącego konta użytkownika. Rejestrowanie jest kontynuowany do momentu usunięcia zmiennej środowiskowej.  
  
    -   Jeśli ustawisz go w ramach procesu przed załadowaniem środowiska CLR, aktywacji rejestrowanie jest włączone, aż do zakończenia procesu.  
  
    -   Jeśli zostanie ustawiona w wierszu polecenia przed uruchomieniem aplikacji, rejestrowanie aktywacji jest włączone dla każdej aplikacji, uruchamianą w tym wierszu polecenia.  
  
     Na przykład do przechowywania dzienników aktywacji w katalogu c:\clrloadlogs zakresie na poziomie procesu, Otwórz okno wiersza polecenia i wpisz następujące polecenie przed uruchomieniem aplikacji:  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a>Przykład  
 Dzienniki aktywacji środowiska CLR zapewniają dużą ilość danych o aktywacji środowiska CLR i używania środowiska CLR hostowania interfejsów API. Większość z tych danych jest używana wewnętrznie przez firmę Microsoft, ale niektóre dane również może być przydatny dla deweloperów, zgodnie z opisem w tym artykule.  
  
 Dziennik odzwierciedla kolejność, w której CLR hostowania interfejsów API zostały wywołane. Zawiera on również użyteczne dane na temat zestawu zainstalowanego środowiska uruchomieniowe wykryty na komputerze. Format dziennika aktywacji środowiska CLR nie jest sam udokumentowane, ale może służyć do pomóc deweloperom, którzy muszą zostać rozwiązane problemów aktywacji środowiska CLR.  
  
> [!NOTE]
>  Nie można otworzyć dziennika aktywacji, dopóki nie zakończył procesu, który używa środowiska CLR.  
  
> [!NOTE]
>  Dzienniki aktywacji środowiska CLR nie są lokalizowane; są one zawsze generowane w języku angielskim.  
  
 W poniższym przykładzie w dzienniku aktywacji najbardziej użyteczne informacje jest wyróżniona i opisem po dziennika.  
  
```  
532,205950.367,CLR Loading log for C:\Tests\myapp.exe   
532,205950.367,Log started at 4:26:12 PM on 10/6/2011   
532,205950.367,-----------------------------------   
532,205950.382,FunctionCall: _CorExeMain   
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}   
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}   
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0   
532,205950.382,Input values for ComputeVersionString follow this line   
532,205950.382,-----------------------------------   
532,205950.382,Default Application Name: C:\Tests\myapp.exe   
532,205950.382,IsLegacyBind is: 0   
532,205950.382,IsCapped is 0   
532,205950.382,SkuCheckFlags are 0   
532,205950.382,ShouldEmulateExeLaunch is 0   
532,205950.382,LegacyBindRequired is 0   
532,205950.382,-----------------------------------   
532,205950.382,Parsing config file: C:\Tests\myapp.exe   
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727   
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.   
532,205950.398,SEM_FAILCRITICALERRORS is set to 0   
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3   
532,205950.398,FunctionCall: RealDllMain. Reason: 0   
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0  
```  
  
-   **Dziennik ładowania CLR** zapewnia ścieżkę do pliku wykonywalnego, który uruchomił proces, który załadowany kodu zarządzanego. Należy pamiętać, że może to być natywne hosta.  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   **Zainstalowane środowisko uruchomieniowe** to zestaw wersji środowiska CLR zainstalowany na komputerze, które nadają się do żądania aktywacji.  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   **utworzonych za pomocą wersji** stanowi wersję środowiska CLR, który został użyty do tworzenia pliku binarnego, który został dostarczony do metody, takie jak [iclrmetahostpolicy::getrequestedruntime —](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   **instalacji funkcji na żądanie** odwołuje się do włączania programu .NET Framework 3.5 w systemie Windows 8. Zobacz [błędy inicjowania programu .NET Framework: Zarządzanie wrażeniami użytkownika](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) Aby uzyskać więcej informacji na temat tego scenariusza.  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a>Zobacz też  
- [Wdrażanie](../../../docs/framework/deployment/index.md)  
- [Instrukcje: Konfiguracja aplikacji do obsługi w programie .NET Framework 4 lub 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
