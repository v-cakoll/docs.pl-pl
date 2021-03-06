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
ms.openlocfilehash: caf6a24207be98be9afb10be2bd027b51405fa3b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396538"
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome, interfejs
Reprezentuje zmienną lokalną lub argument funkcji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetArgumentIndex, metoda](icordebugvariablehome-getargumentindex-method.md)|Pobiera indeks argumentu funkcji.|  
|[GetCode, metoda](icordebugvariablehome-getcode-method.md)|Pobiera wystąpienie "ICorDebugCode", które zawiera ten `ICorDebugVariableHome` obiekt.|  
|[GetLiveRange, metoda](icordebugvariablehome-getliverange-method.md)|Pobiera natywny zakres, w którym znajduje się ta zmienna.|  
|[GetLocationType, metoda](icordebugvariablehome-getlocationtype-method.md)|Pobiera typ lokalizacji natywnej zmiennej.|  
|[GetOffset — Metoda](icordebugvariablehome-getoffset-method.md)|Pobiera przesunięcie z rejestru podstawowego dla zmiennej.|  
|[GetRegister, metoda](icordebugvariablehome-getregister-method.md)|Pobiera rejestr zawierający zmienną z typem lokalizacji `VLT_REGISTER` i rejestr podstawowy dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE` .|  
|[GetSlotIndex, metoda](icordebugvariablehome-getslotindex-method.md)|Pobiera zarządzany indeks szczeliny zmiennej lokalnej.|  
  
## <a name="example"></a>Przykład  
 Poniższy fragment kodu używa obiektu [ICorDebugCode4](icordebugcode4-interface.md) o nazwie `pCode4` .  
  
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
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [ICorDebugVariableHomeEnum, interfejs](icordebugvariablehomeenum-interface.md)
