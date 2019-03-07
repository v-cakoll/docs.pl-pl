---
title: IMetaDataEmit::DefineMethodImpl — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3a6f98dca1c6665b312384721a8fb590f914175
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468900"
---
# <a name="imetadataemitdefinemethodimpl-method"></a>IMetaDataEmit::DefineMethodImpl — Metoda
Tworzy definicję dla implementacji metody dziedziczone z interfejsu, a następnie zwraca token do tej definicji implementacji metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] `mdTypedef` Tokenu dla klasy implementującej.  
  
 `tkBody`  
 [in] `mdMethodDef` Lub `mdMethodRef` tokenu treści kodu.  
  
 `tkDecl`  
 [in] `mdMethodDef` Lub `mdMethodRef` token metody interfejsu implementowanego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
