---
title: ICorDebugNativeFrame::SetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 604486a074c3dbe3d19b741df28499ee03e1b2e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193281"
---
# <a name="icordebugnativeframesetip-method"></a>ICorDebugNativeFrame::SetIP — Metoda
Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie natywnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 [in] Przesunięcie lokalizacji w kodzie natywnym.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania `SetIP` natychmiast unieważnia wszystkie ramki i łańcuchów dla bieżącego wątku. Jeśli debuger potrzebuje informacji o ramce po wywołaniu `SetIP`, należy wykonać, nowe ślad stosu.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) będzie próbował zachować ramki stosu w prawidłowym stanie. Jednak nawet jeśli ramki jest w nieprawidłowym stanie chodzi środowiska uruchomieniowego jest, nadal może być problemy, takie jak niezainicjowanych zmiennych lokalnych i tak dalej. Obiekt wywołujący jest odpowiedzialny za spójność uruchomionego programu.  
  
 Na platformach 64-bitowy wskaźnik instrukcji nie można przenieść poza `catch` lub `finally` bloku. Jeśli `SetIP` nazywa się przejście na platformie 64-bitowej, zwróci wartość HRESULT wskazujący awarię.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
