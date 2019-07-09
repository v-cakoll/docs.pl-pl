---
title: Ustawienie rejestru renderowania grafiki
ms.date: 03/30/2017
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
ms.openlocfilehash: b1c61aa333c428e5cb811a5d19469516cbb813e3
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663157"
---
# <a name="graphics-rendering-registry-settings"></a>Ustawienie rejestru renderowania grafiki
Ten temat zawiera omówienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderującego ustawień rejestru, które wpływają na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  

<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Kiedy należy używać ustawień rejestru renderowania grafiki  
 Te ustawienia są dostarczane dla rozwiązywania problemów, debugowania i do celów obsługi produktu. Ponieważ zmiany w rejestrze mają wpływ na wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, Twoja aplikacja nigdy nie powinien alter tych kluczy rejestru, automatycznie, lub podczas instalacji.  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a>Jakie są XPDM i WDDM?  
 Niektóre ustawienia rejestru renderującego mają różne domyślne wartości w zależności od tego, czy korzysta z XPDM lub WDDM sterownik karty wideo. Jest XPDM [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] modelu sterownika wyświetlania i WDDM jest Model sterownika wyświetlania Windows. WDDM jest dostępna na komputerach z systemem [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] i [!INCLUDE[win7](../../../../includes/win7-md.md)]. XPDM jest dostępna na komputerach z systemem [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)], [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)], i [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)]. Aby uzyskać więcej informacji na temat WDDM zobacz [przewodnik projektowania modelu sterownika Windows Vista wyświetlania](https://go.microsoft.com/fwlink/?LinkId=178394).  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Ustawienia rejestru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia cztery ustawienia rejestru dla kontrolowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Wyłącz opcję Przyspieszanie sprzętowe**|Określa, czy powinno być włączone przyspieszanie sprzętowe.|  
|**Maksymalna wartość wielopróbkowego**|Określa stopień multisampling antyaliasingu do zawartości 3D.|  
|**Wymagany sterownik wideo daty ustawienie**|Określa, czy system wyłącza przyspieszanie sprzętowe dla sterowników wydanych przed listopada 2004.|  
|**Za pomocą opcji rasteryzatora odwołanie**|Określa, czy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] należy używać rasteryzatora odwołania.|  
  
 Te ustawienia są dostępne dla dowolnego narzędzia konfiguracji zewnętrznego, który wie, jak utworzyć odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ustawień rejestru. Te ustawienia można również utworzone lub zmodyfikowane, uzyskując dostęp do wartości bezpośrednio przy użyciu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Edytora rejestru.  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a>Wyłącz opcję Przyspieszanie sprzętowe  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Wyłączyć opcję Przyspieszanie sprzętowe** pozwala wyłączyć przyspieszanie sprzętowe na potrzeby debugowania i testowania. Gdy pojawi się renderowania artefaktów w aplikacji, spróbuj wyłączyć przyspieszanie sprzętowe. Jeśli artefaktu znika, problem może być za pomocą sterownika wideo.  
  
 **Wyłączyć opcję Przyspieszanie sprzętowe** jest wartość typu DWORD, która jest równa 0 lub 1. Wartość 1 powoduje wyłączenie przyspieszanie sprzętowe. Wartość 0 umożliwia przyspieszanie sprzętowe, pod warunkiem system spełnia wymagania przyspieszanie sprzętowe; Aby uzyskać więcej informacji, zobacz [poziomy renderowania grafiki](../advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a>Maksymalna wartość wielopróbkowego  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maksymalną wartość wielopróbkowego** umożliwia dostosowanie maksymalną ilość antialiasingu zawartości 3D. Użyj tego poziomu, aby wyłączyć antialiasingu 3-w [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] lub ją włączyć w [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].  
  
 **Maksymalną wartość wielopróbkowego** jest wartość typu DWORD z zakresu od 0 do 16. Wartość 0 oznacza, że wielopróbkowego antialiasingu zawartości 3D powinny być wyłączone i wartość 16 spróbuje użyć maksymalnie 16 x wielopróbkowego antialiasingu, jeśli jest obsługiwany przez karty wideo. Należy pamiętać, że ustawienie tej wartości klucza rejestru na komputerach za pomocą sterowników XPDM spowoduje, że aplikacje korzystać z dużą ilością dodatkową pamięć, zmniejszyć wydajność renderowania 3W i może potencjalnie wprowadzić błędy renderowania i stabilności problemy.  
  
 Gdy ten klucz rejestru nie jest ustawiona, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wartość domyślna to 0 dla sterowników XPDM i 4 dla sterowników WDDM.  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a>Wymagany sterownik wideo daty ustawienie  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|String|  
  
 W listopadzie, 2004 r. [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] wydana nowa wersja sterownika wytyczne testowania; sterowniki minionych stabilności lepsza oferta daty. Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użyje potoku przyspieszanie sprzętowe te sterowniki, a następnie powróci do renderowania oprogramowania dla sterowników XPDM opublikowanych przed tą datą.  
  
 **Wymagane ustawienie daty sterownika wideo** umożliwia określenie alternatywnej minimalnej daty XPDM sterowniki. Daty wcześniejszej niż listopada 2004 należy określić tylko, jeśli masz pewność, że sterownik wideo jest stabilna, aby obsługiwać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Ustawienie wymaganego sterownika wideo ma następujący format ciągu:  
  
| |  
|-|  
|*RRRR* `/` *MM* `/` *DD*|  
  
 Gdzie *rrrr* jest czterocyfrowy rok, *MM* jest dwucyfrowy miesiąc i *DD* jest dniem dwóch cyfr. Jeśli ustawiono tę wartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa listopada 2004 jako daty wymaganego sterownika wideo.  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a>Za pomocą opcji rasteryzatora odwołanie  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Za pomocą opcji rasteryzatora odwołanie** umożliwia wymuszenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tryb renderowania symulowane sprzętu do debugowania: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przechodzi w tryb sprzętu, ale używa [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] odwołania rasteryzatora oprogramowania d3dref9.dll zamiast w rzeczywistości urządzeniem sprzętowym.  
  
 Rasteryzatora odwołanie jest bardzo długi, ale pomija sterownika wideo, aby uniknąć jakichkolwiek problemów z renderowaniem spowodowane przez problemy sterownika. Z tego powodu można użyć rasteryzatora odwołania, aby określić, jeśli problemy z renderowaniem są spowodowane przez sterownik wideo. Plik d3dref9.dll musi być w lokalizacji, w którym aplikacja do niego dostęp, takie jak w dowolnym miejscu w ścieżce systemowej lub w lokalnym katalogu aplikacji.  
  
 **Za pomocą opcji rasteryzatora odwołanie** przyjmuje wartość typu DWORD. Wartość 0 wskazuje, że rasteryzatora odwołania nie jest używany. Inne siły wartość niezerową [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używać rasteryzatora odwołania.  
  
## <a name="see-also"></a>Zobacz także

- [Warstwy renderowania grafiki](../advanced/graphics-rendering-tiers.md)
- [Renderowanie grafiki WPF — przegląd](wpf-graphics-rendering-overview.md)
