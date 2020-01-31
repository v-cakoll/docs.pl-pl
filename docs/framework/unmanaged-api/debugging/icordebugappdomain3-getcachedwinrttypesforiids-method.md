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
ms.openlocfilehash: 8b259636a8bd28abd3bba12c4a05dda3c13557e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784891"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda
Pobiera moduł wyliczający dla buforowanych środowisko wykonawcze systemu Windows typów w domenie aplikacji w oparciu o ich identyfikatory interfejsów.  
  
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
 podczas Liczba wymaganych typów.  
  
 `iidsToResolve`  
 podczas Wskaźnik do tablicy zawierającej identyfikatory interfejsów odpowiadające zarządzanym reprezentacjom typów środowisko wykonawcze systemu Windows do pobrania.  
  
 `ppTypesEnum`  
 określoną Wskaźnik do adresu obiektu interfejsu "ICorDebugTypeEnum", który umożliwia Wyliczenie buforowanych zarządzanych reprezentacji typów środowisko wykonawcze systemu Windows, opartych na identyfikatorach interfejsu w `iidsToResolve`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda nie może pobrać informacji o określonym identyfikatorze interfejsu, odpowiadający wpis w kolekcji "ICorDebugTypeEnum" będzie mieć typ `ELEMENT_TYPE_END` dla błędów spowodowanych problemami z pobieraniem danych lub `ELEMENT_TYPE_VOID` dla nieznanych identyfikatorów interfejsów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** środowisko wykonawcze systemu Windows  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugAppDomain3, interfejs](icordebugappdomain3-interface.md)
