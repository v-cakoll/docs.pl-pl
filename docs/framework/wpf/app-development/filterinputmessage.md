---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 1453946766e33843ae9e56f7a7f4dbf1678b81b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991385"
---
# <a name="filterinputmessage"></a>FilterInputMessage
Wywoływana przez PresentationHost. exe za każdym razem, gdy wiadomość zostanie odebrana, chyba że zostanie zwrócona wartość E_NOTIMPL.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
## <a name="parameters"></a>Parametry  
 `pMsg`  
  
 podczas Wiadomość WM_INPUT wysłana do okna, które pobiera nieprzetworzone dane wejściowe.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 WYNIK  
  
 S_OK — filtr nie przetworzył komunikatu i może wystąpić dalsze przetwarzanie.  
  
 S_FALSE — filtr przetworzył ten komunikat i nie powinno wystąpić dalsze przetwarzanie.  
  
 E_NOTIMPL — w przypadku zwrócenia wartości [FilterInputMessage](filterinputmessage.md) nie jest ponownie wywoływana. Może to zostać zwrócone z aplikacji hosta, która jest interesująca tylko w celu udostępnienia niestandardowego postępu i błędów interfejsów użytkownika do PresentationHost. exe nie interesuje przekazanie pierwotnych komunikatów wejściowych z PresentationHost. exe.  
  
## <a name="remarks"></a>Uwagi  
 PresentationHost. exe jest elementem docelowym różnych nieprzetworzonych urządzeń wejściowych, w tym klawiatury, myszy i pilotów. Czasami zachowanie w aplikacji hosta jest zależne od danych wejściowych, które w przeciwnym razie byłyby używane przez PresentationHost. exe. Na przykład aplikacja hosta może zależeć od otrzymywania pewnych komunikatów wejściowych, aby określić, czy mają być wyświetlane konkretne elementy interfejsu użytkownika.  
  
 Aby umożliwić aplikacji hosta otrzymywanie niezbędnych komunikatów wejściowych w celu zapewnienia tych zachowań, PresentationHost. exe przekazuje odpowiednie nieprzetworzone komunikaty wejściowe do hostowanej aplikacji przez wywołanie [FilterInputMessage](filterinputmessage.md).  
  
 Hostowana aplikacja odbiera nieprzetworzone komunikaty wejściowe przez zarejestrowanie się w zestawie nieprzetworzonych urządzeń wejściowych (urządzenia interfejsu ludzkiego) zwracanych przez [GetRawInputDevices](getrawinputdevices.md).  
  
## <a name="see-also"></a>Zobacz także

- [WM_INPUT komunikat](/windows/desktop/inputdev/wm-input)
