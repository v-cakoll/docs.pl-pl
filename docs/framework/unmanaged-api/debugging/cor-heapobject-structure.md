---
title: COR_HEAPOBJECT — Struktura
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179337"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT — Struktura
Zawiera informacje o obiekcie na zarządzanym stosie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`address`|Adres obiektu w pamięci.|  
|`size`|Całkowity rozmiar obiektu w bajtach.|  
|`type`|Token [COR_TYPEID](cor-typeid-structure.md) reprezentujący typ obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_HEAPOBJECT`instancje można pobrać, wyliczając obiekt interfejsu [ICorDebugHeapEnum,](icordebugheapenum-interface.md) który jest wypełniany przez [wywołanie metody ICorDebugProcess5::EnumerateHeap.](icordebugprocess5-enumerateheap-method.md)  
  
 Wystąpienie `COR_HEAPOBJECT` zawiera informacje o obiektie na żywo na zarządzanym stercie lub o obiekcie, który nie jest zakorzeniony przez żaden obiekt, ale nie został jeszcze zebrany przez moduł zbierający elementy bezużyteczne.  
  
 Aby uzyskać lepszą `COR_HEAPOBJECT.address` wydajność, `CORDB_ADDRESS` pole jest wartością, a nie wartością interfejsu ICorDebugValue używaną w większości interfejsu API debugowania. Aby uzyskać ICorDebugValue obiektu dla danego adresu obiektu, można przekazać `CORDB_ADDRESS` wartość do [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) metody.  
  
 Aby uzyskać lepszą `COR_HEAPOBJECT.type` wydajność, `COR_TYPEID` pole jest wartością, a nie wartością interfejsu ICorDebugType używaną w większości interfejsu API debugowania. Aby uzyskać obiekt ICorDebugType dla danego identyfikatora typu, można przekazać `COR_TYPEID` wartość do metody [ICorDebugProcess5::GetTypeForTypeID.](icordebugprocess5-gettypefortypeid-method.md)  
  
 Struktura `COR_HEAPOBJECT` zawiera interfejs COM z liczonych odwołaniemi. Jeśli pobierasz `COR_HEAPOBJECT` wystąpienie z wyliczacza, wywołując [metodę ICorDebugHeapEnum::Next,](icordebugheapenum-next-method.md) należy następnie zwolnić odwołanie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury debugowania](debugging-structures.md)
- [Debugging](index.md)
