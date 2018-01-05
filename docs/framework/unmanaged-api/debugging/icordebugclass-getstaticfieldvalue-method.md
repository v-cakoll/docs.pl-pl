---
title: "ICorDebugClass::GetStaticFieldValue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass.GetStaticFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21176eb73b3655fe8bd4b2187b6da49a3c31bd82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue — Metoda
Pobiera wartość określonego pola statycznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fieldDef`  
 [in] Pole `Def` token, który odwołuje się do pola, które mają zostać pobrane.  
  
 `pFrame`  
 [in] Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę służący do odróżniania między wątku, kontekstu lub statystyce domeny aplikacji.  
  
 W przypadku pola statycznego względem wątku, kontekst lub domeny aplikacji, ramki określi poprawnej wartości.  
  
 `ppValue`  
 [out] Wskaźnik do adres obiektu ICorDebugValue reprezentujący wartość pola statycznego.  
  
## <a name="remarks"></a>Uwagi  
 Dla typów sparametryzowane wartość pola statycznego jest określana względem konkretnego wystąpienia. W związku z tym jeśli Konstruktor klasy pobiera parametry typu <xref:System.Type>, wywołaj [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) zamiast `ICorDebugClass::GetStaticFieldValue`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
