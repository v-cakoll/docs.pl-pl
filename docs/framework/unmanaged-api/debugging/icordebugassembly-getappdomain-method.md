---
title: ICorDebugAssembly::GetAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9ba09b80d7118b0ccd9b1647011a7fc7cd74e22
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485112"
---
# <a name="icordebugassemblygetappdomain-method"></a>ICorDebugAssembly::GetAppDomain — Metoda
Pobiera wskaźnik interfejsu do domeny aplikacji, która zawiera to `ICorDebugAssembly` wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppAppDomain`  
 [out] Wskaźnik na adres icordebugappdomain — interfejs, który reprezentuje domeny aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ten zestaw jest zestaw systemowy `GetAppDomain` zwraca wartość null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
