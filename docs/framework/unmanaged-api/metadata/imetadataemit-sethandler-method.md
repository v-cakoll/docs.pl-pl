---
title: "IMetaDataEmit::SetHandler — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetHandler
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d4a56db43f932a155b4251f019e39dc5640eb014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler — Metoda
Ustawia metodę odwołuje się określony `IUnknown` wskaźnika jako wywołanie zwrotne powiadomienia dla tokenu ponowne mapowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pUnk`  
 [in] Program obsługi do zarejestrowania.  
  
## <a name="remarks"></a>Uwagi  
 Aparat metadanych wysyła powiadomienia za pomocą metody, która jest dostarczana przez `SetHandler`, aby kompilatorów, które nie generują rekordów w sposób zoptymalizowany i który chcesz zoptymalizować zapisane rekordy.  
  
 Jeśli metoda wywołania zwrotnego nie jest zapewniana za pomocą `SetHandler`, optymalizacja nie zostaną wykonane na zapisywanie z wyjątkiem przypadków, w której kilka zaimportować zakresy zostały scalone przy użyciu `IMapToken` na scalanie dla każdego zakresu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
