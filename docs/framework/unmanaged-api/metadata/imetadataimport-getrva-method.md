---
title: IMetaDataImport::GetRVA — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 190bcacc84646cfd9294cf2b6b53b0474f38758f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177219"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA — Metoda
Pobiera względny adres wirtualny (RVA) i flagi implementacji metody lub pola reprezentowane przez określony token.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [w] A MethodDef lub FieldDef token metadanych, który reprezentuje obiekt kodu do zwrócenia RVY dla. Jeśli token jest FieldDef, pole musi być zmienną globalną.  
  
 `pulCodeRVA`  
 [na zewnątrz] Wskaźnik do względnego adresu wirtualnego obiektu kodu reprezentowanego przez token.  
  
 `pdwImplFlags`  
 [na zewnątrz] Wskaźnik do flagi implementacji dla metody. Ta wartość jest maską bitową z wyliczenia [CorMethodImpl.](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) Wartość jest `pdwImplFlags` prawidłowa `tk` tylko wtedy, gdy jest tokenem MethodDef.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
