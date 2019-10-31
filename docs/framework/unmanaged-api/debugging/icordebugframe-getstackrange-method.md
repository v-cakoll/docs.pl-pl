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
ms.openlocfilehash: 828e4dc67cb93d0a35879e94b54c9fac6e5bda16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124082"
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
 określoną Wskaźnik do `CORDB_ADDRESS`, który określa adres początkowy ramki stosu reprezentowanej przez ten obiekt `ICorDebugFrame`.  
  
 `pEnd`  
 określoną Wskaźnik do `CORDB_ADDRESS`, który określa adres końcowy ramki stosu reprezentowanej przez ten obiekt `ICorDebugFrame`.  
  
## <a name="remarks"></a>Uwagi  
 Zakres adresów stosu jest przydatny do zszywania razem z przeplotem śladów stosu zebranych z wielu aparatów debugowania. Zakres liczbowy nie zawiera żadnych informacji o zawartości ramki stosu. Jest to zrozumiałe tylko dla porównania lokalizacji ramek stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
