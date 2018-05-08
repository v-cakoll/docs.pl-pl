---
title: 'Porady: debugowanie problemów aktywacji środowiska CLR'
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b78d917b95e06a14b74c812bf92107476ad17212
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-debug-clr-activation-issues"></a>Porady: debugowanie problemów aktywacji środowiska CLR
Jeśli wystąpią problemy podczas pobierania aplikacji do uruchamiania w odpowiedniej wersji środowisko uruchomieniowe języka wspólnego (CLR), można wyświetlać i debugowania dzienniki aktywacji środowiska CLR. Te dzienniki może być bardzo przydatne podczas określania głównej przyczyny problemu aktywacji, gdy aplikacji ładuje inną wersję środowiska CLR, niż oczekiwano lub w ogóle nie jest ładowana środowiska CLR. [Błędy inicjowania programu .NET Framework: Zarządzanie czynności użytkownika](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) tym artykule omówiono środowisko CLR nie został znaleziony dla aplikacji.  
  
 Rejestrowanie aktywacji środowiska CLR może być włączone całego systemu za pomocą klucza rejestru HKEY_LOCAL_MACHINE lub zmienną środowiskową systemu. Dziennik zostaną wygenerowane do wpisu rejestru lub zmiennej środowiskowej zostanie usunięta. Alternatywnie można użyć użytkownika lub zmiennej środowiskowej proces lokalny do włączania rejestrowania zdarzeń z różnych zakresu i czasu trwania.  
  
 Dzienniki aktywacji środowiska CLR nie należy mylić z [dzienniki powiązań zestawów](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), które są całkowicie innej.  
  
## <a name="to-enable-clr-activation-logging"></a>Aby włączyć rejestrowanie aktywacji środowiska CLR  
  
#### <a name="using-the-registry"></a>Za pomocą rejestru  
  
1.  W Edytorze rejestru przejdź do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (na komputerze 32-bitowe) lub HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Folder NETFramework (na komputerze 64-bitowe).  
  
2.  Dodaj wartość ciągu o nazwie `CLRLoadLogDir`i ustaw ją na pełną ścieżkę istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.  
  
 Aktywacja rejestrowania pozostaje włączona do momentu usunięcia wartości ciągu.  
  
#### <a name="using-an-environment-variable"></a>Za pomocą zmiennej środowiskowej  
  
-   Ustaw `COMPLUS_CLRLoadLogDir` zmiennej środowiskowej na ciąg, który reprezentuje pełną ścieżkę istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.  
  
     Jak ustawić zmienną środowiskową określa zakres:  
  
    -   Jeśli zostanie ustawiona na poziomie systemu, aktywacji rejestrowanie jest włączone dla wszystkich aplikacji .NET Framework na tym komputerze, aż do usunięcia zmiennej środowiskowej.  
  
    -   Jeśli zostanie ustawiona na poziomie użytkownika, aktywacji rejestrowanie jest włączone tylko dla bieżącego konta użytkownika. Rejestrowanie będzie kontynuowane do czasu usunięcia zmiennej środowiskowej.  
  
    -   Jeśli ustawisz go z procesu przed załadowaniem CLR, aktywacji rejestrowanie jest włączone, aż do zakończenia procesu.  
  
    -   Jeśli zostanie ustawiona w wierszu polecenia przed uruchomieniem aplikacji, aktywacji rejestrowanie jest włączone dla dowolnej aplikacji, który jest uruchamiany z tego wiersza polecenia.  
  
     Na przykład aby aktywacji dzienniki są przechowywane w katalogu c:\clrloadlogs o zasięgu na poziomie procesu, Otwórz okno wiersza polecenia i wpisz następujące polecenie, aby uruchomić aplikację:  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a>Przykład  
 Dzienniki aktywacji środowiska CLR zapewniają dużą ilość danych o aktywacji środowiska CLR i korzystanie z aparatu CLR hostingu interfejsów API. Większość tych danych jest używana wewnętrznie przez firmę Microsoft, ale niektóre dane mogą być przydatne także deweloperom, zgodnie z opisem w tym artykule.  
  
 Dziennik odzwierciedla w kolejności CLR hostingu API wywołane. Obejmuje on też przydatne dane dotyczące zestawu zainstalowanych środowisk uruchomieniowych wykrył na tym komputerze. Format dziennika aktywacji środowiska CLR nie jest swoim udokumentowane, ale może służyć do pomocy deweloperów chcących rozwiązać problemy dotyczące aktywacji środowiska CLR.  
  
> [!NOTE]
>  Nie można otworzyć dziennika aktywacji, dopóki proces, który używa środowiska CLR został zakończony.  
  
> [!NOTE]
>  Dzienniki aktywacji środowiska CLR nie są zlokalizowane; są one zawsze generowane w języku angielskim.  
  
 W poniższym przykładzie dziennika aktywacji najbardziej przydatne informacje jest wyróżniony i opisem po dziennika.  
  
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
  
-   **Dziennik ładowania środowiska CLR** Określa ścieżkę do pliku wykonywalnego, który uruchomił proces, który załadowano kodu zarządzanego. Należy pamiętać, że może to być hostem natywnego.  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   **Zainstalowane środowisko uruchomieniowe** Zestaw CLR wersje zainstalowane na komputerze, przeznaczone dla żądania aktywacji.  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   **skompilowany jako wersja** jest wersja środowiska CLR, który został użyty do budowania plik binarny, który został dostarczony do metody, takie jak [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   **Instalacja funkcji na żądanie** odwołuje się do włączania programu .NET Framework 3.5 w systemie Windows 8. Zobacz [błędy inicjowania programu .NET Framework: Zarządzanie wrażeniami użytkownika](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) Aby uzyskać więcej informacji na temat tego scenariusza.  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie](../../../docs/framework/deployment/index.md)  
 [Instrukcje: Konfiguracja aplikacji do obsługi w programie .NET Framework 4 lub 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
