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
ms.openlocfilehash: b92885d2a6514839a864d6a345dd8af8b07b90c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489816"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction — Metoda
Ponownie mapuje przeprowadzono edycję funkcji, określając nowy przesunięcia języka pośredniego (MSIL) firmy Microsoft  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `newILOffset`  
 [in] Ramka stosu wskaźnik instrukcji ma zostać umieszczony nowy przesunięcie MSIL. Ta wartość musi być punktu sekwencji.  
  
 Odpowiada za wywołującego Sprawdź poprawność tej wartości. Na przykład przesunięcie MSIL nie jest prawidłowy, jeśli znajduje się poza zakresem funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Podczas edycji funkcji ramki debuger może wywołać `RemapFunction` metodę, aby zamienić w najnowszej wersji funkcji ramki, dzięki czemu mogą być wykonywane. Wykonanie kodu spowoduje rozpoczęcie od danego przesunięcia MSIL.  
  
> [!NOTE]
>  Wywoływanie `RemapFunction`, tak jak podczas wywoływania [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), natychmiast spowoduje unieważnienie wszystkich interfejsów debugowania, które są związane z generowaniem ślad stosu dla wątku. Te interfejsy zawierają [icordebugchain —](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, icordebuginternalframe — i icordebugnativeframe —.  
  
 `RemapFunction` Metoda może być wywoływana tylko w kontekście bieżącej ramki i tylko w następujących przypadkach:  
  
-   Po otrzymaniu [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) wywołanie zwrotne, które jeszcze nie jest kontynuowane.  
  
-   Podczas wykonywania kodu została zatrzymana z powodu [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) zdarzenia dla tej ramki.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
