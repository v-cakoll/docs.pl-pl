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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b30bd3e97af8d222f629c5b4f9f318a9b6379e78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697962"
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual — Metoda
Metoda wywoływana przez wspólnego języka wspólnego (CLR) usługi dostępu do danych w celu zwolnienia pamięci, która była przydzielona wcześniej w przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `addr`  
 [in] A `CLRDATA_ADDRESS` wartość, która określa początkowy adres pamięci, który ma zostać zwolniony.  
  
 `size`  
 [in] Rozmiar w bajtach, pamięci, który ma zostać zwolniony.  
  
 `typeFlags`  
 [in] Flagi sterujące zwalnianie pamięci. Zobacz Win32 `VirtualFree` funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `FreeVirtual` Metody służy jako logiczne otoki dla Win32 `VirtualFree` funkcji.  
  
 Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [AllocVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
