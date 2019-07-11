---
title: ICorDebugAppDomain::GetObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1201ac0dca9cbd48c24b2621eba079ae672fd310
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737846"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject — Metoda
Pobiera wskaźnik interfejsu do typowych domeny aplikacji języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] Wskaźnik na adres obiektu interfejsu ICorDebugValue, który reprezentuje domenę aplikacji CLR.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli jest to zarządzana <xref:System.AppDomain?displayProperty=nameWithType> obiekt nie został skonstruowany dla tej domeny aplikacji, Metoda ta zwraca `S_FALSE` i umieszcza `NULL` w `*ppObject`.  
  
## <a name="remarks"></a>Uwagi  
 Każda domena aplikacji, w ramach procesu może być zarządzany <xref:System.AppDomain?displayProperty=nameWithType> obiektu w czasie wykonywania, który go reprezentuje. Ta funkcja pobiera obiekt interfejsu ICorDebugValue, który odpowiada to zarządzane <xref:System.AppDomain?displayProperty=nameWithType> obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
