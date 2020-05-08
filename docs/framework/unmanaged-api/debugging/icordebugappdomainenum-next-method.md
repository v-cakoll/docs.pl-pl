---
title: ICorDebugAppDomainEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
ms.openlocfilehash: 17bf4c92b1e1347a8fe790c8df5937de0f95df4d
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895082"
---
# <a name="icordebugappdomainenumnext-method"></a>ICorDebugAppDomainEnum::Next — Metoda
Pobiera określoną liczbę domen aplikacji z kolekcji, rozpoczynając od bieżącego położenia kursora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba domen aplikacji do pobrania.  
  
 `values`  
 określoną Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugAppDomain, który reprezentuje domenę aplikacji.  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby domen aplikacji faktycznie zwróconych. Ta wartość może być równa `celt` null, jeśli jest taka.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
