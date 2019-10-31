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
ms.openlocfilehash: f2c881603cfa0e4b3d2dc8d1e996631b51d1e850
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134713"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject — Metoda
Pobiera wskaźnik interfejsu do domeny aplikacji środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppObject`  
 określoną Wskaźnik do adresu obiektu interfejsu ICorDebugValue, który reprezentuje domenę aplikacji CLR.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli obiekt zarządzany <xref:System.AppDomain?displayProperty=nameWithType> nie został skonstruowany dla tej domeny aplikacji, metoda zwróci `S_FALSE` i umieści `NULL` w `*ppObject`.  
  
## <a name="remarks"></a>Uwagi  
 Każda domena aplikacji w procesie może mieć zarządzany obiekt <xref:System.AppDomain?displayProperty=nameWithType> w czasie wykonywania, który go reprezentuje. Ta funkcja pobiera obiekt interfejsu ICorDebugValue, który odpowiada obiektowi zarządzanemu <xref:System.AppDomain?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
