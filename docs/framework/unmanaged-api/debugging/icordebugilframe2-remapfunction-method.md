---
title: "ICorDebugILFrame2::RemapFunction — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.RemapFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4def20bc51d1b01b1c05b81a89fc3c983b4d1219
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction — Metoda
Ponownie mapuje funkcję edytowany przez określenie nowego przesunięcie język pośredni (MSIL) firmy Microsoft  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `newILOffset`  
 [in] Ramka stosu wskaźnik instrukcji ma zostać umieszczony nowy przesunięcie MSIL. Ta wartość musi być punktu sekwencji.  
  
 Odpowiada wywołującego Sprawdź poprawność tej wartości. Na przykład przesunięcie MSIL nie jest prawidłowy, jeśli znajduje się poza zakresem funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Podczas edycji funkcja ramki debuger może wywołać `RemapFunction` sposób wymiany w ostatniej wersji funkcja ramki, tak aby można było wykonać. Wykonywanie kodu zostanie rozpoczęte od danego przesunięcia MSIL.  
  
> [!NOTE]
>  Wywoływanie `RemapFunction`, takiej jak wywołanie [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), natychmiast spowoduje unieważnienie wszystkich interfejsów debugowania, które nie są związane z generowaniem ślad stosu wątku. Te interfejsy zawierają [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame i ICorDebugNativeFrame.  
  
 `RemapFunction` Metodę można wywołać tylko w kontekście bieżącej ramki i tylko w następujących przypadkach:  
  
-   Po otrzymaniu [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) wywołania zwrotnego, która nie ma jeszcze kontynuowane.  
  
-   Podczas wykonywania kodu została zatrzymana z powodu [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) zdarzeń dla tej ramki.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
