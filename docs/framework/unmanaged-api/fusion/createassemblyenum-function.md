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
ms.openlocfilehash: 0e54027806cef07fad4740c3bf5226fd26c72570
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108778"
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
 określoną Wskaźnik do lokalizacji pamięci zawierającej żądany `IAssemblyEnum` wskaźnik.  
  
 `pUnkReserved`  
 podczas Zarezerwowane do użytku w przyszłości. `pUnkReserved` musi być odwołaniem o wartości null.  
  
 `pName`  
 podczas `IAssemblyName` żądanego zestawu. Ta nazwa jest używana do filtrowania wyliczania. Może ona mieć wartość null, aby wyliczyć wszystkie zestawy w globalnej pamięci podręcznej zestawów.  
  
 `dwFlags`  
 podczas Flagi modyfikujące zachowanie modułu wyliczającego. Ten parametr zawiera dokładnie jeden bit z wyliczenia [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .  
  
 `pvReserved`  
 podczas Zarezerwowane do użytku w przyszłości. `pvReserved` musi być odwołaniem o wartości null.  
  
## <a name="remarks"></a>Uwagi  
 Parametr `dwFlags` zawiera dokładnie jeden bit z wyliczenia `ASM_CACHE_FLAGS`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyEnum, interfejs](iassemblyenum-interface.md)
- [IAssemblyName, interfejs](iassemblyname-interface.md)
- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)
