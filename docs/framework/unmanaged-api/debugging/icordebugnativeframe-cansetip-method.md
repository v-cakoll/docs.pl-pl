---
title: ICorDebugNativeFrame::CanSetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93a8c8650822c5d986e21a456d58b2dc0327f05b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479531"
---
# <a name="icordebugnativeframecansetip-method"></a>ICorDebugNativeFrame::CanSetIP — Metoda
Pobiera wartość HRESULT, która wskazuje, czy można bezpiecznie Ustaw wskaźnik instrukcji (IP) do określonej lokalizacji przesunięcia w kodzie natywnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 [in] Odpowiednie ustawienie wskaźnik instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CanSetIP` metoda przed wywołaniem [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) metody. Jeśli `CanSetIP` zwraca wartość HRESULT żadnych innych niż S_OK, nadal mogą wywoływać `ICorDebugNativeFrame::SetIP`, ale nie ma żadnej gwarancji, że debuger będą nadal bezpiecznego i prawidłowe wykonywanie debugowany kod.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

