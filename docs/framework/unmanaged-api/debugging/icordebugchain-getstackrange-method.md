---
title: ICorDebugChain::GetStackRange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac40927ac9469e4a2fb74fb550287130b9bb9f83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989459"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange — Metoda
Pobiera zakres adresów segment stosu dla tego łańcucha.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStart`  
 [out] Wskaźnik do `CORDB_ADDRESS` wartość, która jest adres początkowy segment stosu.  
  
 `pEnd`  
 [out] Wskaźnik do `CORDB_ADDRESS` wartość, która jest adres końcowy segmentu stosu.  
  
## <a name="remarks"></a>Uwagi  
 Zakresu liczbowego ma znaczenie tylko w przypadku porównywania lokalizacje ramki stosu. Nie można wprowadzać żadnych założeń dotyczących co rzeczywiście jest przechowywana na stosie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
