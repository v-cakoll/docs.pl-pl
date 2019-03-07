---
title: ICorDebugType2::GetTypeID Method
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54b3f8e931507e53809a2419ab7f06e63eb70c10
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497642"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2::GetTypeID Method
Pobiera [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) dla tego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 [out] Wskaźnik do [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) dla tego ICorDebugType.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu. `HRESULT` Kody obejmują następujące elementy:  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|`S_OK`|Metody powiodło się. Metoda pobierze prawidłową [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).|  
|`CORDBG_E_CLASS_NOT_LOADED`|Typ nie został załadowany.|  
|`CORDBG_E_UNSUPPORTED`|Typ nie jest obsługiwany.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia mapowanie z ICorDebugType, który reprezentuje typ, który może być lub może nie zostały załadowane w czasie wykonywania, do [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), który służy jako nieprzezroczystego obsługi, który identyfikuje typ załadowane w czasie wykonywania.  
  
 Jeśli typ, który reprezentuje ICorDebugType jeszcze nie zostały załadowane, Metoda ta zwraca `CORDBG_E_CLASS_NOT_LOADED`.  Jeśli typ nie jest obsługiwany, zwraca `CORDBG_E_UNSUPPORTED`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugType2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
