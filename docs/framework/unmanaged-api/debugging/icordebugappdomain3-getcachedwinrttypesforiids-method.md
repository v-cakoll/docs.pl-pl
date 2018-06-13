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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c8c82b3ace19d4b1d79fbfd296ce239e6da99ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409560"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda
Pobiera moduł wyliczający dla pamięci podręcznej [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów w domenie aplikacji w oparciu o ich identyfikatorów interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cReqTypes`  
 [in] Liczba wymaganych typów.  
  
 `iidsToResolve`  
 [in] Wskaźnik do tablicy zawiera identyfikatory interfejsu odpowiadającego zarządzanych reprezentacje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy, które mają zostać pobrane.  
  
 `ppTypesEnum`  
 [out] Wskaźnik do obiektu interfejsu "ICorDebugTypeEnum", który umożliwia wyliczenie zapisane w pamięci podręcznej adres zarządzane reprezentacje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] pobrać typy oparte na identyfikatorach interfejsu w `iidsToResolve`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda nie można pobrać informacji o identyfikator określonego interfejsu, odpowiadający mu wpis w kolekcji "ICorDebugTypeEnum" będzie mieć typ `ELEMENT_TYPE_END` błędy z powodu problemów pobierania danych, lub `ELEMENT_TYPE_VOID` dla nieznanego interfejsu identyfikatory.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugAppDomain3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
