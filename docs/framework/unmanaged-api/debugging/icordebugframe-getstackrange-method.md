---
title: ICorDebugFrame::GetStackRange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 7a35ce025360e0ec8b7085d68e54548026b7c7fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178910"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange — Metoda
Pobiera bezwzględny zakres adresów tej ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStart`  
 [na zewnątrz] Wskaźnik do, `CORDB_ADDRESS` który określa adres początkowy ramki stosu `ICorDebugFrame` reprezentowanej przez ten obiekt.  
  
 `pEnd`  
 [na zewnątrz] Wskaźnik do, `CORDB_ADDRESS` który określa adres końcowy ramki stosu `ICorDebugFrame` reprezentowanej przez ten obiekt.  
  
## <a name="remarks"></a>Uwagi  
 Zakres adresów stosu jest przydatne do piecing razem przeplotem ślady stosu zebrane z wielu aparatów debugowania. Zakres liczbowy nie zawiera żadnych informacji o zawartości ramki stosu. Ma znaczenie tylko dla porównania lokalizacji ramki stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
