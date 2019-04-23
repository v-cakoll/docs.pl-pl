---
title: IDebugAutoAttach::AutoAttach — Metoda
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5064e66708044d82e3a097c8235b5b28a3412200
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077137"
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach — Metoda
Wykonuje automatyczne wywoływane serwer debugera dołączania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `guidPort`  
 [in] Zawsze ustawiony na wartość `GUID_NULL`.  
  
 `dwPid`  
 [in] Identyfikator, zwykle pobierane za pomocą procesu `GetCurrentProcessId` funkcji.  
  
 `dwProgramType`  
 [in] Typ programu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, lub `AUTOATTACH_PROGRAM_UNKNOWN`.  
  
 `dwProgramId`  
 [in] Identyfikator programu.  
  
 `pszSessionId`  
 [in] Ciąg przekazywany przez czasownik debug.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** DbgAutoAttach.h  
  
## <a name="see-also"></a>Zobacz także

- [IDebugAutoAttach, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
