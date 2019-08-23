---
title: ICorDebugCode, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75cc8ea9d88dda42362f50b519864b1a78e1a64b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960792"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode, interfejs

Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Tworzy punkt przerwania w określonym przesunięciu.|  
|[GetAddress, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Pobiera względny adres wirtualny (RVA) segmentu kodu, który `ICorDebugCode` reprezentuje.|  
|[GetCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Pobiera cały kod dla określonej funkcji, sformatowany pod kątem demontażu. Ta metoda jest przestarzała; Zamiast tego użyj [ICorDebugCode2:: GetCodeChunks —](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) .|  
|[GetEnCRemapSequencePoints, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Nie zaimplementowane.|  
|[GetFunction, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|Pobiera wartość "ICorDebugFunction" skojarzoną z `ICorDebugCode`tym elementem.|  
|[GetILToNativeMapping, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|Pobiera tablicę wystąpień "COR_DEBUG_IL_TO_NATIVE_MAP", które reprezentują mapowania z przesunięć MSIL do natywnych przesunięć.|  
|[GetSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Pobiera rozmiar (w bajtach) kodu binarnego reprezentowanego przez ten `ICorDebugCode`element.|  
|[GetVersionNumber, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Pobiera jednostronicowy numer identyfikujący wersję kodu, który `ICorDebugCode` reprezentuje.|  
|[IsIL, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Pobiera wartość wskazującą, czy jest ona `ICorDebugCode` kompilowana w MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugCode`może reprezentować kod MSIL lub natywny. Obiekt "ICorDebugFunction", który reprezentuje kod MSIL, może mieć skojarzone z nim `ICorDebugCode` zero lub jeden obiekt. Obiekt "ICorDebugFunction" reprezentujący kod natywny może zawierać dowolną liczbę `ICorDebugCode` obiektów skojarzonych z nim.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugCode3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
