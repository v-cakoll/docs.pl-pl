---
title: "CreateAssemblyEnum — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyEnum
helpviewer_keywords: CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3719da442b2c2c589772a0bc19cec3efb4e6dace
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum — Funkcja
Pobiera wskaźnik do [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) wystąpienie, które można wyliczyć obiektów w zestawie z określonym [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pEnum`  
 [out] Wskaźnik do lokalizacji w pamięci, który zawiera żądanie `IAssemblyEnum` wskaźnika.  
  
 `pUnkReserved`  
 [in] Zarezerwowane dla przyszłego rozszerzalności. `pUnkReserved`musi być odwołanie o wartości null.  
  
 `pName`  
 [in] `IAssemblyName` Żądanego zestawu. Ta nazwa jest używana do filtrowania wyliczenia. Może być null wyliczyć wszystkich zestawów w globalnej pamięci podręcznej zestawów.  
  
 `dwFlags`  
 [in] Flagi do modyfikowania zachowania modułu wyliczającego. Ten parametr zawiera dokładnie jeden bit z [asm_cache_flags —](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) wyliczenia.  
  
 `pvReserved`  
 [in] Zarezerwowane dla przyszłego rozszerzalności. `pvReserved`musi być odwołanie o wartości null.  
  
## <a name="remarks"></a>Uwagi  
 `dwFlags` Parametr zawiera dokładnie jeden bit z `ASM_CACHE_FLAGS` wyliczenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [IAssemblyName, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
