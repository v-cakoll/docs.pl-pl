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
ms.openlocfilehash: a3a5cadc1b5a9df7967aae271ff10296843121dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436959"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA — Metoda
Pobiera względny adres wirtualny (RVA) oraz flagi implementacji metody lub pola reprezentowanego przez określony token.  
  
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
 podczas Token metadanych MethodDef lub FieldDef reprezentujący obiekt kodu do zwrócenia adresu RVA. Jeśli token jest FieldDef, pole musi być zmienną globalną.  
  
 `pulCodeRVA`  
 określoną Wskaźnik do względnego adresu wirtualnego obiektu kodu reprezentowanego przez token.  
  
 `pdwImplFlags`  
 określoną Wskaźnik do flag implementacji dla metody. Ta wartość jest maska bitowa z wyliczenia [CorMethodImpl —](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) . Wartość `pdwImplFlags` jest prawidłowa tylko wtedy, gdy `tk` jest tokenem MethodDef.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
