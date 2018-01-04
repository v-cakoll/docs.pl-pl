---
title: Ustawienie rejestru renderowania grafiki
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a760f910bfd9e64fddfe2e7db3bb380cf744719d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-rendering-registry-settings"></a>Ustawienie rejestru renderowania grafiki
Ten temat zawiera omówienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderującego ustawień rejestru, które mają wpływ na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  

  
<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Kiedy należy używać ustawień rejestru renderowania grafiki  
 Te ustawienia są dostępne dla rozwiązywania problemów, debugowanie i celów pomocy technicznej produktu. Ponieważ zmiany w rejestrze mają wpływ na wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, aplikacja nigdy nie powinien alter te klucze rejestru, automatycznie lub podczas instalacji.  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a>Jakie są XPDM i WDDM?  
 Niektóre ustawienia rejestru renderującego mają przypisane wartości domyślne różne, w zależności od tego, czy korzysta z XPDM lub WDDM sterownik karty wideo. Jest XPDM [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] modelu sterownika wyświetlania i WDDM jest modelu sterownika wyświetlania systemu Windows. WDDM jest dostępna na komputerach z systemem [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] i [!INCLUDE[win7](../../../../includes/win7-md.md)]. XPDM jest dostępna na komputerach z systemem [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)], [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)], i [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)]. Aby uzyskać więcej informacji na temat WDDM, zobacz [przewodnik projektowania modelu sterowników systemu Windows Vista wyświetlania](http://go.microsoft.com/fwlink/?LinkId=178394).  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Ustawienia rejestru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia cztery ustawienia rejestru dla kontrolowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Wyłącz opcję Przyspieszanie sprzętowe**|Określa, czy powinno być włączone przyspieszanie sprzętowe.|  
|**Maksymalna wartość wielopróbkowego**|Określa stopień multisampling dla antialiasingu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] zawartości.|  
|**Wymagane sterownik wideo daty ustawienie**|Określa, czy system wyłącza przyspieszanie sprzętowe sterowniki wydane zanim listopad 2004.|  
|**Opcja rasteryzator odwołania**|Określa, czy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] należy używać rasteryzator odwołania.|  
  
 Te ustawienia są dostępne dla dowolnego narzędzia konfiguracji zewnętrznego, który potrafi odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ustawień rejestru. Te ustawienia można również utworzony lub zmodyfikowany, uzyskując dostęp do wartości bezpośrednio za pomocą [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Edytor rejestru.  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a>Wyłącz opcję Przyspieszanie sprzętowe  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Wyłączyć opcję Przyspieszanie sprzętowe** można wyłączyć przyspieszanie sprzętowe dla celów debugowania i testowania. Gdy pojawi się artefaktów renderowania w aplikacji, spróbuj wyłączyć przyspieszanie sprzętowe. Jeśli znika artefaktu, problem może być ze sterownikiem wideo.  
  
 **Wyłączyć opcję Przyspieszanie sprzętowe** jest wartość typu DWORD 0 lub 1. Wartość 1 powoduje wyłączenie przyspieszanie sprzętowe. Wartość 0 umożliwia przyspieszanie sprzętowe, pod warunkiem system spełnia wymagania przyspieszanie sprzętowe; Aby uzyskać więcej informacji, zobacz [warstw renderowania grafiki](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a>Maksymalna wartość wielopróbkowego  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maksymalna wartość wielopróbkowego** umożliwia dostosowanie maksymalną ilość antialiasingu z [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] zawartości. Użyj tego poziomu, aby wyłączyć [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] antialiasingu w [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] lub włączyć ją w [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].  
  
 **Maksymalna wartość wielopróbkowego** jest z zakresu od 0 do 16 wartości DWORD. Wartość 0 oznacza, że wielopróbkowego antialiasingu zawartości 3-powinny być wyłączone i wartość 16 podejmie próbę użycia do 16 x wielopróbkowego antialiasingu, jeśli jest to obsługiwane przez kartę wideo. Należy pamiętać, że ustawienie tej wartości klucza rejestru na komputerach przy użyciu sterowników XPDM spowoduje aplikacji do korzystania z dużą ilością dodatkową pamięć, zmniejszyć wydajność [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] renderowania i może powodować błędy renderowania i Problemy stabilności.  
  
 Gdy ten klucz rejestru nie jest ustawiona, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wartość domyślna to 0 XPDM sterowniki i 4 dla sterowników WDDM.  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a>Wymagane sterownik wideo daty ustawienie  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|String|  
  
 W listopadzie 2004 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] wydana nowa wersja sterownika wytyczne testowania; sterowniki zapisać po tej daty oferta większa stabilność. Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użyje potoku przyspieszanie sprzętowe dla te sterowniki i powróci do renderowania oprogramowania sterowniki XPDM opublikowane przed tą datą.  
  
 **Wymagane ustawienie daty sterownik wideo** umożliwia określenie alternatywnej Minimalna data XPDM sterowniki. Tylko należy określić datę starszych niż listopada 2004, jeśli masz pewność, że sterownik wideo jest stabilna do obsługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Ustawienie wymagane sterownik wideo ma ciągu o następującym formacie:  
  
||  
|-|  
|*RRRR* `/` *MM* `/` *DD*|  
  
 Gdzie *rrrr* jest rokiem czterocyfrowym *MM* miesiąc dwucyfrowe i *DD* dzień dwóch cyfr. Gdy ta wartość jest nieustawioną [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa listopada 2004 jako daty wymagane sterownik wideo.  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a>Opcja rasteryzator odwołania  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Opcja rasteryzator odwołanie** umożliwia wymuszenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w tryb renderowania symulowane sprzętu do debugowania: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przechodzi do trybu sprzętu, ale używa [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] odwołania rasteryzator oprogramowania d3dref9.dll, zamiast w rzeczywistości urządzeniem sprzętowym.  
  
 Rasteryzator odwołanie odbywa się bardzo wolno, ale pomija sterownik wideo, aby uniknąć problemów renderowania spowodowane przez problemy sterownika. Z tego powodu rasteryzator odwołania służy do określenia, czy problemy z renderowaniem są powodowane przez sterownik wideo. Plik d3dref9.dll musi być w lokalizacji, w którym aplikacja do niego dostęp, takich jak w dowolnej lokalizacji w ścieżce systemowej lub w lokalnym katalogu aplikacji.  
  
 **Opcja rasteryzator odwołanie** przyjmuje wartość typu DWORD. Wartość 0 wskazuje, czy rasteryzator odwołania nie jest używany. Inne wartości niezerowej siły [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do użycia rasteryzator odwołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Warstwy renderowania grafiki](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
