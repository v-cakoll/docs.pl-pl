---
title: Rozwiązywanie problemów dotyczących konfiguracji
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9238c1a1c9092e6806ee941bd7c992071cf98e09
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="troubleshooting-setup-issues"></a>Rozwiązywanie problemów dotyczących konfiguracji
W tym temacie opisano sposoby rozwiązywania [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Konfigurowanie problemy.  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Wykonując operacji naprawy MSI na .NET Framework 3.0 nie naprawiane niektórych kluczy rejestru systemu Windows Communication Foundation  
 Jeśli usuniesz żadnego z następujących kluczy rejestru:  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
-   Mostek HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC 3.0.0.0  
  
 Klucze nie są ponownie tworzone po uruchomieniu naprawy przy użyciu Instalatora .NET Framework 3.0 uruchamiana z **Dodaj lub usuń programy** aplet **Panelu sterowania**. Aby ponownie utworzyć te klucze poprawnie, użytkownik musi odinstalowanie i ponowne zainstalowanie programu .NET Framework 3.0.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>Instalacja bloki uszkodzenie usługi WMI dostawcy programu Windows Communication Foundation WMI podczas instalacji pakietu .NET Framework 3.0  
 Uszkodzenie usługi WMI mogą zablokować instalację dostawcy usługi Windows Communication Foundation WMI. Podczas instalacji programu Windows Communication Foundation Instalator nie może zarejestrować plik MOF WCF za pomocą składnika mofcomp.exe. Poniżej przedstawiono listę symptomy:  
  
1.  Instalacja środowiska .NET framework 3.0 zakończy się pomyślnie, ale dostawca WCF WMI nie jest zarejestrowany.  
  
2.  Zdarzenie błędu pojawia się w dzienniku zdarzeń aplikacji, który odwołuje się do problemów rejestracji dostawcy WMI dla usług WCF lub systemem mofcomp.exe.  
  
3.  Plik dziennika instalacji o nazwie dd_wcf_retCA * w katalogu temp % % użytkownika zawiera odwołania do awarii można zarejestrować dostawcy WCF WMI.  
  
4.  W dzienniku zdarzeń lub ustawienia pliku dziennika śledzenia mogą być wyświetlone wyjątek, taki jak następujące:  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: nieoczekiwany wynik 3 wykonywania E:\WINDOWS\system32\wbem\mofcomp.exe z "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows komunikacji Foundation\ServiceModel.mof"  
  
     lub:  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException: Inicjator typu dla "System.Management.ManagementPath" wywołała wyjątek. ---> System.Runtime.InteropServices.COMException (0x80040154): Pobranie fabryki klasy COM dla składnika o identyfikatorze CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} nie powiodło się z powodu następującego błędu: 80040154.  
  
     lub:  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: nie można załadować pliku lub zestawu 'C:\WINDOWS\system32\wbem\mofcomp.exe' lub jednej z jego zależności. W systemie nie można odnaleźć określonego pliku.  
  
     Nazwa pliku: "C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Aby rozwiązać problem opisany wcześniej musi być wykonać następujące czynności.  
  
1.  Uruchom [narzędzie diagnostyczne WMI, w wersji 2.0](http://go.microsoft.com/fwlink/?LinkId=94685) napraw usługę WMI. Aby uzyskać więcej informacji na temat stosowania tego narzędzia, zobacz [narzędzie diagnostyczne WMI](http://go.microsoft.com/fwlink/?LinkId=94686) tematu.  
  
 Napraw instalację programu .NET Framework 3.0 za pomocą **Dodaj lub usuń programy** apletu znajduje się w **Panelu sterowania**, lub odinstalowywanie i ponowna instalacja programu .NET Framework 3.0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>Naprawianie platformy .NET Framework 3.0 po instalacji programu .NET Framework 3.5 usuwa elementy konfiguracji, które wprowadzono w programie .NET Framework 3.5 w pliku machine.config  
 Jeśli po zainstalowaniu Wykonaj naprawę programu .NET Framework 3.0 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], elementy konfiguracji wprowadzone przez [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] w pliku machine.config zostały usunięte. Jednak że plik web.config pozostanie niezmieniona. Należy naprawić [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] po za pomocą protokołu ARP, lub użyj [narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) z `/c` przełącznika.  
  
 [Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) znajduje się w temacie %windir%\Microsoft.NET\framework\v3.5\ lub %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Poprawnie skonfigurować usługi IIS dla usługi WCF/WF Webhost po zainstalowaniu programu .NET Framework 3.5  
 Gdy [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] instalacja nie powiedzie się skonfigurować dodatkowe [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-pokrewne ustawienia konfiguracji usług IIS, rejestruje błąd w dzienniku instalacji i kontynuuje. Próba uruchomienia aplikacji obiektów Workflowservice zakończy się niepowodzeniem, ponieważ brakuje wymaganych ustawień konfiguracyjnych. Na przykład ładowanie usługi xoml lub reguły może zakończyć się niepowodzeniem.  
  
 Aby obejść ten problem, użyj [narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) z `/c` przełącznik, aby poprawnie skonfigurować mapy skryptów programu IIS na komputerze. [Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) znajduje się w temacie %windir%\Microsoft.NET\framework\v3.5\ lub %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Nie można załadować typu 'System.ServiceModel.Activation.HttpModule' z zestawu ' System.ServiceModel, wersja 3.0.0.0, kultury = neutral, PublicKeyToken = b77a5c561934e089 "  
 Ten błąd występuje, gdy [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] jest zainstalowany, a następnie [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] włączono aktywację HTTP. Aby rozwiązać ten problem, uruchom następujące polecenie w wierszu polecenia z wewnątrz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] wiersza polecenia:  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje dotyczące konfiguracji](../../../docs/framework/wcf/samples/set-up-instructions.md)
