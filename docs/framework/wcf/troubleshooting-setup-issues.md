---
title: Rozwiązywanie problemów dotyczących konfiguracji
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 2cd9ced4f0780b1a6f63e4a5833e20ac91870121
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121583"
---
# <a name="troubleshoot-setup-issues"></a>Rozwiązywanie problemów z konfiguracją

W tym artykule opisano sposób rozwiązywania problemów z programem Windows Communication Foundation (WCF).  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Niektóre klucze rejestru programu Windows Communication Foundation nie są naprawione przez wykonanie operacji naprawy MSI w programie .NET Framework 3.0  
 Jeśli usuniesz którykolwiek z następujących kluczy rejestru:  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Mostek 3.0.0.0  
  
 Klucze nie są tworzone ponownie, jeśli uruchomiono naprawę przy użyciu instalatora programu .NET Framework 3.0 uruchomionego z apletu **Dodaj/Usuń programy** w **Panelu sterowania**. Aby poprawnie utworzyć te klucze, użytkownik musi odinstalować i ponownie zainstalować program .NET Framework 3.0.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>Uszkodzenie usługi WMI blokuje instalację dostawcy WMI programu Windows Communication Foundation podczas instalacji pakietu .NET Framework 3.0  
 Uszkodzenie usługi WMI może zablokować instalację dostawcy WMI programu Windows Communication Foundation. Podczas instalacji instalator Windows Communication Foundation nie może zarejestrować pliku WCF .mof przy użyciu składnika mofcomp.exe. Poniżej znajduje się lista objawów:  
  
1. Instalacja programu .NET Framework 3.0 kończy się pomyślnie, ale dostawca WMI WCF nie jest zarejestrowany.  
  
2. W dzienniku zdarzeń aplikacji pojawia się zdarzenie błędu, które odwołuje się do problemów z zarejestrowaniem dostawcy usługi WMI dla wcf lub uruchomieniem pliku mofcomp.exe.  
  
3. Plik dziennika instalacji o nazwie dd_wcf_retCA* w katalogu %temp% użytkownika zawiera odwołania do niepowodzenia rejestracji dostawcy WCF WMI.  
  
4. W pliku dziennika zdarzeń lub pliku dziennika śledzenia konfiguracji może znajdować się wyjątek, taki jak poniższy:  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: Nieoczekiwany wynik 3 wykonanie E:\WINDOWS\system32\wbem\mofcomp.exe z "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"  
  
     lub:  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException: Inicjator typu dla 'System.Management.ManagementPath' zgłosił wyjątek. ---> System.Runtime.InteropServices.COMException (0x80040154): Pobieranie fabryki klasy COM dla składnika z identyfikatorem CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} nie powiodło się z powodu następującego błędu: 80040154.  
  
     lub:  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Nie można załadować pliku lub zestawu "C:\WINDOWS\system32\wbem\mofcomp.exe" lub jednej z jego zależności. W systemie nie można odnaleźć określonego pliku.  
  
     Nazwa pliku: 'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Aby rozwiązać opisany wcześniej problem, należy wykonać następujące kroki.  
  
1. Uruchom [narzędzie diagnostyki WMI w](https://www.microsoft.com/download/details.aspx?id=7684) celu naprawy usługi WMI. Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz [Narzędzie diagnostyki WMI](https://docs.microsoft.com/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).  
  
 Napraw instalację programu .NET Framework 3.0 za pomocą apletu **Dodaj/Usuń programy znajdującego** się w **Panelu sterowania**lub odinstaluj/zainstaluj ponownie program .NET Framework 3.0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>Naprawa programu .NET Framework 3.0 po instalacji programu .NET Framework 3.5 usuwa elementy konfiguracyjne wprowadzone przez program .NET Framework 3.5 w pliku machine.config  
 Jeśli po zainstalowaniu programu .NET Framework 3.0 zostanie naprawiona program .NET Framework 3.5, elementy konfiguracji wprowadzone przez program .NET Framework 3.5 w pliku machine.config zostaną usunięte. Jednak web.config pozostaje nienaruszony. Obejście jest naprawienie .NET Framework 3.5 po tym za pośrednictwem ARP lub użyj [Narzędzia rejestracji usługi WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) z przełącznikiem. `/c`  
  
 [Narzędzie do rejestracji usługi WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) można znaleźć pod adresem %windir%\Microsoft.NET\framework\v3.5\ lub %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Poprawnie konfigurować usługi IIS dla WCF/WF Webhost po zainstalowaniu programu .NET Framework 3.5  
 Gdy instalacja programu .NET Framework 3.5 nie może skonfigurować dodatkowych ustawień konfiguracji usług IIS związanych z WCF, rejestruje błąd w dzienniku instalacji i kontynuuje. Każda próba uruchomienia aplikacji WorkflowServices zakończy się niepowodzeniem, ponieważ brakuje wymaganych ustawień konfiguracji. Na przykład ładowanie usługi xoml lub reguły może zakończyć się niepowodzeniem.  
  
 Aby obejść ten problem, użyj [narzędzia do rejestracji usługi WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) z przełącznikiem, `/c` aby prawidłowo skonfigurować mapy skryptów usług IIS na komputerze. [Narzędzie do rejestracji usługi WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) można znaleźć pod adresem %windir%\Microsoft.NET\framework\v3.5\ lub %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Nie można załadować typu "System.ServiceModel.Activation.HttpModule" z zestawu "System.ServiceModel, wersja 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
 Ten błąd występuje, jeśli program .NET Framework 4 jest zainstalowany, a następnie WCF HTTP Aktywacja jest włączona. Aby rozwiązać ten problem, uruchom następujący wiersz polecenia z wiersza polecenia dewelopera dla programu Visual Studio:  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje dotyczące konfiguracji](./samples/set-up-instructions.md)
