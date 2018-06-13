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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad1ea4da252fe9fac89faa79195b6a6de245ad9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414703"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP — Metoda
Pobiera wartość HRESULT, która wskazuje, czy jest bezpieczne, można ustawić wskaźnika instrukcji w określonej lokalizacji przesunięcia w kodzie Microsoft języka pośredniego (MSIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nOffset`  
 [in] Odpowiednie ustawienie wskaźnik instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CanSetIP` metoda przed wywołaniem [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) metody. Jeśli `CanSetIP` zwraca HRESULT żadnych innych niż S_OK, nadal mogą wywoływać `ICorDebugILFrame::SetIP`, ale nie ma żadnej gwarancji, że debuger będzie bezpieczne i prawidłowe wykonywanie kodu debugowany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug, h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
