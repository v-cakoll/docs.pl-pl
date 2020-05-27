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
ms.openlocfilehash: 67668aa7ff9faf035a047e485a8a3c8a451f45b9
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805239"
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats — Metoda
Pobiera statystyki bieżącego stanu systemu odzyskiwania pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStats`  
 [in. out] Wskaźnik do struktury [COR_GC_STATS](cor-gc-stats-structure.md) , która zawiera statystyki dotyczące bieżącego stanu systemu odzyskiwania pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Dane statystyczne mogą być używane przez system alokacji inteligentnej, aby ułatwić działanie systemu wyrzucania elementów bezużytecznych. Na przykład system alokacji może określić, po przejrzeniu statystyk, że należy dodać więcej pamięci lub wymusić zbieranie danych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost. idl, GCHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IGCHost, interfejs](igchost-interface.md)
