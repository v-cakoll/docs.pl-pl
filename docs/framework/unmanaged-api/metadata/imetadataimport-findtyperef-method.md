---
title: IMetaDataImport::FindTypeRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b47369e8cee2215b3e7a21e9f069d18dffda847a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691761"
---
# <a name="imetadataimportfindtyperef-method"></a>IMetaDataImport::FindTypeRef — Metoda
Pobiera wskaźnik do TypeRef tokenu do <xref:System.Type> odwołania, który znajduje się w podanym zakresie i który ma określoną nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkResolutionScope`  
 [in] Element ModuleRef, elementu AssemblyRef lub TypeRef token, który określa moduł, zestawu lub typu, odpowiednio, w której typ odwołania jest zdefiniowana.  
  
 `szName`  
 [in] Nazwa odwołania typu do wyszukania.  
  
 `ptr`  
 [out] Wskaźnik do dopasowania token TypeRef.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
