---
title: IMetaDataImport::IsValidToken — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a99ed42f500b83b5109631b21a88029995b43d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123884"
---
# <a name="imetadataimportisvalidtoken-method"></a>IMetaDataImport::IsValidToken — Metoda
Pobiera wartość wskazującą, czy określony token zawiera prawidłowe odwołanie do obiektu kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [in] Token do sprawdzania poprawności odwołania dla.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `tk` jest tokenem poprawności metadanych w bieżącym zakresie. W przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
