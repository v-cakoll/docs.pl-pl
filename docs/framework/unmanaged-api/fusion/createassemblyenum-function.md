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
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795388"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum — Funkcja
Pobiera wskaźnik do wystąpienia [IAssemblyEnum](iassemblyenum-interface.md) , które może wyliczyć obiekty w zestawie przy użyciu określonego [IAssemblyName](iassemblyname-interface.md).  
  
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
 określoną Wskaźnik do lokalizacji pamięci, która zawiera żądany `IAssemblyEnum` wskaźnik.  
  
 `pUnkReserved`  
 podczas Zarezerwowane do użytku w przyszłości. `pUnkReserved`musi być odwołaniem o wartości null.  
  
 `pName`  
 podczas `IAssemblyName` Żądanego zestawu. Ta nazwa jest używana do filtrowania wyliczania. Może ona mieć wartość null, aby wyliczyć wszystkie zestawy w globalnej pamięci podręcznej zestawów.  
  
 `dwFlags`  
 podczas Flagi modyfikujące zachowanie modułu wyliczającego. Ten parametr zawiera dokładnie jeden bit z wyliczenia [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .  
  
 `pvReserved`  
 podczas Zarezerwowane do użytku w przyszłości. `pvReserved`musi być odwołaniem o wartości null.  
  
## <a name="remarks"></a>Uwagi  
 Parametr zawiera dokładnie jeden bit `ASM_CACHE_FLAGS` z wyliczenia. `dwFlags`  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyEnum, interfejs](iassemblyenum-interface.md)
- [IAssemblyName, interfejs](iassemblyname-interface.md)
- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)
