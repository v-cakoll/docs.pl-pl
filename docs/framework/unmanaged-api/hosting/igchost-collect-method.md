---
title: IGCHost::Collect — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdacb454783cfb8f90ea5a73807f0a199e16475d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154781"
---
# <a name="igchostcollect-method"></a>IGCHost::Collect — Metoda
Wymusza kolekcji wystąpi dla danej generacji, bez względu na stan bieżącej operacji wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Generation`  
 [in] Generowanie, na którym do wyrzucania elementów bezużytecznych. Wartość -1 wskazuje, że wszystkie generacje zostaną poddane wyrzucania elementów bezużytecznych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost.idl, GCHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IGCHost — Interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
