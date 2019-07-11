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
ms.openlocfilehash: c24d6e9c42a091eafbe6d4bdee2bb4e055fd8852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772034"
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
 [out] Wskaźnik na adres `ICorDebugType` obiekt, który reprezentuje typ podstawowy.  
  
## <a name="remarks"></a>Uwagi  
 Wyszukiwanie z typem podstawowym typem jest przydatne do zaimplementowania typowych funkcji debugowania, takich jak drukowanie wszystkich pól obiektu lub jej klas nadrzędnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
