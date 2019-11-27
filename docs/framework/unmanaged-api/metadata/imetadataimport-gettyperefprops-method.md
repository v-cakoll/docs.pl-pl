---
title: IMetaDataImport::GetTypeRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 6ea7605e062eb77e0488b3a9561c4d83be16fa7d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436708"
---
# <a name="imetadataimportgettyperefprops-method"></a>IMetaDataImport::GetTypeRefProps — Metoda
Pobiera metadane skojarzone z <xref:System.Type>, do którego odwołuje się określony token elementu TypeRef.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tr`  
 podczas Token elementu TypeRef, który reprezentuje typ do zwrócenia metadanych.  
  
 `ptkResolutionScope`  
 określoną Wskaźnik do zakresu, w którym następuje odwołanie. Ta wartość jest tokenem AssemblyRef lub ModuleRef.  
  
 `szName`  
 określoną Bufor zawierający nazwę typu.  
  
 `cchName`  
 podczas Żądany rozmiar w szerokich znakach `szName`.  
  
 `pchName`  
 określoną Zwrócony rozmiar w szerokich znakach `szName`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
