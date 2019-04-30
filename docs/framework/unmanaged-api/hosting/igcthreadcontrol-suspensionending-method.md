---
title: IGCThreadControl::SuspensionEnding — Metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90b0cba50129bc728089e41ece5a30697cfc3bc5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763207"
---
# <a name="igcthreadcontrolsuspensionending-method"></a>IGCThreadControl::SuspensionEnding — Metoda
Powiadamia hosta, czy środowisko uruchomieniowe jest wznawianie wątków po wyrzucania elementów bezużytecznych lub innych zawieszenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Generation`  
 [in] Generowanie, na którym została wykonana wyrzucania elementów bezużytecznych.  
  
## <a name="remarks"></a>Uwagi  
 Nie zmienić termin egzaminu żadnych wątków podczas `SuspensionEnding` wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IGCThreadControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
