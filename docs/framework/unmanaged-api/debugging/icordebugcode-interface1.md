---
title: ICorDebugCode Interface1
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
ms.openlocfilehash: 37917577c802514fcebc3ea0792cbce9bb8a7345
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414082"
---
# <a name="icordebugcode-interface1"></a>ICorDebugCode Interface1
Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Tworzy punkt przerwania, od wskazanego przesunięcia.|  
|[GetAddress, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Pobiera wirtualny adres względny (RVA) segment kodu, który to `ICorDebugCode` reprezentuje.|  
|[GetCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Pobiera cały kod dla określonej funkcji, sformatowany dezasemblacji. Ta metoda jest przestarzała; Użyj [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) zamiast tego.|  
|[GetEnCRemapSequencePoints, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Nie jest zaimplementowana.|  
|[GetFunction, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|Pobiera skojarzone z tym "ICorDebugFunction" `ICorDebugCode`.|  
|[GetILToNativeMapping, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|Pobiera tablicę wystąpień "cor_debug_il_to_native_map —", które reprezentują mapowania z przesunięcia MSIL do natywnej przesunięcia.|  
|[GetSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Pobiera rozmiar w bajtach kod binarny reprezentowany przez to `ICorDebugCode`.|  
|[GetVersionNumber, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Pobiera numer jedynki, który identyfikuje wersję kodu tego `ICorDebugCode` reprezentuje.|  
|[IsIL, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Pobiera wartość wskazującą, czy to `ICorDebugCode` ma być kompilowana w MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugCode` może reprezentować MSIL lub kodu natywnego. Obiekt "ICorDebugFunction", który reprezentuje kod MSIL może mieć wartość zero lub jeden `ICorDebugCode` obiektów skojarzonych z nim. Obiekt "ICorDebugFunction", który reprezentuje kod natywny może mieć dowolną liczbę `ICorDebugCode` obiektów skojarzonych z nim.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
    
 [ICorDebugCode3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
