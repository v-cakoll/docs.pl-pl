---
title: "ICLRDataTarget::ReadVirtual — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.ReadVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dffe95b1bab3d8dae72cc62f5d45baa85e39e590
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetreadvirtual-method"></a>ICLRDataTarget::ReadVirtual — Metoda
Odczytuje dane z adresów pamięci wirtualnej określony w buforze określona.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] CLRDATA_ADDRESS, która przechowuje adresów pamięci wirtualnej.  
  
 `buffer`  
 [out] Wskaźnik do buforu, który odbiera dane.  
  
 `bytesRequested`  
 [in] Długość buforu.  
  
 `bytesRead`  
 [out] Wskaźnik do liczba bajtów zwrócona.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRDataTarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
