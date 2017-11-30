---
title: "ICorDebugFunction::GetLocalVarSigToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetLocalVarSigToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67cdb14577ca44f44685807fda4f308b50462002
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a>ICorDebugFunction::GetLocalVarSigToken — Metoda
Pobiera metadane token podpisu lokalnego zmiennej funkcji, która jest reprezentowana przez to wystąpienie ICorDebugFunction.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pmdSig`  
 [out] Wskaźnik do `mdSignature` tokenu dla zmiennej podpisu lokalnego z tej funkcji, lub `mdSignatureNil`, jeśli ta funkcja nie ma lokalnych zmiennych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
