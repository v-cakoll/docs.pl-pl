---
title: Metoda ICorDebugILFrame4::GetCodeEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: edaea49d95eeb9856b949f118f16aa49e528f7ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421037"
---
# <a name="icordebugilframe4getcodeex-method"></a>Metoda ICorDebugILFrame4::GetCodeEx
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wskaźnik do kodu, który jest wykonywany tej ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 [in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) element członkowski wyliczenia, która określa, czy język pośredni (IL), zdefiniowany przez profiler ReJIT żądanie znajduje się w ramce.  
  
 `ppCode`  
 [out] Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje kod, który jest wykonywany tej ramki stosu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) metody, z wyjątkiem, że opcjonalnie dostęp do kodu określonego przez profiler ReJIT żądanie. Wywołanie tej metody za pomocą `flags` wartość `ILCODE_ORIGINAL_IL` jest odpowiednikiem wywołania [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); w wypadku metody został zinstrumentowany, jego IL nie będą dostępne. `ILCODE_REJIT_IL` Umożliwia debugera IL zdefiniowany przez profiler ReJIT żądanie dostępu do. Jeśli nie ma instrumentacji IL, `ppCode` jest **null**, a metoda zwraca `S_OK`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugILFrame4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Przewodnik](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
