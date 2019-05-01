---
title: IMetaDataImport::GetPinvokeMap — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 99aea385cf5e3c8bcf7cf39b7cc5618f99f8a631
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777588"
---
# <a name="imetadataimportgetpinvokemap-method"></a>IMetaDataImport::GetPinvokeMap — Metoda
Pobiera element ModuleRef jest token reprezentujący zestaw docelowy wywołania funkcji PInvoke.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [in] Token FieldDef lub MethodDef można pobrać metadanych mapowania funkcji PInvoke.  
  
 `pdwMappingFlags`  
 [out] Wskaźnik flagi używane do mapowania. Ta wartość jest z [corpinvokemap —](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) wyliczenia.  
  
 `szImportName`  
 [out] Nazwa docelowej niezarządzanych bibliotek DLL.  
  
 `cchImportName`  
 [in] Rozmiar w znaków `szImportName`.  
  
 `pchImportName`  
 [out] Liczba znaków dwubajtowych zwracane w `szImportName`.  
  
 `pmrImportDLL`  
 [out] Wskaźnik do tokenu element ModuleRef, który reprezentuje biblioteki obiektów docelowych niezarządzanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
