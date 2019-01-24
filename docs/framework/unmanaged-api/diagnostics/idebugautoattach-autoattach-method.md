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
ms.openlocfilehash: 6b45b5e1a7589329b788160df3ac4493efa48197
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663521"
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
  
#### <a name="parameters"></a>Parametry  
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
