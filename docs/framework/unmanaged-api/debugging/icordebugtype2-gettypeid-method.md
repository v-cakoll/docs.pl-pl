---
title: 'ICorDebugType2:: GetTypeId — Metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
ms.openlocfilehash: 631f605fd18559b36071964e35a15761cd4c8228
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791231"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2:: GetTypeId — Metoda
Pobiera [COR_TYPEID](cor-typeid-structure.md) dla tego typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 określoną Wskaźnik do [COR_TYPEID](cor-typeid-structure.md) dla tego ICorDebugType.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Wartość zwracana jest `S_OK` w przypadku sukcesu lub niepowodzenie `HRESULT` kod w przypadku niepowodzenia. Kody `HRESULT` są następujące:  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|`S_OK`|Metoda powiodła się. Metoda pobrała prawidłowy [COR_TYPEID](cor-typeid-structure.md).|  
|`CORDBG_E_CLASS_NOT_LOADED`|Typ nie został załadowany.|  
|`CORDBG_E_UNSUPPORTED`|Typ nie jest obsługiwany.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia mapowanie od ICorDebugType, który reprezentuje typ, który może lub nie został załadowany do środowiska uruchomieniowego, do [COR_TYPEID](cor-typeid-structure.md), który służy jako uchwyt nieprzezroczysty, który identyfikuje typ załadowany do środowiska uruchomieniowego.  
  
 Gdy typ, który ICorDebugType reprezentuje, nie został jeszcze załadowany, Metoda ta zwraca `CORDBG_E_CLASS_NOT_LOADED`.  Jeśli typ nie jest obsługiwany, zwraca `CORDBG_E_UNSUPPORTED`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugType2, interfejs](icordebugtype2-interface.md)
