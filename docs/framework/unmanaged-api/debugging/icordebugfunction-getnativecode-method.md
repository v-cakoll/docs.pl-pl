---
title: ICorDebugFunction::GetNativeCode — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0507d59011f6b584ecb1ae11c35c456c80793af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754596"
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode — Metoda
Pobiera kodu natywnego dla funkcji, która jest reprezentowana przez to wystąpienie ICorDebugFunction.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppCode`  
 [out] Wskaźnik do wystąpienia ICorDebugCode, który reprezentuje kodu natywnego dla funkcji lub wartość null, jeśli ta funkcja jest kod intermediate language (MSIL) firmy Microsoft, który nie został just-in-time (JIT) skompilowany.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja, która jest reprezentowana przez to `ICorDebugFunction` wystąpienie zostało kompilowanego dokładnie na czas więcej niż raz, jak w przypadku typów ogólnych `GetNativeCode` zwraca obiekt losowy kodu natywnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
