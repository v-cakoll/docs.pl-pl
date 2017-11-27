---
title: "ICorDebugEval2::CreateValueForType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.CreateValueForType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc2760b1c303141372aed824bda71ebdae8ffe0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType — Metoda
Pobiera wskaźnik do nowego ICorDebugValue określonego typu o wartości początkowej zero lub wartość null.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pType`  
 [in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ.  
  
 `ppValue`  
 [out] Wskaźnik do adresu `ICorDebugValue` obiekt, który reprezentuje wartość.  
  
## <a name="remarks"></a>Uwagi  
 `CreateValueForType`stanowi uogólnienie [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) , umożliwiając określenie typu dowolnego obiektu, w tym konstruować typów takich jak `List<int>`. Jedynym celem tej metody polega na generowaniu wartości, które mogą zostać przekazane do obliczania funkcji.  
  
 Typ musi być klasą lub typem wartości. Tej metody nie można użyć do utworzenia tablicy wartości lub wartości ciągu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
