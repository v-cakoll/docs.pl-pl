---
title: ICorDebugType::GetBase — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b96c6ab8fb9065e1a08ad45a7f4482ef0b32788b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418888"
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase — Metoda
Pobiera wskaźnika interfejsu do ICorDebugType, który reprezentuje typ podstawowy, jeśli istnieje, typu reprezentowanego przez ten `ICorDebugType`.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBase`  
 [out] Wskaźnik do adresu `ICorDebugType` obiekt, który reprezentuje typ podstawowy.  
  
## <a name="remarks"></a>Uwagi  
 Wyszukiwanie typu podstawowego dla typu jest przydatne do zaimplementowania typowych funkcji debugera, takie jak drukowanie wszystkie pola obiektu lub jej klas nadrzędnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
