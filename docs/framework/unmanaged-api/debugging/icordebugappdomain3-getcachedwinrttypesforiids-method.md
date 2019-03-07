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
ms.openlocfilehash: 601110d37fabbff01aeb14d8ca69a27a2463353f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491424"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda
Pobiera moduł wyliczający dla pamięci podręcznej [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów w domenie aplikacji w oparciu o ich identyfikatory interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cReqTypes`  
 [in] Liczba wymaganych typów.  
  
 `iidsToResolve`  
 [in] Wskaźnik do tablicy, który zawiera identyfikatory interfejsu odpowiadający reprezentacje zarządzane [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy, które mają zostać pobrane.  
  
 `ppTypesEnum`  
 [out] Wskaźnik na adres obiektu interfejsu "icordebugtypeenum —", który umożliwia wyliczenie buforowane zarządzane reprezentacje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] pobierane typy, oparte na identyfikatory interfejsu w `iidsToResolve`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda nie można pobrać informacji dla identyfikatora określonego interfejsu, odpowiadający mu wpis w kolekcji "Icordebugtypeenum —" będzie mieć typ `ELEMENT_TYPE_END` błędy z powodu problemów z pobierania danych, lub `ELEMENT_TYPE_VOID` dla nieznanego interfejsu identyfikatory.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugAppDomain3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
