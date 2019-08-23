---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 5249d7ea359db5d5c58ae87600f61048b465b4c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964764"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Ten interfejs wylicza pierwotne urządzenia wejściowe i jest używany tylko przez PresentationHost. exe.  
  
> [!NOTE]
> Ten interfejs API jest przeznaczony tylko do użytku i jest obsługiwany na lokalnym komputerze klienckim  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|Wylicza następne `celt` elementy (czyli struktury RAWINPUTDEVICE) na liście modułu wyliczającego, zwracając `rgelt` je wraz z rzeczywistą liczbą wyliczeniowych elementów w `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|Instruuje moduł wyliczający, aby pominąć `celt` kolejne elementy w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) nie zwróci tych elementów.|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|Resetuje sekwencję wyliczenia na początek.|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|Tworzy inny nieprzetworzony moduł wyliczający urządzenia wejściowe z tym samym stanem co bieżący moduł wyliczający, aby wykonać iterację na tej samej liście.|  
  
## <a name="see-also"></a>Zobacz także

- [Informacje o nieprzetworzonym wejściu](/windows/desktop/inputdev/about-raw-input)
