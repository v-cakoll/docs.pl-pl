---
title: ICorDebugClass::GetStaticFieldValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b67f5ec233679461f61715d7562b47c2a195fb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750854"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue — Metoda
Pobiera wartość określonego pola statyczne.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fieldDef`  
 [in] Pole `Def` token, który odwołuje się do pola, które mają zostać pobrane.  
  
 `pFrame`  
 [in] Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę, która ma być używany, aby rozróżniać wśród wątku, kontekstu lub statystyce domeny aplikacji.  
  
 Jeśli pola statycznego jest określana względem wątku, kontekst lub domenę aplikacji, ramki określi poprawnej wartości.  
  
 `ppValue`  
 [out] Wskaźnik na adres obiektu ICorDebugValue, która reprezentuje wartość pola statycznego.  
  
## <a name="remarks"></a>Uwagi  
 Dla typów sparametryzowanych wartość pola statycznego jest względem określonego wystąpienia. W związku z tym jeśli Konstruktor klasy ma parametry typu <xref:System.Type>, wywołaj [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) zamiast `ICorDebugClass::GetStaticFieldValue`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
