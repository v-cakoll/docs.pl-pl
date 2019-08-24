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
ms.openlocfilehash: f2af32315f8f955495c51f2928c2b8eed5350759
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016084"
---
# <a name="graphics-rendering-registry-settings"></a>Ustawienie rejestru renderowania grafiki
Ten temat zawiera omówienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ustawień rejestru renderowania grafiki, które mają wpływ na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje.  

<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Kiedy używać ustawień rejestru renderowania grafiki  
 Te ustawienia rejestru są dostępne na potrzeby rozwiązywania problemów, debugowania i obsługi produktów. Ponieważ zmiany w rejestrze wpływają na wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje, aplikacja nie powinna automatycznie zmieniać tych kluczy rejestru ani podczas instalacji.  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a>Co to są XPDM i WDDM?  
 Niektóre ustawienia rejestru renderowania grafiki mają różne wartości domyślne, w zależności od tego, czy karta wideo korzysta ze sterownika XPDM czy WDDM. XPDM to [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] model sterownika wyświetlania, a WDDM to model sterownika wyświetlania systemu Windows. WDDM jest dostępny na komputerach z [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] systemami [!INCLUDE[win7](../../../../includes/win7-md.md)]i. XPDM jest dostępna na komputerach z [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]systemami [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)], i [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)]. Aby uzyskać więcej informacji na temat usługi WDDM, zobacz [Przewodnik dotyczący projektowania modelu sterownika wyświetlania systemu Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178394).  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Ustawienia rejestru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia cztery ustawienia rejestru do kontrolowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Wyłącz opcję przyspieszania sprzętowego**|Określa, czy przyspieszenie sprzętowe powinno być włączone.|  
|**Maksymalna wartość wielopróbkowa**|Określa stopień próbkowania wielostronicowego do wygładzania zawartości 3-D.|  
|**Wymagane ustawienie daty sterownika wideo**|Określa, czy system wyłącza przyspieszenie sprzętowe dla sterowników wydanych przed listopad 2004.|  
|**Użyj opcji rasteryzatora odwołań**|Określa, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] czy powinien być używany Rasteryzacja odwołania.|  
  
 Dostęp do tych ustawień można uzyskać za pomocą dowolnego narzędzia konfiguracji zewnętrznej, które wie, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jak odwoływać się do ustawień rejestru. Te ustawienia można również utworzyć lub zmodyfikować, uzyskując dostęp do wartości bezpośrednio przy użyciu Edytora rejestru systemu Windows.  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a>Wyłącz opcję przyspieszania sprzętowego  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Opcja Wyłącz przyspieszenie sprzętowe** umożliwia wyłączenie przyspieszania sprzętowego na potrzeby debugowania i testowania. Gdy widzisz artefakty renderowania w aplikacji, spróbuj wyłączyć przyspieszenie sprzętowe. Jeśli artefakt zniknie, problem może być związany z Twoim sterownikiem wideo.  
  
 **Opcja Wyłącz przyspieszenie sprzętowe** jest wartością typu DWORD równą 0 lub 1. Wartość 1 powoduje wyłączenie przyspieszania sprzętowego. Wartość 0 włącza przyspieszenie sprzętowe, pod warunkiem, że system spełnia wymagania przyspieszania sprzętowego. Aby uzyskać więcej informacji, zobacz [warstwy renderowania grafiki](../advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a>Maksymalna wartość wielopróbkowa  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maksymalna wartość** wieloprzykładowa umożliwia dostosowanie maksymalnej liczby antyaliasów zawartości 3-D. Użyj tego poziomu, aby wyłączyć Antyaliasowanie 3-D [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] w programie lub włączyć [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]je w programie.  
  
 **Maksymalna wartość** wielowartościowa to wartość DWORD, która ma zakres od 0 do 16. Wartość 0 oznacza, że antypróbkowanie antyaliasowe zawartości 3-D powinno być wyłączone, a wartość 16 podejmie próbę użycia do próbkowania wieloznacznego, jeśli jest to obsługiwane przez kartę wideo. Uważaj, że ustawienie tej wartości klucza rejestru na komputerach używających sterowników XPDM spowoduje użycie dużej ilości dodatkowej pamięci wideo, zmniejszenie wydajności renderowania trójwymiarowego i dodanie błędów renderowania i stabilności dotyczące.  
  
 Jeśli ten klucz rejestru nie jest ustawiony, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wartość domyślna to 0 dla sterowników XPDM i 4 dla sterowników WDDM.  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a>Wymagane ustawienie daty sterownika wideo  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|String|  
  
 W listopadzie 2004 firma Microsoft opublikowała nową wersję wytycznych dotyczących testowania sterowników; Sterowniki zapisywane po tej dacie oferują lepszą stabilność. Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] program użyje potoku przyspieszania sprzętowego dla tych sterowników i powróci do renderowania oprogramowania dla sterowników XPDM opublikowanych przed tą datą.  
  
 **Wymagane ustawienie daty sterownika wideo** pozwala określić alternatywną minimalną datę dla sterowników XPDM. Należy określić datę wcześniejszą niż listopad, 2004, jeśli masz pewność, że sterownik wideo jest wystarczająco stabilny do obsługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Wymagane ustawienie sterownika wideo Pobiera ciąg w następującym formacie:  
  
| |  
|-|  
|*RRRR* *MM* DD `/` `/`|  
  
 Gdzie *rrrr* to czterocyfrowy rok, *mm* to dwucyfrowy miesiąc, a *DD* to dwucyfrowy dzień. Gdy ta wartość zostanie niezmieniona [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , program używa listopada 2004 jako wymaganej daty sterownika wideo.  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a>Użyj opcji rasteryzatora odwołań  
  
|Klucz rejestru|Typ wartości|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Opcja Użyj rasteryzacji odwołania** umożliwia wymuszenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] symulowanego trybu renderowania sprzętu na potrzeby debugowania: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przechodzi do trybu sprzętowego, ale używa rasteryzatora oprogramowania referencyjnego Microsoft Direct3D, d3dref9. dll, zamiast rzeczywistego urządzenia sprzętowego.  
  
 Rasteryzacja odwołania jest bardzo niska, ale pomija sterownik wideo, aby uniknąć problemów z renderowaniem spowodowanych przez problemy ze sterownikami. Z tego powodu można użyć rasteryzatora referencyjnego, aby określić, czy problemy z renderowaniem są spowodowane przez sterownik wideo. Plik d3dref9. dll musi znajdować się w lokalizacji, w której aplikacja może uzyskać do niej dostęp, na przykład w dowolnej lokalizacji w ścieżce systemowej lub w katalogu lokalnym aplikacji.  
  
 **Opcja Użyj rasteryzacji odwołań** przyjmuje wartość typu DWORD. Wartość 0 oznacza, że Rasteryzacja odwołania nie jest używana. Wszystkie inne wartości inne niż zero wymuszają [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użycie rasteryzatora Reference.  
  
## <a name="see-also"></a>Zobacz także

- [Warstwy renderowania grafiki](../advanced/graphics-rendering-tiers.md)
- [Renderowanie grafiki WPF — przegląd](wpf-graphics-rendering-overview.md)
