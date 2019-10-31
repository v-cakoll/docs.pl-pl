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
ms.openlocfilehash: 867db3325f9b18b31f66429d01ea02be3603c0f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125760"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue — Metoda
Pobiera wartość określonego pola statycznego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fieldDef`  
 podczas Token `Def` pola, który odwołuje się do pola, które ma zostać pobrane.  
  
 `pFrame`  
 podczas Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę, która ma zostać użyta do rozróżnienia między elementem statycznym, kontekstowym lub domeną aplikacji.  
  
 Jeśli pole statyczne jest powiązane z wątkiem, kontekstem lub domeną aplikacji, ramka będzie określać odpowiednią wartość.  
  
 `ppValue`  
 określoną Wskaźnik do adresu obiektu ICorDebugValue, który reprezentuje wartość pola statycznego.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku typów sparametryzowanych wartość pola statycznego jest określana względem konkretnego wystąpienia. W związku z tym, jeśli Konstruktor klasy przyjmuje parametry typu <xref:System.Type>, należy wywołać [ICorDebugType:: GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) , a nie `ICorDebugClass::GetStaticFieldValue`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
