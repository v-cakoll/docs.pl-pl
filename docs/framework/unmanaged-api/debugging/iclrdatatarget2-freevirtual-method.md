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
ms.openlocfilehash: 7eda9bfff6de6b386c16ad0a188931d9d3adcb93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793656"
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

- [ICLRDataTarget2, interfejs](iclrdatatarget2-interface.md)
- [AllocVirtual, metoda](iclrdatatarget2-allocvirtual-method.md)
