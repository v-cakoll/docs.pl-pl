---
title: ICLRDataTarget2::FreeVirtual — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: c084a3fcbbc02504124a511c6e136be32f408d21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112323"
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual — Metoda
Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do wolnej pamięci, która została wcześniej przydzielone w przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `addr`  
 podczas Wartość `CLRDATA_ADDRESS`, która określa początkowy adres pamięci, która ma zostać zwolniona.  
  
 `size`  
 podczas Rozmiar (w bajtach) pamięci, która ma zostać zwolniona.  
  
 `typeFlags`  
 podczas Flagi kontrolujące zwalnianie pamięci. Zobacz funkcję Win32 `VirtualFree`.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `FreeVirtual` służy jako otoka logiczna dla funkcji Win32 `VirtualFree`.  
  
 Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [AllocVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
