---
title: ICLRDataTarget2::AllocVirtual — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
ms.openlocfilehash: 7640f7fafd0bf52a302ac0da1e5df39b5da22d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091147"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual — Metoda
Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do przydzielania pamięci w przestrzeni adresowej tego procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `addr`  
 podczas Wartość `CLRDATA_ADDRESS`, która określa żądany adres początkowy pamięci do przydzielenia.  
  
 `size`  
 podczas Rozmiar pamięci do przydzielenia w bajtach.  
  
 `typeFlags`  
 podczas Flagi kontrolujące przydział pamięci. Zobacz funkcję Win32 `VirtualAlloc`.  
  
 `protectFlags`  
 podczas Atrybuty ochrony przydzieloną pamięć. Zobacz funkcję Win32 `VirtualAlloc`.  
  
 `virt`  
 określoną Wskaźnik do wartości `CLRDATA_ADDRESS`, który określa rzeczywisty adres początkowy przydzieloną pamięć.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `AllocVirtual` służy jako otoka logiczna dla funkcji Win32 `VirtualAlloc`.  
  
 Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [FreeVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
