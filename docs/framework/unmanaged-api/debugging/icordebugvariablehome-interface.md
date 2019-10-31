---
title: ICorDebugVariableHome, interfejs
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: 306a07450b8ae6d29875ca0cc4679390472e4d1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121046"
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome, interfejs
Reprezentuje zmienną lokalną lub argument funkcji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetArgumentIndex, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|Pobiera indeks argumentu funkcji.|  
|[GetCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|Pobiera wystąpienie "ICorDebugCode", które zawiera ten obiekt `ICorDebugVariableHome`.|  
|[GetLiveRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|Pobiera natywny zakres, w którym znajduje się ta zmienna.|  
|[GetLocationType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|Pobiera typ lokalizacji natywnej zmiennej.|  
|[GetOffset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|Pobiera przesunięcie z rejestru podstawowego dla zmiennej.|  
|[GetRegister, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|Pobiera rejestr zawierający zmienną z typem lokalizacji `VLT_REGISTER`i podstawową rejestracją dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.|  
|[GetSlotIndex, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|Pobiera zarządzany indeks szczeliny zmiennej lokalnej.|  
  
## <a name="example"></a>Przykład  
 Poniższy fragment kodu używa obiektu [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) o nazwie `pCode4`.  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugVariableHomeEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
