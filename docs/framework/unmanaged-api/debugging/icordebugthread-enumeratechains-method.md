---
title: ICorDebugThread::EnumerateChains — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f131f7566376d6474f3189d5eb612b30bec2e2b7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648436"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains — Metoda
Pobiera moduł wyliczający icordebugchainenum —, który zawiera wszystkie łańcuchów stosu, w tym obiekcie ICorDebugThread wskaźnika interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppChains`  
 [out] Wskaźnik na adres `ICorDebugChainEnum` obiekt, który umożliwia wyliczenie wszystkich stosu, który tworzy powiązanie w tym wątku, zaczynając od łańcucha aktywny (to znaczy najnowszej).  
  
## <a name="remarks"></a>Uwagi  
 Łańcuch stosu reprezentuje stosu wywołań fizycznych dla wątku. Następujące okoliczności Utwórz granicę łańcucha stosu:  
  
- Zarządzane do niezarządzanego lub niezarządzane do zarządzanego przejście.  
  
- Przełączenie kontekstu.  
  
- A debugera przejęcie kontroli nad wątku użytkownika.  
  
 W prostym przypadku wątku, który działa wyłącznie zarządzany kod w jednym kontekście odpowiednika będzie istnieć między wątkami i łańcuchów stosu.  
  
 Debuger może być ponowne rozmieszczanie stosy wywołań fizycznych wszystkich wątków do stosów wywołań logicznych. Wymagałoby to sortowanie łańcuchów wszystkie wątki według ich relacji wywołujący/wywoływany i zgrupowania je.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
