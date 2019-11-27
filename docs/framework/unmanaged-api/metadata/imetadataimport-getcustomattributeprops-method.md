---
title: IMetaDataImport::GetCustomAttributeProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
ms.openlocfilehash: 9a80336db4a5a8d7cfdebb7eb8d25bcb8f96e87c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437650"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps — Metoda
Pobiera wartość atrybutu niestandardowego z uwzględnieniem jego tokenu metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cv`  
 podczas Token metadanych, który reprezentuje atrybut niestandardowy do pobrania.  
  
 `ptkObj`  
 [out, opcjonalne] Token metadanych reprezentujący obiekt, który modyfikuje atrybut niestandardowy. Ta wartość może być dowolnego typu tokenu metadanych, z wyjątkiem `mdCustomAttribute`.  
  
 `ptkType`  
 [out, opcjonalne] `mdMethodDef` lub `mdMemberRef` token metadanych reprezentujący <xref:System.Type> zwróconego atrybutu niestandardowego.  
  
 `ppBlob`  
 [out, opcjonalne] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.  
  
 `pcbSize`  
 [out, opcjonalne] Rozmiar w bajtach danych zwróconych w *`ppBlob`.  
  
## <a name="remarks"></a>Uwagi  
 Atrybut niestandardowy jest przechowywany jako tablica danych, format zrozumiały dla aparatu metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
