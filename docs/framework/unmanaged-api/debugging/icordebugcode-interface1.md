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
ms.openlocfilehash: 4b24b3dfe6a931866acd7eba966811071ff39ea5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788928"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode, interfejs

Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](icordebugcode-createbreakpoint-method.md)|Tworzy punkt przerwania w określonym przesunięciu.|  
|[GetAddress, metoda](icordebugcode-getaddress-method.md)|Pobiera względny adres wirtualny (RVA) segmentu kodu, który reprezentuje ten `ICorDebugCode`.|  
|[GetCode, metoda](icordebugcode-getcode-method.md)|Pobiera cały kod dla określonej funkcji, sformatowany pod kątem demontażu. Ta metoda jest przestarzała; Zamiast tego użyj [ICorDebugCode2:: GetCodeChunks —](icordebugcode2-getcodechunks-method.md) .|  
|[GetEnCRemapSequencePoints, metoda](icordebugcode-getencremapsequencepoints-method.md)|Nie zaimplementowane.|  
|[GetFunction, metoda](icordebugcode-getfunction-method.md)|Pobiera wartość "ICorDebugFunction" skojarzoną z tym `ICorDebugCode`.|  
|[GetILToNativeMapping, metoda](icordebugcode-getiltonativemapping-method.md)|Pobiera tablicę wystąpień "COR_DEBUG_IL_TO_NATIVE_MAP", które reprezentują mapowania z przesunięć MSIL do natywnych przesunięć.|  
|[GetSize, metoda](icordebugcode-getsize-method.md)|Pobiera rozmiar (w bajtach) kodu binarnego reprezentowanego przez ten `ICorDebugCode`.|  
|[GetVersionNumber, metoda](icordebugcode-getversionnumber-method.md)|Pobiera jednostronicowy numer identyfikujący wersję kodu, który reprezentuje ten `ICorDebugCode`.|  
|[IsIL, metoda](icordebugcode-isil-method.md)|Pobiera wartość wskazującą, czy ten `ICorDebugCode` jest kompilowany w języku MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugCode` może reprezentować kod MSIL lub natywny. Obiekt "ICorDebugFunction", który reprezentuje kod MSIL, może mieć skojarzone z nim zero lub jeden `ICorDebugCode` obiektów. Obiekt "ICorDebugFunction" reprezentujący kod natywny może zawierać dowolną liczbę obiektów `ICorDebugCode` skojarzonych z nim.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugCode3, interfejs](icordebugcode3-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
