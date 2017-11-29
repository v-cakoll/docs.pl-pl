---
title: IEnumRAWINPUTDEVICE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f9ebd0aee5041ef8a8a7cc44261fa69e3da1fa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Ten interfejs wylicza raw urządzenia wejściowe i jest używana tylko przez PresentationHost.exe.  
  
> [!NOTE]
>  Ten interfejs API jest tylko przeznaczone i obsługiwana na maszynie lokalnej klienta  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|Wylicza następnej `celt` elementy (to znaczy RAWINPUTDEVICE struktury) na liście modułu wyliczającego, zwracając je w `rgelt` wraz z rzeczywistą liczbę elementów wyliczane w `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|Powoduje, że moduł wyliczający, aby przejść dalej `celt` elementów w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) nie zwróci tych elementów.|  
|[IEnumRAWINPUTDEVIC:Reset](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[IEnumRAWINPUTDEVIC:Clone](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|Tworzy inny moduł wyliczający raw urządzenia wejściowego z takim samym stanie, aby jako bieżącego modułu wyliczającego, aby przejść przez tę samą listę.|  
  
## <a name="see-also"></a>Zobacz też  
 [O nieprzetworzone dane wejściowe](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/aboutrawinput.asp)
