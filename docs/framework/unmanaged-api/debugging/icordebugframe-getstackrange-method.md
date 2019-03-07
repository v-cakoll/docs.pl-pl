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
ms.openlocfilehash: 43532888d181adcb7a7e3760f2a5e3d8f664a35c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492286"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange — Metoda
Pobiera bezwzględny zakres adresów tej ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStart`  
 [out] Wskaźnik do `CORDB_ADDRESS` , który określa adres początkowy ramki stosu, reprezentowane przez to `ICorDebugFrame` obiektu.  
  
 `pEnd`  
 [out] Wskaźnik do `CORDB_ADDRESS` , który określa adres końcowy ramki stosu, reprezentowane przez to `ICorDebugFrame` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Zakres adresów stosu jest przydatna do zszywania przeplotem śladów stosu zebranych z wielu aparaty debugowania. Zakresu liczbowego nie dostarcza żadnych informacji o zawartości ramki stosu. Jest to istotne tylko w przypadku porównywania lokalizacje ramki stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
