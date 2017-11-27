---
title: "ICorDebugThread::EnumerateChains — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.EnumerateChains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67b5a5da0a0053536ab4331e9d134464a4330500
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains — Metoda
Pobiera wskaźnika interfejsu, aby moduł wyliczający ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu w tym obiekcie ICorDebugThread.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppChains`  
 [out] Wskaźnik do adresu `ICorDebugChainEnum` powiązany obiekt, który umożliwia wyliczenie wszystkich stosu, w tym wątku, zaczynając od łańcucha aktywny (to znaczy najnowszej).  
  
## <a name="remarks"></a>Uwagi  
 Łańcuch stosu reprezentuje stosu wywołań fizycznych wątku. Następujące okoliczności Utwórz granicę łańcucha stosu:  
  
-   Przejście niezarządzany zarządzany lub niezarządzany zarządzany.  
  
-   Przełączenie kontekstu.  
  
-   A debugera przejęcie kontroli nad wątku użytkownika.  
  
 W przypadku prostego dla wątku, który działa wyłącznie zarządzany kod w pojedynczym kontekście odpowiednika będą istnieć między wątków i łańcuchów stosu.  
  
 Debuger może być rozmieszczanie stosy wywołań fizycznych, wszystkich wątków w stosy wywołań logiczne. Wymagałoby to sortowanie łańcuchów wszystkie wątki według ich relacje wywołujący/wywoływany i zgrupowania je.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
