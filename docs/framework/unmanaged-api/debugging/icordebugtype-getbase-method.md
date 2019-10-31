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
ms.openlocfilehash: cff527aa7cde6a13667d47d030a0ef7db96ad5ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122344"
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase — Metoda
Pobiera wskaźnik interfejsu do ICorDebugType, który reprezentuje typ podstawowy, jeśli taki istnieje, typu reprezentowanego przez ten `ICorDebugType`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBase`  
 określoną Wskaźnik do adresu obiektu `ICorDebugType`, który reprezentuje typ podstawowy.  
  
## <a name="remarks"></a>Uwagi  
 Wyszukiwanie typu podstawowego dla typu jest przydatne, aby zaimplementować typowe funkcje debugera, takie jak drukowanie wszystkich pól obiektu lub jego klas nadrzędnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
