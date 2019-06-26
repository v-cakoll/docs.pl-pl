---
title: Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 211af75c04dfe971228bc1710fbe1fc4d7aaee60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402483"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)
Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe) jest autonomicznym narzędziem, które można dodać, usunąć lub naprawić elementy konfiguracji dla usług Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Składnia  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Uwagi  
 Narzędzie znajduje się w temacie [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] lokalizację instalacji, w szczególności % windir%\Microsoft.NET\Framework\v3.5 lub %windir%\Microsoft.NET\Framework64\v3.5 w 64-bitowych maszyn.  
  
 W poniższych tabelach opisano opcje, które mogą być używane z narzędzia rejestracji usług przepływu pracy (WFServicesReg.exe).  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/c`|Umożliwia skonfigurowanie usług przepływu pracy Windows. Używane w instalacji i naprawiania scenariuszy.|  
|`/r`|Usuwa konfigurację usługi przepływu pracy Windows.|  
|`/v`|Pełne informacje dotyczące drukowania (dla konfiguracji lub usuwania).|  
|`/m`|Włącza format rejestrowania tożsamości usługi Zarządzanej.|  
|`/i`|Minimalizuje okna, gdy aplikacja zostanie uruchomiona.|  
  
## <a name="registration"></a>Rejestracja  
 Narzędzie sprawdza plik Web.config i rejestruje następujące czynności:  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] zestawy referencyjne.  
  
- Dostawca kompilacji pliki xoml.  
  
- Aby uzyskać pliki xoml i Rules funkcje obsługi protokołu HTTP.  
  
 Narzędzie sprawdza plik Machine.config i rejestruje następujące rozszerzenia:  
  
- behaviorExtensions  
  
- bindingElementExtensions  
  
- bindingExtensions  
  
 Narzędzie rejestruje także następujące importerów metadane klienta:  
  
- policyImporters  
  
- wsdlImporters  
  
 Narzędzie rejestruje także xoml i Rules mapy skryptów i programów obsługi w metabazie IIS.  
  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../includes/wxp-md.md)] maszyny (usługi IIS 5.1 i IIS 6.0), jeden zestaw xoml i Rules mapy skryptów są zarejestrowane.  
  
 Na komputerach 64-bitowe narzędzie rejestruje mapy skryptów trybie WOW, jeśli `Enable32BitAppOnWin64` przełącznik jest włączony lub natywnych 64-bitowych mapy skryptów, jeśli `Enable32BitAppOnWin64` przełącznik jest wyłączony.  
  
 Na [!INCLUDE[wv](../../../includes/wv-md.md)] i Windows Server 2008 (usługi IIS 7.0 i nowsze wersje) maszyny, dwa zestawy xoml i Rules obsługi są zarejestrowane: jeden dla trybu zintegrowanego i jeden dla trybu klasycznego.  
  
 Na komputerach 64-bitowych zarejestrowano trzy rodzaje obsługi (bez względu na stan `Enable32BitAppOnWin64` przełącznika): jeden dla działania w trybie zintegrowanym, w trybie WOW klasycznym i jeden dla trybu macierzystego Classic 64-bitowych.  
  
> [!NOTE]
>  W odróżnieniu od ServiceModelreg.exe WFServicesReg.exe nie zezwala na dodawanie, usuwanie lub naprawianie mapy skryptów lub programów obsługi dla określonej witryny sieci Web. Obejście tego problemu znajduje się w sekcji "Naprawa mapy skryptów".  
  
## <a name="usage-scenarios"></a>Scenariusze użycia  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Instalowanie usług IIS po zainstalowaniu programu .NET Framework 3.5  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest zainstalowany przed instalacją usług IIS. Z powodu niedostępności metabazy usług IIS, instalacja [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] zakończy się pomyślnie bez konieczności instalowania xoml i Rules mapy skryptów.  
  
 Po zainstalowaniu usług IIS, można użyć narzędzia WFServicesReg.exe z `/c` przełącznik, aby zainstalować te określonego mapowania skryptów.  
  
### <a name="repairing-the-scriptmaps"></a>Naprawianie mapowania skryptów  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Mapowania skryptów usunięte w węźle witryn sieci Web  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny, xoml lub Rules zostanie przypadkowo usunięta z węzeł witryn sieci Web. Można to naprawić, uruchamiając narzędzie WFServicesReg.exe z `/c` przełącznika.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Mapowania skryptów usunięte w ramach określonej witryny sieci Web  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny, xoml lub Rules zostaną przypadkowo usunięte z określonej witryny sieci Web (na przykład, domyślna witryna sieci Web), a nie z węzła witryn sieci Web.  
  
 Aby naprawić usunięte programy obsługi dla określonej witryny sieci Web, należy uruchomić "WFServicesReg.exe/r" Aby usunąć obsługi z wszystkich witryn sieci Web, a następnie uruchom "WFServicesReg.exe c" można utworzyć odpowiednie programy obsługi dla wszystkich witryn sieci Web.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Konfigurowanie obsługi po przełączeniu do trybu usług IIS  
 Gdy program IIS jest w trybie konfiguracji udostępnionej i [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest zainstalowany, metabazy usług IIS jest skonfigurowane w lokalizacji udostępnionej. Jeśli usługi IIS przełączyć się do trybu konfiguracji nieudostępnione, lokalnej metabazy nie będzie zawierać wymagane programy obsługi. Aby poprawnie skonfigurować lokalne metabazy, możesz zaimportować udostępnionych metabazy do lokalnego lub wykonywania "WFServicesReg.exe /c", który konfiguruje metabazy lokalnej.
