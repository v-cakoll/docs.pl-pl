---
title: ICorDebugEval2::CreateValueForType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 20315dfc426b63f2d526f3481756e165b388b41e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137608"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType — Metoda
Pobiera wskaźnik do nowego ICorDebugValue określonego typu z początkową wartością zero lub null.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pType`  
 podczas Wskaźnik do obiektu ICorDebugType, który reprezentuje typ.  
  
 `ppValue`  
 określoną Wskaźnik na adres `ICorDebugValue` obiektu, który reprezentuje wartość.  
  
## <a name="remarks"></a>Uwagi  
 `CreateValueForType` generalizes [:: SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) , umożliwiając określenie dowolnego typu obiektu, w tym typów skonstruowanych, takich jak `List<int>`. Jedynym celem tej metody jest wygenerowanie wartości, która może zostać przeniesiona do oceny funkcji.  
  
 Typ musi być klasą lub typem wartości. Nie można użyć tej metody do tworzenia wartości tablicy lub wartości ciągu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
