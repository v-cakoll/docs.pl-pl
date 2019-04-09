---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: bd696752a287a78533d55c0fd3ad9986a32bd180
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111322"
---
# <a name="filterinputmessage"></a>FilterInputMessage
Metoda wywoływana przez PresentationHost.exe zawsze wtedy, gdy wiadomość zostaje odebrana, chyba że E_NOTIMPL jest zwracana.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
## <a name="parameters"></a>Parametry  
 `pMsg`  
  
 [in] Komunikat WM_INPUT wysyłane do okna, które otrzymuje nieprzetworzone dane wejściowe.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 HRESULT:  
  
 S_OK — filtr nie przetworzył komunikat i dalszego przetwarzania mogą wystąpić.  
  
 S_FALSE — filtr przetworzyć ten komunikat i nie dalszego przetwarzania powinny być wykonywane.  
  
 E_NOTIMPL — Jeśli ta wartość jest zwracana, [filterinputmessage —](filterinputmessage.md) nie zostanie ponownie wywołana. To może być zwracane z aplikacji hosta, która jest tylko zainteresowana dostarczanie postępu niestandardowych i interfejsy użytkownika Błąd PresentationHost.exe nie jest zainteresowany przesyłane dalej nieprzetworzone komunikaty wejściowe z PresentationHost.exe.  
  
## <a name="remarks"></a>Uwagi  
 PresentationHost.exe jest celem różnych nieprzetworzonych danych wejściowych urządzeń, w tym klawiatury, myszy i zdalnego sterowania. Czasami zachowania w aplikacji hosta jest zależny od danych wejściowych, które w przeciwnym razie może być zużyte przez PresentationHost.exe. Na przykład aplikacja hosta może zależeć odbierania niektórych komunikatów wejściowych, aby określić, czy należy wyświetlać elementy interfejsu użytkownika.  
  
 Aby umożliwić aplikacji hosta otrzymywać niezbędne komunikaty wejściowe, aby zapewnić następujące zachowania, PresentationHost.exe przekazuje odpowiednie nieprzetworzone komunikaty wejściowe do aplikacji hostowanej przez wywołanie metody [filterinputmessage —](filterinputmessage.md).  
  
 Hostowana aplikacja odbiera nieprzetworzone komunikaty wejściowe przez zarejestrowanie kodowań z zestawem nieprzetworzonych danych wejściowych (urządzenia ludzi interfejsu) zwracane przez [getrawinputdevices —](getrawinputdevices.md).  
  
## <a name="see-also"></a>Zobacz także

- [Komunikat WM_INPUT](/windows/desktop/inputdev/wm-input)
