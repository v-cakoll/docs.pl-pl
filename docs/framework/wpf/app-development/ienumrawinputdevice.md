---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 04caca0c580d26fde7fc9a3e3a11b7a8fed26d65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225524"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Ten interfejs wylicza pierwotne urządzenia wejściowe i jest używana tylko przez PresentationHost.exe.  
  
> [!NOTE]
>  Ten interfejs API jest tylko przeznaczone i obsługiwane do użytku na komputerze klienckim lokalne  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|Wylicza następnego `celt` elementów (czyli RAWINPUTDEVICE struktury) na liście modułu wyliczającego, zwracając je w `rgelt` wraz z liczbą rzeczywiste elementy wyliczenia `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|Powoduje, że moduł wyliczający, aby pominąć następnego `celt` elementów w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) nie będzie zwracać tych elementów.|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|Tworzy inny moduł wyliczający pierwotne urządzenia wejściowego o ten sam stan jako bieżący modułu wyliczającego do wykonywania iteracji w tej samej listy.|  
  
## <a name="see-also"></a>Zobacz także

- [Temat nieprzetworzone dane wejściowe](/windows/desktop/inputdev/about-raw-input)
