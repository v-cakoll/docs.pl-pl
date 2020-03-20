---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179064"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda
Pobiera moduł wyliczacza dla buforowanych typów środowiska wykonawczego systemu Windows w domenie aplikacji na podstawie ich identyfikatorów interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cReqTypes`  
 [w] Liczba wymaganych typów.  
  
 `iidsToResolve`  
 [w] Wskaźnik do tablicy zawierającej identyfikatory interfejsu odpowiadające zarządzanym reprezentacjom typów środowiska wykonawczego systemu Windows do pobrania.  
  
 `ppTypesEnum`  
 [na zewnątrz] Wskaźnik do adresu obiektu interfejsu "ICorDebugTypeEnum", który umożliwia wyliczanie buforowanych zarządzanych reprezentacji pobranych typów środowiska wykonawczego `iidsToResolve`systemu Windows, na podstawie identyfikatorów interfejsu w programie .  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda nie może pobrać informacji dla określonego identyfikatora interfejsu, odpowiedni wpis w kolekcji "ICorDebugTypeEnum" będzie miał `ELEMENT_TYPE_END` typ `ELEMENT_TYPE_VOID` błędów z powodu problemów z pobieraniem danych lub nieznanych identyfikatorów interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Środowisko wykonawcze systemu Windows  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugAppDomain3, interfejs](icordebugappdomain3-interface.md)
