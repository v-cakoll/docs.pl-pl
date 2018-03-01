---
title: GetRawInputDevices
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5229eb7e72b63f3e44f67dc750d49acbf44410da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
Umożliwia PresentationHost.exe w celu odnalezienia urządzeń wejściowych raw (człowieka interfejsu urządzenia), które jest zainteresowana aplikacji hosta.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
  
 [out] Wskaźnik do [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) wyliczania raw urządzenia wejściowego.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 WYNIK HRESULT:  
  
 S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) tylko będą używane przez PresentationHost.exe, jeśli jest zwracana wartość S_OK.  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Uwagi  
 Nieprzetworzone urządzenia wejściowe są zbiór urządzeń wejściowych obejmuje klawiatury, myszy i mniej tradycyjnych urządzeniami, takimi jak zdalnego sterowania.  
  
 Po pobraniu listy urządzeń wejściowych raw PresentationHost.exe rejestruje urządzenia odbierają powiadomienia WM_INPUT.  
  
## <a name="see-also"></a>Zobacz też  
 [http://msdn.microsoft.com/library/default.asp?URL=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
