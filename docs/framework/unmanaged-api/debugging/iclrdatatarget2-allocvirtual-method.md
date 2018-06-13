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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46532592057f4fa6d9883d46dcef2f8f9e5f7228
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406347"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual — Metoda
Metoda wywoływana przez wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) dostępu do usługi danych można przydzielić pamięci w przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `addr`  
 [in] A `CLRDATA_ADDRESS` wartość, która określa żądany adres początkowy pamięci do przydzielenia.  
  
 `size`  
 [in] Rozmiar w bajtach pamięci do przydzielenia.  
  
 `typeFlags`  
 [in] Flagi, które kontrolują alokacji pamięci. Zobacz Win32 `VirtualAlloc` funkcji.  
  
 `protectFlags`  
 [in] Atrybuty ochrony alokacji pamięci. Zobacz Win32 `VirtualAlloc` funkcji.  
  
 `virt`  
 [out] Wskaźnik do `CLRDATA_ADDRESS` wartość, która określa rzeczywisty adres początkowy alokacji pamięci.  
  
## <a name="remarks"></a>Uwagi  
 `AllocVirtual` Metody służy jako otoka logiczne dla środowiska Win32 `VirtualAlloc` funkcji.  
  
 Ta metoda jest implementowany przez twórcę debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [FreeVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
