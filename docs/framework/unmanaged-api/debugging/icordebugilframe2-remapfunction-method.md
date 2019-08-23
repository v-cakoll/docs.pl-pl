---
title: ICorDebugILFrame2::RemapFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75004f646c01897ef3e3016b073220ad33a0d925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967578"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction — Metoda
Ponownie mapuje edytowaną funkcję poprzez określenie nowego przesunięcia języka pośredniego firmy Microsoft (MSIL)  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `newILOffset`  
 podczas Nowe przesunięcie MSIL ramki stosu, w którym należy umieścić wskaźnik instrukcji. Ta wartość musi być punktem sekwencji.  
  
 Jest on odpowiedzialny za zagwarantowanie ważności tej wartości. Na przykład przesunięcie MSIL jest nieprawidłowe, jeśli znajduje się poza granicami funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Po edytowaniu funkcji ramki debuger może wywołać `RemapFunction` metodę, aby dokonać zamiany w najnowszej wersji funkcji ramki, aby można ją było wykonać. Wykonanie kodu rozpocznie się w danym przesunięciu MSIL.  
  
> [!NOTE]
> Wywołanie `RemapFunction`, takie jak wywołanie [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), natychmiast unieważnia wszystkie interfejsy debugowania, które są związane z generowaniem śladu stosu dla wątku. Te interfejsy obejmują [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame i ICorDebugNativeFrame.  
  
 `RemapFunction` Metodę można wywołać tylko w kontekście bieżącej ramki i tylko w jednym z następujących przypadków:  
  
- Po odebraniu wywołania zwrotnego [ICorDebugManagedCallback2:: FunctionRemapOpportunity —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) , które nie było jeszcze kontynuowane.  
  
- Mimo że wykonywanie kodu zostało zatrzymane z powodu zdarzenia [ICorDebugManagedCallback:: EditAndContinueRemap —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) dla tej ramki.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
