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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d305aa59c1b9e9e1225b30f12e36fc689d584db1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778885"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA — Metoda
Pobiera względnych adresów wirtualnych (RVA) i flagi implementacji metody lub pola, reprezentowane przez określony token.  
  
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
 [in] MethodDef lub FieldDef metadanych token, który reprezentuje obiekt kodu, aby zwrócić adres RVA dla. Jeśli token jest FieldDef, pole musi być zmienną globalną.  
  
 `pulCodeRVA`  
 [out] Wskaźnik względne wirtualnym adresem kod obiektu reprezentowanego przez ten token.  
  
 `pdwImplFlags`  
 [out] Wskaźnik flagi implementacji metody. Ta wartość jest z [cormethodimpl —](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) wyliczenia. Wartość `pdwImplFlags` jest prawidłowa tylko wtedy, gdy `tk` jest tokenem MethodDef.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
