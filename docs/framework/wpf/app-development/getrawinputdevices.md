---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 4fc7a5021f9f8d9e6badcd3e13266fb8f4bfe7a4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991746"
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
Zezwala programowi PresentationHost. exe na odnajdywanie nieprzetworzonych urządzeń wejściowych (urządzeń z interfejsem ludzkim), których aplikacja hosta interesuje.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
  
 określoną Wskaźnik do [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) do wyliczania nieprzetworzonych urządzeń wejściowych.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 WYNIK  
  
 S_OK- [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) będzie używana tylko przez PresentationHost. exe, jeśli zostanie zwrócony S_OK.  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Uwagi  
 Pierwotne urządzenia wejściowe to zbiór urządzeń wejściowych, które obejmują klawiatury, myszy i mniejsze tradycyjne urządzenia, takie jak zdalne sterowanie.  
  
 Po pobraniu listy nieprzetworzonych urządzeń wejściowych PresentationHost. exe rejestruje je na urządzeniach do odbierania komunikatów powiadomień WM_INPUT.  
  
## <a name="see-also"></a>Zobacz także

- [GetRawInputDeviceList](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [FilterInputMessage](filterinputmessage.md)
