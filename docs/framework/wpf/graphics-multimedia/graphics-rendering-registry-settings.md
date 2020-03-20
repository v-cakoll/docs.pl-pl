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
ms.openlocfilehash: 85e32c99674cc95f670a4cb483b55865b996cb31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186422"
---
# <a name="graphics-rendering-registry-settings"></a>Ustawienie rejestru renderowania grafiki
W tym temacie przedstawiono omówienie ustawień rejestru renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafiki, które mają wpływ na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje.  

<a name="overview"></a>
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Kiedy używać ustawień rejestru renderowania grafiki  
 Te ustawienia rejestru są dostępne do rozwiązywania problemów, debugowania i pomocy technicznej dla produktu. Ponieważ zmiany w rejestrze mają wpływ na wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje, aplikacja nigdy nie powinna zmieniać tych kluczy rejestru automatycznie lub podczas instalacji.  
  
<a name="xpdmandwddm"></a>
## <a name="what-are-xpdm-and-wddm"></a>Co to są XPDM i WDDM?  
 Niektóre ustawienia rejestru renderowania grafiki mają różne wartości domyślne, w zależności od tego, czy karta wideo używa sterownika XPDM lub WDDM. XPDM to model sterownika ekranu systemu Microsoft Windows XP, a WDDM jest modelem sterownika ekranu systemu Windows. Usługa WDDM jest dostępna na komputerach z systemami Windows Vista i Windows 7. Program XPDM jest dostępny na komputerach z systemami Windows Vista, Microsoft Windows XP i Microsoft Windows Server 2003. Aby uzyskać więcej informacji na temat programu WDDM, zobacz Przewodnik po projekcie modelu sterownika ekranu [systemu Windows (WDDM).](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide)  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Ustawienia rejestru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia cztery ustawienia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rejestru do kontrolowania renderowania:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Wyłącz opcję przyspieszenia sprzętowego**|Określa, czy ma być włączone przyspieszanie sprzętowe.|  
|**Maksymalna wartość multipróbki**|Określa stopień wielowymirzalania dla antyaliasing 3-W zawartości.|  
|**Wymagane ustawienie daty sterownika wideo**|Określa, czy system wyłącza akcelerację sprzętową dla sterowników wydanych przed listopadem 2004 r.|  
|**Użyj opcji rasteryzatora referencyjnego**|Określa, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] czy należy używać rasteryzatora referencyjnego.|  
  
 Dostęp do tych ustawień można uzyskać za pomocą dowolnego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zewnętrznego narzędzia konfiguracyjnego, które wie, jak odwoływać się do ustawień rejestru. Te ustawienia można również utworzyć lub zmodyfikować, uzyskując dostęp do wartości bezpośrednio za pomocą Edytora rejestru systemu Windows.  
  
<a name="disablehardwareacceleration"></a>
## <a name="disable-hardware-acceleration-option"></a>Wyłącz opcję przyspieszenia sprzętowego  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Opcja wyłączanie akceleracji sprzętowej** umożliwia wyłączenie akceleracji sprzętowej do celów debugowania i testowania. Gdy widzisz artefakty renderowania w aplikacji, spróbuj wyłączyć akcelerację sprzętową. Jeśli artefakt zniknie, problem może dotyczyć sterownika wideo.  
  
 **Opcja wyłączanie akceleracji sprzętowej** jest wartością DWORD, która jest 0 lub 1. Wartość 1 wyłącza akcelerację sprzętową. Wartość 0 umożliwia akcelerację sprzętową, pod warunkiem, że system spełnia wymagania przyspieszania sprzętowego; Aby uzyskać więcej informacji, zobacz [Warstwy renderowania grafiki](../advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>
## <a name="maximum-multisample-value"></a>Maksymalna wartość multipróbki  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maksymalna wartość multisample** umożliwia dostosowanie maksymalnej ilości antyaliasingu zawartości 3-W. Użyj tego poziomu, aby wyłączyć antyaliasing 3-D w systemie Windows Vista.  
  
 **Maksymalna wartość multisample** jest wartość DWORD, która waha się od 0 do 16. Wartość 0 określa, że multisample antialiasing zawartości 3-W powinny być wyłączone, a wartość 16 będzie próbował użyć do 16x multisample antialiasing, jeśli jest obsługiwany przez kartę graficzną. Uważaj, że ustawienie tej wartości klucza rejestru na komputerach przy użyciu sterowników XPDM spowoduje, że aplikacje będą korzystać z dużej ilości dodatkowej pamięci wideo, zmniejszyć wydajność renderowania 3-W i może potencjalnie wprowadzić błędy renderowania i stabilność Problemy.  
  
 Jeśli ten klucz rejestru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie jest ustawiony, domyślnie 0 dla sterowników XPDM i 4 dla sterowników WDDM.  
  
<a name="requiredvideodriverdatesetting"></a>
## <a name="required-video-driver-date-setting"></a>Wymagane ustawienie daty sterownika wideo  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|Ciąg|  
  
 W listopadzie 2004 r. firma Microsoft wydała nową wersję wytycznych dotyczących testowania sterowników; sterowniki napisane po tej dacie oferują lepszą stabilność. Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użyje potoku akceleracji sprzętowej dla tych sterowników i powróci do renderowania oprogramowania dla sterowników XPDM opublikowanych przed tą datą.  
  
 **Wymagane ustawienie daty sterownika wideo** umożliwia określenie alternatywnej daty minimalnej dla sterowników XPDM. Datę wcześniejszą niż listopad 2004 należy określić tylko wtedy, gdy masz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pewność, że sterownik wideo jest wystarczająco stabilny, aby obsługiwać .  
  
 Wymagane ustawienie sterownika wideo przyjmuje ciąg następującego formatu:  
  
| |  
|-|  
|*YYYY* `/` *MM* `/` *DD*|  
  
 Tam, gdzie *YYYY* jest czterocyfrowym rokiem, *MM* jest dwucyfrowym miesiącem, a *DD* jest dniem dwucyfrowym. Gdy ta wartość jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nieustawiewa, używa listopada 2004 r. jako wymaganej daty sterownika wideo.  
  
<a name="usereferencerasterizeroption"></a>
## <a name="use-reference-rasterizer-option"></a>Użyj opcji rasteryzatora referencyjnego  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Opcja rasteryzatora referencyjnego umożliwia** wprowadzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] symulowanego trybu renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sprzętowego do debugowania: przechodzi w tryb sprzętowy, ale używa rasterysty oprogramowania referencyjnego Microsoft Direct3D, d3dref9.dll, zamiast rzeczywistego urządzenia sprzętowego.  
  
 Rasteryzator odniesienia jest bardzo powolny, ale omija sterownik wideo, aby uniknąć problemów z renderowaniem spowodowanych problemami ze sterownikami. Z tego powodu można użyć rasteryzatora referencyjnego, aby ustalić, czy problemy z renderowaniem są spowodowane przez sterownik wideo. Plik d3dref9.dll musi znajdować się w lokalizacji, w której aplikacja może uzyskać do niego dostęp, na przykład w dowolnej lokalizacji w ścieżce systemowej lub w lokalnym katalogu aplikacji.  
  
 **Opcja rasteryzatora odwołania do użycia** przyjmuje wartość DWORD. Wartość 0 wskazuje, że rasteryzator odniesienia nie jest używany. Wszystkie inne wartości niezerowe wymusza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używać rasteryzatora odniesienia.  
  
## <a name="see-also"></a>Zobacz też

- [Poziomy zmiany grafiki](../advanced/graphics-rendering-tiers.md)
- [Przegląd Renderowanie grafiki WPF](wpf-graphics-rendering-overview.md)
