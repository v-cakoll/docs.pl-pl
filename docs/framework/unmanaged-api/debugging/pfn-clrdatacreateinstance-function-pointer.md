---
title: "PFN_CLRDataCreateInstance — Wskaźnik funkcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PFN_CLRDataCreateInstance
api_location: mscordbi.dll
api_type: COM
f1_keywords: PFN_CLRDataCreateInstance
helpviewer_keywords: PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98a966434332549d9ceb7f29de81e19fa1b2108f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a>PFN_CLRDataCreateInstance — Wskaźnik funkcji
Punkty do funkcji, która tworzy obiekt interfejs dla elementu określonego obiektu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator interfejsu, który ma zostać utworzona.  
  
 `target`  
 [in] Wskaźnik do użytkownika zaimplementowana [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) obiekt, który reprezentuje element docelowy, dla którego ma zostać utworzony obiekt interfejsu.  
  
 `iface`  
 [out] Wskaźnik do adresu obiektu zwróconego interface.  
  
## <a name="remarks"></a>Uwagi  
 `ICLRDataTarget` Obiektu jest implementowany przez twórcę debugowania aplikacji. Implementacja zależy od typu reprezentowanego elementu docelowego. Element docelowy może być procesu, zrzutu pamięci, komputer zdalny i tak dalej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
