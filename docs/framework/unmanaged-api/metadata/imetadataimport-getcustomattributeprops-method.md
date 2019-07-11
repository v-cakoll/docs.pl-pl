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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c714915651d8660a739d8ee6518fc3814af4c08d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782415"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps — Metoda
Pobiera wartość atrybutu niestandardowego, biorąc pod uwagę jego token metadanych.  
  
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
 [in] Token metadanych, który reprezentuje atrybut niestandardowy do pobrania.  
  
 `ptkObj`  
 [out, opcjonalny] Token metadanych reprezentujący obiekt, który modyfikuje atrybutu niestandardowego. Ta wartość może być dowolnego typu tokenu metadanych z wyjątkiem `mdCustomAttribute`.  
  
 `ptkType`  
 [out, opcjonalny] `mdMethodDef` Lub `mdMemberRef` metadanych token reprezentujący <xref:System.Type> zwrócone atrybutu niestandardowego.  
  
 `ppBlob`  
 [out, opcjonalny] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.  
  
 `pcbSize`  
 [out, opcjonalny] Rozmiar w bajtach dane zwrócone w *`ppBlob`.  
  
## <a name="remarks"></a>Uwagi  
 Atrybut niestandardowy jest przechowywany jako tablicę danych, formatu, który zrozumieniu przez aparat metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
