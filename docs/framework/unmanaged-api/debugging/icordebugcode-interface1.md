---
title: ICorDebugCode — Interfejs
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
ms.openlocfilehash: 9ca47eb5508907297a78dba1ab2b0a6d2b8ece0d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976931"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode — Interfejs

Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Tworzy punkt przerwania w określonym przesunięciu.|  
|[GetAddress, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Pobiera wirtualny adres względny (RVA) segment kodu, który to `ICorDebugCode` reprezentuje.|  
|[GetCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Pobiera cały kod dla określonej funkcji, sformatowane, aby dezasemblacji. Ta metoda jest przestarzała; Użyj [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) zamiast tego.|  
|[GetEnCRemapSequencePoints, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Nie zaimplementowano.|  
|[GetFunction, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|Pobiera skojarzony z tym "ICorDebugFunction" `ICorDebugCode`.|  
|[GetILToNativeMapping, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|Pobiera tablicę wystąpień "cor_debug_il_to_native_map —", które reprezentują mapowania z MSIL przesunięć natywnych przesunięć.|  
|[GetSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Pobiera rozmiar w bajtach, reprezentowane przez ten kod binarny `ICorDebugCode`.|  
|[GetVersionNumber, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Pobiera liczbę liczonego od jednego, który identyfikuje wersję kodu że `ICorDebugCode` reprezentuje.|  
|[IsIL, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Pobiera wartość wskazującą, czy to `ICorDebugCode` jest skompilowany w MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugCode` może reprezentować MSIL lub kodu natywnego. Obiekt "ICorDebugFunction", który reprezentuje kod MSIL może mieć zero lub jeden `ICorDebugCode` obiektów skojarzonych z nim. Obiekt "ICorDebugFunction", który reprezentuje kod natywny może mieć dowolną liczbę `ICorDebugCode` obiektów skojarzonych z nim.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugCode3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
