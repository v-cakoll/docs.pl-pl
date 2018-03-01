---
title: "ICorDebugProcess::IsTransitionStub — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9fe38cf5f53c2514b845238c1d52fa12df526fdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub — Metoda
Pobiera wartość wskazującą, czy adres znajduje się wewnątrz skrótowa, która spowoduje przejście do kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] A `CORDB_ADDRESS` wartość, która określa adres jest zagrożona.  
  
 `pbTransitionStub`  
 [out] Wskaźnik do wartość logiczna, która jest `true` , jeśli określony adres znajduje się wewnątrz skrótowa, która spowoduje przejście do zarządzanego kodu; w przeciwnym razie *`pbTransitionStub` jest `false`.  
  
## <a name="remarks"></a>Uwagi  
 `IsTransitionStub` Metoda pozwala przez kod niezarządzany wykonywania krokowego podjęcie decyzji dotyczącej powrócić wykonywania krokowego kontroli do zarządzanych stepper.  
  
 Można również klas zastępczych przejścia tożsamości, analizując informacje w przenośny plik wykonywalny (PE).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
