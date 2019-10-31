---
title: ICorDebugILFrame::CanSetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: 57d83d1f301cbfd43f8f553d9aef4beb3baf95f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131083"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP — Metoda
Pobiera wartość HRESULT, która wskazuje, czy można bezpiecznie ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie języka pośredniego (MSIL) firmy Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 podczas Odpowiednie ustawienie wskaźnika instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 Przed wywołaniem metody [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) użyj metody `CanSetIP`. Jeśli `CanSetIP` zwraca wszystkie HRESULT inne niż S_OK, nadal można wywołać `ICorDebugILFrame::SetIP`, ale nie ma gwarancji, że debuger będzie kontynuował bezpieczne i prawidłowe wykonywanie debugowanego kodu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug, h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
