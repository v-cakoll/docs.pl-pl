---
title: ICorDebugThread2::GetConnectionID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc4963dcf686fe62f473aea1af86868df03718df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768966"
---
# <a name="icordebugthread2getconnectionid-method"></a>ICorDebugThread2::GetConnectionID — Metoda
Pobiera identyfikator połączenia dla tego obiektu icordebugthread2 —.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwConnectionId`  
 [out] A `CONNID` reprezentujący identyfikator połączenia.  
  
## <a name="remarks"></a>Uwagi  
 `GetConnectionID` Metoda zwraca zero w `pdwConnectionId` parametru, jeśli ten wątek nie jest częścią połączenia.  
  
 Jeśli ten wątek jest podłączony do wystąpienia programu Microsoft SQL Server 2005 Analysis Services (SSAS), `CONNID` mapuje do identyfikatora procesu serwera (SPID).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
