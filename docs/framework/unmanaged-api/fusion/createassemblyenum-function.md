---
title: CreateAssemblyEnum — Funkcja
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c56b0168df6e4aee69b5d3e5fbbe027ca2c8974a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778444"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum — Funkcja
Pobiera wskaźnik do [iassemblyenum —](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) wystąpienie, które można wyliczyć obiektów w zestawie z określonym [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `pEnum`  
 [out] Wskaźnik do lokalizacji pamięci, która zawiera żądanie `IAssemblyEnum` wskaźnika.  
  
 `pUnkReserved`  
 [in] Zarezerwowane dla przyszłej rozszerzalności. `pUnkReserved` musi być odwołanie o wartości null.  
  
 `pName`  
 [in] `IAssemblyName` Żądanego zestawu. Ta nazwa jest używana do filtrowania wyliczenia. Może być null można wyliczyć wszystkie zestawy w globalnej pamięci podręcznej.  
  
 `dwFlags`  
 [in] Flagi do modyfikowania zachowania modułu wyliczającego. Ten parametr zawiera dokładnie jeden bit z [asm_cache_flags —](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) wyliczenia.  
  
 `pvReserved`  
 [in] Zarezerwowane dla przyszłej rozszerzalności. `pvReserved` musi być odwołanie o wartości null.  
  
## <a name="remarks"></a>Uwagi  
 `dwFlags` Parametr zawiera dokładnie jeden bit z `ASM_CACHE_FLAGS` wyliczenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [IAssemblyName, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
