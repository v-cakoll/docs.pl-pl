---
title: "IDebugAutoAttach::AutoAttach — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebugAutoAttach.AutoAttach
api_location: diasymreader.dll
api_type: COM
f1_keywords: IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 359aaf96c42a661657028d508f096f9625d4ba71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach — Metoda
Wykonuje automatycznie wywoływane serwera debugera dołączyć.  
  
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
 [in] Identyfikator normalnie pobierane z procesu `GetCurrentProcessId` funkcji.  
  
 `dwProgramType`  
 [in] Program typu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, lub `AUTOATTACH_PROGRAM_UNKNOWN`.  
  
 `dwProgramId`  
 [in] Identyfikator programu.  
  
 `pszSessionId`  
 [in] Ciąg przekazany przez zlecenia debug.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** DbgAutoAttach.h  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugAutoAttach — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
