---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 86910434e572bc19595d1664347f35d7a39eb75b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365107"
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
Umożliwia PresentationHost.exe odnajdywania nieprzetworzonych danych wejściowych (urządzenia ludzi interfejs), które jest zainteresowany aplikacji hosta.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
  
 [out] Wskaźnik do [ienumrawinputdevice —](ienumrawinputdevice.md) wyliczania urządzeniach niesformatowanych danych wejściowych.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 HRESULT:  
  
 S_OK - [ienumrawinputdevice —](ienumrawinputdevice.md) tylko będą używane przez PresentationHost.exe, jeśli zostanie zwrócony S_OK.  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Uwagi  
 Urządzeniach niesformatowanych danych wejściowych to zbiór urządzeń, danych wejściowych, obejmującą klawiatur, myszy i mniej tradycyjnych urządzenia, na przykład zdalnego sterowania.  
  
 Po pobraniu listy urządzeniach niesformatowanych danych wejściowych PresentationHost.exe rejestruje się za pomocą urządzeń mają otrzymywać powiadomienia WM_INPUT.  
  
## <a name="see-also"></a>Zobacz także
- [GetRawInputDeviceList](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [FilterInputMessage](filterinputmessage.md)
