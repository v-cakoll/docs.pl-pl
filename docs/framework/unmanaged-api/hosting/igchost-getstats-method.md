---
title: IGCHost::GetStats — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3e0d6f68ffa5280d4616d4fa4ac60b4cb86f6a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437768"
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
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IGCHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
