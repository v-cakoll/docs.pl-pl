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
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177539"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler — Metoda
Ustawia metodę, do którą `IUnknown` odwołuje się określony wskaźnik jako wywołanie zwrotne powiadomień dla ponownego mapowania tokenu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pUnk`  
 [w] Program obsługi do zarejestrowania.  
  
## <a name="remarks"></a>Uwagi  
 Aparat metadanych wysyła powiadomienie przy użyciu `SetHandler`metody, która jest dostarczana przez , do kompilatorów, które nie generują rekordów w sposób zoptymalizowany i które chcą zoptymalizować zapisane rekordy.  
  
 Jeśli metoda wywołania zwrotnego `SetHandler`nie jest dostarczana za pośrednictwem , nie zostanie przeprowadzona optymalizacja przy zapisywaniu, z wyjątkiem sytuacji, gdy kilka zakresów importu zostało scalonych przy użyciu `IMapToken` scalania dla każdego zakresu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
