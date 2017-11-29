---
title: "ICorDebugFunction::GetNativeCode — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetNativeCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2fccfaeb346d59f5cf565f47a9a64e732706adad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode — Metoda
Pobiera kodu natywnego dla funkcji, która jest reprezentowana przez to wystąpienie ICorDebugFunction.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppCode`  
 [out] Wskaźnik do wystąpienia ICorDebugCode, który reprezentuje kodu natywnego dla tej funkcji, lub wartość null, jeśli ta funkcja jest kod języka pośredniego (MSIL) firmy Microsoft, który nie został just-in-time (JIT) skompilowany.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja reprezentowanym przez to `ICorDebugFunction` wystąpienia został skompilowany JIT więcej niż raz, jak w przypadku typów ogólnych `GetNativeCode` zwraca obiekt losowego kodu natywnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
