---
title: ICorDebugMDA::GetXML — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06eaa77ab655d57ad2cc0a3c5613c05444afd903
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660635"
---
# <a name="icordebugmdagetxml-method"></a>ICorDebugMDA::GetXML — Metoda
Pobiera pełną strumień XML skojarzony z zarządzanego Asystenta debugowania (MDA), reprezentowana przez [icordebugmda —](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchName`  
 [in] Rozmiar `szName` tablicy.  
  
 `pcchName`  
 [out] Wskaźnik do długość strumienia XML.  
  
 `szName`  
 [out] Tablica do przechowywania strumień XML. Tablica może być pusta.  
  
## <a name="remarks"></a>Uwagi  
 `GetXML` Metoda może wpłynąć na wydajność, w zależności od rozmiaru skojarzonego strumienia XML.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugMDA, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
