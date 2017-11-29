---
title: "ICorDebugAppDomain::GetObject — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetObject
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4f923d8e9bf9762d5208dd6e9be527a50a688b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject — Metoda
Pobiera wskaźnika interfejsu do typowych domeny aplikacji języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] Wskaźnik do adresu ICorDebugValue obiektu interfejsu, który reprezentuje CLR domeny aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli zarządzanego <xref:System.AppDomain?displayProperty=nameWithType> obiektu nie zostało utworzone dla tej domeny aplikacji, metoda zwraca `S_FALSE` i umieszcza `NULL` w `*ppObject`.  
  
## <a name="remarks"></a>Uwagi  
 Każda domena aplikacji w ramach procesu może mieć zarządzanego <xref:System.AppDomain?displayProperty=nameWithType> obiektu w czasie wykonywania, który reprezentuje on. Ta funkcja pobiera ICorDebugValue obiektu interfejsu, który odpowiada to zarządzany <xref:System.AppDomain?displayProperty=nameWithType> obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
