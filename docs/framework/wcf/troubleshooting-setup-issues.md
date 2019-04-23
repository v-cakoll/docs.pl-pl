---
title: Rozwiązywanie problemów dotyczących konfiguracji
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 69242ec745f2a5b945ae64eb558070dbf0d39c10
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299621"
---
# <a name="troubleshooting-setup-issues"></a>Rozwiązywanie problemów dotyczących konfiguracji
W tym temacie opisano, jak rozwiązywać problemy z Windows Communication Foundation (WCF), skonfigurować problemów.  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Niektóre klucze rejestru systemu Windows Communication Foundation nie są naprawiona przez wykonanie operacji naprawy MSI na .NET Framework 3.0  
 Jeśli usuniesz żadnego z następujących kluczy rejestru:  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0  
  
 Klucze nie są ponownie tworzone po uruchomieniu naprawy za pomocą Instalatora programu .NET Framework 3.0 uruchomionego z **Dodaj/Usuń programy** aplet **Panelu sterowania**. Aby ponownie utworzyć te klucze poprawnie, użytkownik musi odinstalowanie i ponowne zainstalowanie programu .NET Framework 3.0.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>Instalacja bloki uszkodzenie usługi WMI podczas instalacji pakietu .NET Framework 3.0 dostawcy WMI programu Windows Communication Foundation  
 Uszkodzenie usługi WMI mogą blokować instalację dostawcy usługi WMI do programu Windows Communication Foundation. Podczas instalacji programu Windows Communication Foundation Instalator nie mógł zarejestrować plik MOF programu WCF za pomocą składnika mofcomp.exe. Oto lista objawy:  
  
1. Instalacja środowiska .NET framework 3.0 zakończy się pomyślnie, ale dostawca WMI usługi WCF nie jest zarejestrowany.  
  
2. Zdarzenie błędu pojawia się w dzienniku zdarzeń aplikacji, która odwołuje się problemy dotyczące rejestrowania dostawcy WMI dla usług WCF lub systemem mofcomp.exe.  
  
3. W pliku dziennika Instalatora o nazwie dd_wcf_retCA * w katalogu temp % % użytkownika zawiera odwołania do błędów, aby zarejestrować dostawcę WMI usługi WCF.  
  
4. Wyjątek taki poniżej mogą być wymienione w pliku dziennika śledzenia dziennika zdarzeń lub instalacji:  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: Nieoczekiwany wynik 3 wykonywania E:\WINDOWS\system32\wbem\mofcomp.exe za pomocą "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows komunikacji Foundation\ServiceModel.mof"  
  
     lub:  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException: Inicjator typu "System.Management.ManagementPath" zgłosiła wyjątek. ---> System.Runtime.InteropServices.COMException (0x80040154): Trwa pobieranie fabryki klasy COM dla składnika o identyfikatorze CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} nie powiodło się z powodu następującego błędu: 80040154.  
  
     lub:  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Nie można załadować pliku lub zestawu "C:\WINDOWS\system32\wbem\mofcomp.exe" lub jednej z jego zależności. W systemie nie można odnaleźć określonego pliku.  
  
     Nazwa pliku: 'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Poniższe kroki musi występować w celu rozwiązania problemu opisanego wcześniej.  
  
1. Uruchom [narzędzie diagnostyczne WMI, wersja 2.0](https://go.microsoft.com/fwlink/?LinkId=94685) naprawy usługi WMI. Aby uzyskać więcej informacji dotyczących używania tego narzędzia, zobacz [narzędzie diagnostyczne WMI](https://go.microsoft.com/fwlink/?LinkId=94686) tematu.  
  
 Napraw instalację programu .NET Framework 3.0 za pomocą **Dodaj/Usuń programy** apletu znajduje się w **Panelu sterowania**, lub odinstalowanie/ponownie zainstalowanie programu .NET Framework 3.0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>Naprawianie .NET Framework 3.0 po instalacji programu .NET Framework 3.5 spowoduje usunięcie elementów konfiguracji, które wprowadzono w programie .NET Framework 3.5 w pliku machine.config  
 Jeśli po zainstalowaniu Wykonaj naprawę środowiska .NET Framework 3.0 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], elementy konfiguracji, wynikające z [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] w pliku machine.config są usuwane. Jednak pliku web.config pozostaje bez zmian. Obejście polega na napraw [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] później za pomocą protokołu ARP lub użyj [narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) z `/c` przełącznika.  
  
 [Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) znajduje się w temacie %windir%\Microsoft.NET\framework\v3.5\ lub %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Skonfigurować usługi IIS prawidłowo hostem sieci Web WCF/WF po zainstalowaniu środowiska .NET Framework 3.5  
 Gdy [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] instalacja nie powiedzie się skonfigurować dodatkowe ustawienia konfiguracji związane z WCF IIS, rejestruje błąd w dzienniku instalacji i jest kontynuowane. Każda próba uruchomienia aplikacji WorkflowServices zakończy się niepowodzeniem, ponieważ brakuje wymaganych ustawień konfiguracji. Na przykład podczas ładowania pliku xoml lub zasady usługi może zakończyć się niepowodzeniem.  
  
 Aby obejść ten problem, użyj [narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) z `/c` przełącznik, aby poprawnie skonfigurować mapy skryptów usług IIS na komputerze. [Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) znajduje się w temacie %windir%\Microsoft.NET\framework\v3.5\ lub %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Nie można załadować typu "System.ServiceModel.Activation.HttpModule" z zestawu "System.ServiceModel, wersja 3.0.0.0, kulturze = neutral, PublicKeyToken = b77a5c561934e089"  
 Ten błąd występuje, jeśli [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] jest zainstalowany i Aktywacja HTTP programu WCF jest włączone. Aby rozwiązać ten problem, uruchom następujące polecenie wiersza polecenia z wewnątrz wiersz polecenia programisty dla programu Visual Studio:  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje dotyczące konfiguracji](../../../docs/framework/wcf/samples/set-up-instructions.md)
