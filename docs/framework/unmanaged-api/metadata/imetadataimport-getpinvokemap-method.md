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
ms.openlocfilehash: c458fef77b49f522ca21dd5487731f4d43588cea
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437100"
---
# <a name="imetadataimportgetpinvokemap-method"></a>IMetaDataImport::GetPinvokeMap — Metoda
Pobiera token typu ModuleRef reprezentujący zestaw docelowy wywołania PInvoke.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Token FieldDef lub MethodDef, aby uzyskać metadane mapowania funkcji PInvoke dla.  
  
 `pdwMappingFlags`  
 określoną Wskaźnik do flag użytych do mapowania. Ta wartość jest maska bitowa z wyliczenia [CorPinvokeMap —](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) .  
  
 `szImportName`  
 określoną Nazwa niezarządzanej docelowej biblioteki DLL.  
  
 `cchImportName`  
 podczas Rozmiar w szerokich znakach `szImportName`.  
  
 `pchImportName`  
 określoną Liczba znaków dwubajtowych zwracanych w `szImportName`.  
  
 `pmrImportDLL`  
 określoną Wskaźnik do tokenu elementu ModuleRef, który reprezentuje niezarządzaną bibliotekę obiektów docelowych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
