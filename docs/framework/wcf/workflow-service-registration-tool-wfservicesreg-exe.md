---
title: Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 0a9cd5039c085f82f5507c93ebe0855cc620825d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916822"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)
Narzędzie rejestracji usług przepływu pracy (WFServicesReg. exe) to autonomiczne narzędzie, które służy do dodawania, usuwania lub naprawiania elementów konfiguracji dla usług Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Składnia  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Uwagi  
 Narzędzie to można znaleźć w lokalizacji instalacji [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] , w tym%windir%\Microsoft.Net\Framework\v3.5 lub w%windir%\Microsoft.NET\Framework64\v3.5 na maszynach 64-bitowych.  
  
 W poniższych tabelach opisano opcje, które mogą być używane z narzędziem rejestracji usług przepływu pracy (WFServicesReg. exe).  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/c`|Konfiguruje usługi przepływu pracy systemu Windows. Używany w scenariuszach instalacji i naprawy.|  
|`/r`|Usuwa konfigurację usług Windows Workflow Services.|  
|`/v`|Drukuj pełne informacje (dla konfiguracji lub usuwania).|  
|`/m`|Włącza Format rejestrowania MSI.|  
|`/i`|Minimalizuje okno, gdy aplikacja jest uruchomiona.|  
  
## <a name="registration"></a>Rejestracja  
 Narzędzie sprawdza plik Web. config i rejestruje następujące elementy:  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]zestawy odwołań.  
  
- Dostawca kompilacji dla plików xoml.  
  
- Obsługa protokołu HTTP dla plików xoml i. rules.  
  
 Narzędzie sprawdza plik Machine. config i rejestruje następujące rozszerzenia:  
  
- behaviorExtensions  
  
- bindingElementExtensions  
  
- bindingExtensions  
  
 Narzędzie rejestruje także następujących importerów metadanych klienta:  
  
- policyImporters  
  
- wsdlImporters  
  
 Narzędzie rejestruje również właściwości xoml i. rules oraz programy obsługi w metabazie usług IIS.  
  
 W [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] systemach [!INCLUDE[wxp](../../../includes/wxp-md.md)] i na maszynach (IIS 5,1 i IIS 6,0) jest rejestrowany jeden zestaw właściwości xoml i rules.  
  
 Na komputerach 64-bitowych narzędzie rejestruje w trybie WOW mapowania skryptów, jeśli `Enable32BitAppOnWin64` przełącznik jest włączony, lub natywnie 64-bitowej mapy skryptów `Enable32BitAppOnWin64` , jeśli przełącznik jest wyłączony.  
  
 Na [!INCLUDE[wv](../../../includes/wv-md.md)] maszynach i na komputerach z systemem Windows Server 2008 (IIS 7,0 lub nowszym) są rejestrowane dwa zestawy programów xoml i.  
  
 Na komputerach 64-bitowych są zarejestrowane trzy zestawy programów obsługi (bez względu na stan `Enable32BitAppOnWin64` przełącznika): jeden dla trybu zintegrowanego, jeden dla klasycznego trybu WOW i jeden dla natywnego 64-bitowego trybu klasycznego.  
  
> [!NOTE]
> W przeciwieństwie do ServiceModelreg. exe, WFServicesReg. exe nie zezwala na dodawanie, usuwanie ani naprawianie skryptów lub programów obsługi dla określonej witryny sieci Web. Aby obejść ten problem, zobacz sekcję "Naprawa skryptów".  
  
## <a name="usage-scenarios"></a>Scenariusze użycia  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Instalowanie usług IIS po zainstalowaniu .NET Framework 3,5  
 Na komputerze program [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest instalowany przed instalacją usług IIS. [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] Ze względu na niedostępność metabazy usług IIS instalacja [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] programu kończy się powodzeniem bez instalowania. xoml i. rules.  
  
 Po zainstalowaniu usług IIS można użyć narzędzia WFServicesReg. exe z `/c` przełącznikiem, aby zainstalować te konkretne mapy skryptów.  
  
### <a name="repairing-the-scriptmaps"></a>Naprawianie skryptów  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Właściwości scriptmap usunięte w węźle witryny sieci Web  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] Na komputerze, xoml lub. reguły są przypadkowo usuwane z węzła witryny sieci Web. Można to naprawić, uruchamiając narzędzie WFServicesReg. exe z `/c` przełącznikiem.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Właściwości scriptmap usunięte w określonej witrynie sieci Web  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] Na komputerze, xoml lub. reguły są przypadkowo usuwane z określonej witryny sieci Web (na przykład domyślnej witryny sieci Web), a nie z węzła witryny sieci Web.  
  
 Aby naprawić usunięte programy obsługi dla określonej witryny sieci Web, należy uruchomić polecenie "WFServicesReg. exe/r", aby usunąć programy obsługi ze wszystkich witryn sieci Web, a następnie uruchomić polecenie "WFServicesReg. exe/c" w celu utworzenia odpowiednich programów obsługi dla wszystkich witryn sieci Web.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Konfigurowanie programów obsługi po przełączeniu trybu usług IIS  
 Gdy usługi IIS są w trybie konfiguracji udostępnionej i [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] są zainstalowane, metabaza usług IIS jest konfigurowana w lokalizacji udostępnionej. W przypadku przełączenia usług IIS do trybu konfiguracji nieudostępnionej, lokalna metabaza nie będzie zawierać wymaganych programów obsługi. Aby prawidłowo skonfigurować lokalną metabazę, możesz zaimportować udostępnioną metabazę do lokalnego lub uruchomić polecenie "WFServicesReg. exe/c", które konfiguruje lokalną metabazę.
