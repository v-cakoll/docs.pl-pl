---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 69bc1e973b690454bcf91487c12dc4ce0ac46a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548408"
---
# <a name="filterinputmessage"></a>FilterInputMessage
Metoda wywoływana przez PresentationHost.exe zawsze, gdy wiadomość zostanie odebrana, chyba że E_NOTIMPL jest zwracany.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMsg`  
  
 [in] WM_INPUT komunikat wysyłany do okna, które otrzymuje nieprzetworzone dane wejściowe.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 WYNIK HRESULT:  
  
 S_OK — filtr nie przetworzyć komunikatu i dalsze przetwarzanie nie może występować.  
  
 Wartości S_FALSE - przetworzyć filtru ten komunikat i nie dalsze przetwarzanie powinna się odbyć.  
  
 E_NOTIMPL — Jeśli ta wartość jest zwracana, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) nie zostanie ponownie wywołany. Może to być zwracane z aplikacji hosta, który tylko zainteresowani dostarczanie niestandardowych postęp i interfejsów użytkownika Błąd PresentationHost.exe nie jest zainteresowana przesyłane dalej komunikaty wejściowe pierwotnych z PresentationHost.exe.  
  
## <a name="remarks"></a>Uwagi  
 PresentationHost.exe jest elementem docelowym różnych raw wejściowych urządzeń, takich jak klawiatura, mysz i zdalnego sterowania. Czasami zachowania w aplikacji hosta jest zależny od danych wejściowych, które w przeciwnym razie może być zużyte przez PresentationHost.exe. Na przykład aplikacja hosta może zależeć od odbieranie komunikatów wejściowych do ustalenia, czy wyświetlać elementy interfejsu użytkownika.  
  
 Aby umożliwić aplikacji hosta do odbierania niezbędne komunikaty wejściowe zapewnienie te zachowania, PresentationHost.exe przekazuje odpowiednie komunikaty wejściowe nieprzetworzone dla aplikacji hostowanej przez wywołanie metody [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).  
  
 Hostowana aplikacja odbiera raw komunikaty wejściowe rejestrując z zestawem raw wejściowych (urządzenia człowieka interfejsu) zwrócone przez [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).  
  
## <a name="see-also"></a>Zobacz też  
 [WM_INPUT powiadomień](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
