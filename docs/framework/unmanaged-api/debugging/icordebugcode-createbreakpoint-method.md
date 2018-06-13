---
title: ICorDebugCode::CreateBreakpoint — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1173091a5f2d8814747c93f827150afe39b8b309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399124"
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint — Metoda
Tworzy punkt przerwania w tym segmencie kodu od wskazanego przesunięcia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `offset`  
 [in] Przesunięcie, w którym chcesz utworzyć punkt przerwania.  
  
 `ppBreakpoint`  
 [out] Wskaźnik do obiektu "ICorDebugFunctionBreakpoint", który reprezentuje punkt przerwania adresu.  
  
## <a name="remarks"></a>Uwagi  
 Aby punkt przerwania jest aktywna, można dodać go do obiektu procesu.  
  
 Jeśli ten kod jest kod języka pośredniego (MSIL) firmy Microsoft, a istnieje just-in-time (JIT)-skompilowanych wersji natywnego kodu punkt przerwania zostaną zastosowane w również JIT skompilowanego kodu. (Taki sam jest wartość true, jeśli kod jest kompilacji JIT później).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
