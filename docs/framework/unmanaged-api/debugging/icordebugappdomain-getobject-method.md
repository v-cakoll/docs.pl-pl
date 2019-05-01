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
ms.openlocfilehash: 0ca9792df69f859e20f1d9e40754d1cec138945d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785115"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject — Metoda
Pobiera wskaźnik interfejsu do typowych domeny aplikacji języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
