---
title: "IMetaDataEmit::SetPinvokeMap — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a10482b12f9a34b0f247779f22c7cc70f871324a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetpinvokemap-method"></a>IMetaDataEmit::SetPinvokeMap — Metoda
Ustawia lub zmienia funkcje podpisu funkcji PInvoke metody, zgodnie z wcześniejszym wywołaniu [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tk`  
 [in] `mdToken` Do mapowania, które informacje dotyczą.  
  
 `dwMappingFlags`  
 [in] Flagi używane przez funkcji PInvoke w celu mapowania. To jest maską bitów z `CorPinvokeMap` wartości.  
  
 `szImportName`  
 [in] Nazwa elementu docelowego eksportu w natywnej biblioteki DLL.  
  
 `mrImportDLL`  
 [in] `mdModuleRef` Tokenów dla celu niezarządzanych bibliotek DLL.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
