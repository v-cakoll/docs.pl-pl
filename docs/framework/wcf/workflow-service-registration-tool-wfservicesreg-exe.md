---
title: Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 3ea0f737cc050ec3f918044e0e105a41011a3e25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)
Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe) jest autonomicznym narzędziem, które można dodać, usunąć lub napraw elementy konfiguracji dla usług Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Składnia  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Uwagi  
 Narzędzie znajduje się w temacie [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] lokalizacja instalacji, w szczególności % windir%\Microsoft.NET\Framework\v3.5 lub %windir%\Microsoft.NET\Framework64\v3.5 w 64-bitowych maszyn.  
  
 W poniższych tabelach opisano opcje, które mogą być używane z narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe).  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/c`|Konfiguruje usługi przepływu pracy systemu Windows. Używane w instalacji i naprawy scenariuszy.|  
|`/r`|Usuwa konfiguracji usługi przepływu pracy systemu Windows.|  
|`/v`|Pełne informacje dotyczące drukowania (dla konfiguracji lub usuwania).|  
|`/m`|Włącza format rejestrowania MSI.|  
|`/i`|Minimalizuje okno po uruchomieniu aplikacji.|  
  
## <a name="registration"></a>Rejestracja  
 Narzędzie bada pliku Web.config i rejestruje następujące czynności:  
  
-   [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] zestawy odwołań.  
  
-   Dostawcę kompilacji dla plików xoml.  
  
-   Programy obsługi HTTP pliki xoml i rules.  
  
 Narzędzie bada pliku Machine.config i rejestruje następujące rozszerzenia:  
  
-   behaviorExtensions  
  
-   bindingElementExtensions  
  
-   bindingExtensions  
  
 Narzędzie rejestruje także następujące importerów metadane klienta:  
  
-   policyImporters  
  
-   wsdlImporters  
  
 Narzędzie rejestruje także xoml i Rules mapy skryptów i obsługi w metabazie usług IIS.  
  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../includes/wxp-md.md)] maszyny (usługi IIS 5.1 i [!INCLUDE[iis601](../../../includes/iis601-md.md)]), jeden zestaw xoml i Rules mapy skryptów są zarejestrowane.  
  
 Na komputerach 64-bitowych, narzędzie rejestruje mapy skryptów trybie WOW, jeśli `Enable32BitAppOnWin64` przełącznik jest włączone lub natywnych 64-bitowych mapy skryptów, jeśli `Enable32BitAppOnWin64` przełącznik jest wyłączony.  
  
 Na [!INCLUDE[wv](../../../includes/wv-md.md)] i Windows Server 2008 (usługi IIS 7.0 lub nowszym) maszyny, dwa zestawy xoml i Rules są zarejestrowane: jeden dla trybu zintegrowanego i jeden dla trybu klasycznego.  
  
 Na komputerach 64-bitowych, są rejestrowane trzy zestawy programów obsługi (niezależnie od stanu `Enable32BitAppOnWin64` przełącznika): jeden dla działania w trybie zintegrowanym, w trybie WOW klasycznym i jeden do trybu macierzystego Classic 64-bitowych.  
  
> [!NOTE]
>  W odróżnieniu od ServiceModelreg.exe WFServicesReg.exe nie zezwala na dodawanie, usuwanie lub naprawianie mapy skryptów lub programy obsługi dla określonej witryny sieci Web. Obejścia tego problemu zobacz sekcję "Naprawianie mapy skryptów".  
  
## <a name="usage-scenarios"></a>Scenariusze użycia  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Instalowanie programu IIS po zainstalowaniu programu .NET Framework 3.5  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest zainstalowany przed instalacją usług IIS. Z powodu niedostępności metabazy usług IIS, instalacja [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] zakończy się pomyślnie bez instalowania xoml i Rules mapy skryptów.  
  
 Po zainstalowaniu usług IIS, można użyć narzędzia WFServicesReg.exe z `/c` przełącznik, aby zainstalować te określone mapy skryptów.  
  
### <a name="repairing-the-scriptmaps"></a>Naprawianie mapowania skryptów  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Usunięte w węźle witryn sieci Web właściwościach scriptmap  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny, xoml lub Rules zostaną przypadkowo usunięte z węzła witryn sieci Web. Można to naprawić, uruchamiając narzędzie WFServicesReg.exe z `/c` przełącznika.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Usunięte w obszarze określonej witryny sieci Web właściwościach scriptmap  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny, xoml lub Rules zostaną przypadkowo usunięte z określonej witryny sieci Web (na przykład domyślna witryna sieci Web), a nie z węzła witryn sieci Web.  
  
 Aby naprawić usunięto programy obsługi dla określonej witryny sieci Web, należy uruchomić "WFServicesReg.exe r" Aby usunąć obsługi z wszystkich witryn sieci Web, a następnie uruchomić "WFServicesReg.exe c" Aby utworzyć odpowiednie programy obsługi dla wszystkich witryn sieci Web.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Konfigurowanie obsługi po przełączeniu w tryb usług IIS  
 Gdy usługi IIS działają w trybie konfiguracji udostępnionej i [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest zainstalowany, metabazy usług IIS jest skonfigurowany w lokalizacji udostępnionej. Jeśli usługi IIS nastąpi przełączenie do trybu konfiguracji nieudostępnione, metabazy lokalnej nie będzie zawierać wymagane programy obsługi. Aby poprawnie skonfigurować lokalne metabazy, możesz zaimportować udostępnionego metabazy do lokalnego lub wykonywania "WFServicesReg.exe /c", który konfiguruje metabazy lokalnej.
