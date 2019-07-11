---
title: ICorDebugILFrame::SetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af3f58fa7714b3c2b0ba387b1da650f0638dd6c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758776"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP — Metoda
Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie języka intermediate language (MSIL) firmy Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 Przesunięcie lokalizacji w kodzie MSIL.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania `SetIP` natychmiast unieważnia wszystkie ramki i łańcuchów dla bieżącego wątku. Jeśli debuger potrzebuje informacji o ramce po wywołaniu `SetIP`, należy wykonać, nowe ślad stosu.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) będzie próbował zachować ramki stosu w prawidłowym stanie. Jednak nawet jeśli ramki jest w nieprawidłowym stanie, nadal może istnieć problemy, takie jak niezainicjowanych zmiennych lokalnych. Obiekt wywołujący jest odpowiedzialny za zapewnienie spójności uruchomionego programu.  
  
 Na platformach 64-bitowy wskaźnik instrukcji nie można przenieść poza `catch` lub `finally` bloku. Jeśli `SetIP` nazywa się przejście na platformie 64-bitowej, zwróci wartość HRESULT wskazujący awarię.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
