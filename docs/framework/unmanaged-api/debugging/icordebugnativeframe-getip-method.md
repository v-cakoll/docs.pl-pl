---
title: ICorDebugNativeFrame::GetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a27a50e6fb120e537d28759a79a2b90c6d437e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600456"
---
# <a name="icordebugnativeframegetip-method"></a>ICorDebugNativeFrame::GetIP — Metoda
Pobiera kodu macierzystego przesunięcia lokalizacji, do której jest aktualnie ustawiona wskaźnik instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pnOffset`  
 [out] Wskaźnik do przesunięcia lokalizacji w kodzie natywnym.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ramka stosu, który jest reprezentowany przez ten icordebugnativeframe "—" jest aktywna, przesunięcie jest adres następnej instrukcji do wykonania. Jeśli tej ramki stosu nie jest aktywny, przesunięcie jest adres następnej instrukcji do wykonania podczas ponownego uaktywniania ramki stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

