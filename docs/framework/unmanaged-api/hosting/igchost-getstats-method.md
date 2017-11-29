---
title: "IGCHost::GetStats — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.GetStats
api_location: mscoree.dll
api_type: COM
f1_keywords: GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c8db4f854b73d04e7260457c978a7a644677559
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats — Metoda
Pobiera statystyki dla bieżącego stanu systemu czyszczenia pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStats`  
 [w, out] Wskaźnik do [cor_gc_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktury zawierającą statystyki dla bieżącego stanu systemu czyszczenia pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Statystyki można za pomocą systemu inteligentne alokacji systemu kolekcji garbage działania pomocy. Na przykład system alokacji może ustalić, po zapoznaniu się dane statystyczne, którą chce dodać więcej pamięci lub wymusić kolekcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost.idl, GCHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IGCHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
