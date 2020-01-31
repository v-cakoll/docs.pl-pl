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
ms.openlocfilehash: 8632799b68ae8f92835d1774472bc1432d886f3b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793481"
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
 `CreateValueForType` generalizes [:: SetValue](icordebugeval-createvalue-method.md) , umożliwiając określenie dowolnego typu obiektu, w tym typów skonstruowanych, takich jak `List<int>`. Jedynym celem tej metody jest wygenerowanie wartości, która może zostać przeniesiona do oceny funkcji.  
  
 Typ musi być klasą lub typem wartości. Nie można użyć tej metody do tworzenia wartości tablicy lub wartości ciągu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
