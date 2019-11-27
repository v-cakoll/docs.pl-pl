---
title: IMetaDataImport2::GetGenericParamProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: a8c5dd263401002deaee3d21f1e41b41a29faec2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427299"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps — Metoda
Pobiera metadane skojarzone z parametrem ogólnym reprezentowanym przez określony token.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `gp`  
 podczas Token reprezentujący parametr generyczny, dla którego mają być zwracane metadane.  
  
 `pulParamSeq`  
 określoną Pozycja porządkowa parametru `Type` w konstruktorze nadrzędnym lub metodzie.  
  
 `pdwParamFlags`  
 określoną Wartość wyliczenia [CorGenericParamAttr —](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) opisująca `Type` parametru generycznego.  
  
 `ptOwner`  
 określoną Token TypeDef lub MethodDef, który reprezentuje właściciela parametru.  
  
 `reserved`  
 określoną Zarezerwowane do użytku w przyszłości.  
  
 `wzName`  
 określoną Nazwa parametru generycznego.  
  
 `cchName`  
 podczas Rozmiar buforu `wzName`.  
  
 `pchName`  
 określoną Zwrócony rozmiar nazwy w znaki dwubajtowe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
