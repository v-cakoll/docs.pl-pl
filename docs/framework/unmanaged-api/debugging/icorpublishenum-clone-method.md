---
title: ICorPublishEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0ce1d8c0074f62d35e16465b368269e233a713b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105134"
---
# <a name="icorpublishenumclone-method"></a>ICorPublishEnum::Clone — Metoda
Tworzy kopię [icorpublishenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Wskaźnik na adres `ICorPublishEnum` obiektu, który jest kopią tego `ICorPublishEnum` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublishEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
