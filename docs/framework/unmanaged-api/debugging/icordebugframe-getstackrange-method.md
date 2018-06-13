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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5da87071bc23ac17a3077049cd77f0fb8611439f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413023"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange — Metoda
Pobiera adres bezwzględny zakres tej ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStart`  
 [out] Wskaźnik do `CORDB_ADDRESS` , który określa adres początkowy ramki stosu reprezentowany przez to `ICorDebugFrame` obiektu.  
  
 `pEnd`  
 [out] Wskaźnik do `CORDB_ADDRESS` , który określa adres końcowy ramki stosu reprezentowany przez to `ICorDebugFrame` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Zakres adresów stosu jest przydatne w przypadku piecing razem śladów stosu przeplotem zebrane z wielu aparaty debugowania. Zakres liczb nie zawiera żadnych informacji o zawartości ramki stosu. Jest łatwy do rozpoznania tylko do porównania z lokalizacji ramki stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
