---
title: IMetaDataImport::FindTypeDefByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d2d7f9b459e5a46793d44728a9fea269ca47887
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492390"
---
# <a name="imetadataimportfindtypedefbyname-method"></a>IMetaDataImport::FindTypeDefByName — Metoda
Pobiera wskaźnik do metadanych TypeDef tokenu do <xref:System.Type> o określonej nazwie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [in] Nazwa typu, dla którego można uzyskać tokenu TypeDef.  
  
 `tkEnclosingClass`  
 [in] Element TypeDef lub TypeRef token reprezentujący otaczającej klasy. Jeśli typ do znalezienia nie jest klasą zagnieżdżoną, wartość tę należy ustawić na wartość NULL.  
  
 `ptd`  
 [out] Wskaźnik do zgodnego tokenu TypeDef.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
