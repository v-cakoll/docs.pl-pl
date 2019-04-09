---
title: IMetaDataEmit::SetHandler — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac0e5db4a87b49d631bad4411f03fae8c1199aea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125635"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler — Metoda
Ustawia metodę odwołuje się określony `IUnknown` wskaźnik jako wywołania zwrotnego dla tokenu ponowne mapowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pUnk`  
 [in] Program obsługi, aby zarejestrować.  
  
## <a name="remarks"></a>Uwagi  
 Aparat metadanych wysyła powiadomienie za pomocą metody, która jest dostarczana przez `SetHandler`, aby kompilatory, którzy nie generują rekordów w sposób zoptymalizowany i który chcesz zoptymalizować zapisanych rekordów.  
  
 Jeśli metoda wywołania zwrotnego nie jest oferowana w ramach `SetHandler`, bez optymalizacji będą wykonywane na zapisywanie z wyjątkiem sytuacji, w których kilka importować zakresy zostały scalone przy użyciu `IMapToken` na scalanie dla każdego zakresu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
