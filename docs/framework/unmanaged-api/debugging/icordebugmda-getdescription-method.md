---
title: ICorDebugMDA::GetDescription — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fdace527194228dd6004a991950a80d23275650
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413299"
---
# <a name="icordebugmdagetdescription-method"></a>ICorDebugMDA::GetDescription — Metoda
Pobiera ciąg zawierający opis zarządzany Asystent debugowania (MDA) reprezentowany przez [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchName`  
 [in] Rozmiar buforu ciągu, w którym będzie przechowywany opis.  
  
 `pcchName`  
 [out] Wskaźnik do liczba bajtów zwrócona w buforze ciągu.  
  
 `szName`  
 [out] Bufor ciąg zawierający opis MDA.  
  
## <a name="remarks"></a>Uwagi  
 Ten ciąg może być zerowej długości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugMDA, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
