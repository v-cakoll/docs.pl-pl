---
title: IMetaDataImport::GetTypeSpecFromToken — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7e060d2f72609b470dbd5060746a1458f5eed9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782311"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a>IMetaDataImport::GetTypeSpecFromToken — Metoda
Pobiera podpisu metadanych binarne specyfikacji typu reprezentowanego przez określony token.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `typespec`  
 [in] Token elementu TypeSpec związany z podpisem żądanego metadanych.  
  
 `ppvSig`  
 [out] Wskaźnik do podpisu metadanych binarnego.  
  
 `pcbSig`  
 [out] Rozmiar w bajtach podpisu metadanych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje powodzenie lub niepowodzenie. Błędy można przetestować za pomocą makra nie powiodło się.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
