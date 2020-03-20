---
title: ICorDebugChain::GetStackRange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 64e697323377d664b7b1e36bbf5931a44465cc51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178959"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange — Metoda
Pobiera zakres adresów segmentu stosu dla tego łańcucha.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStart`  
 [na zewnątrz] Wskaźnik do `CORDB_ADDRESS` wartości, która jest adresem początkowym segmentu stosu.  
  
 `pEnd`  
 [na zewnątrz] Wskaźnik do `CORDB_ADDRESS` wartości, która jest adresem końcowym segmentu stosu.  
  
## <a name="remarks"></a>Uwagi  
 Zakres liczbowy ma znaczenie tylko dla porównania lokalizacji ramki stosu. Nie można wprowadzać żadnych założeń dotyczących tego, co jest faktycznie przechowywane na stosie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
