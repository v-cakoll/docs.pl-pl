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
ms.openlocfilehash: 8409e56b5ec4dbe47035a0555b6b7ce175b517ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490981"
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
 określoną Wskaźnik do flag użytych do mapowania. Ta wartość jest maska bitowa z wyliczenia [CorPinvokeMap —](corpinvokemap-enumeration.md) .  
  
 `szImportName`  
 określoną Nazwa niezarządzanej docelowej biblioteki DLL.  
  
 `cchImportName`  
 podczas Rozmiar w postaci znaków dwubajtowych `szImportName` .  
  
 `pchImportName`  
 określoną Liczba znaków dwubajtowych zwracana w `szImportName` .  
  
 `pmrImportDLL`  
 określoną Wskaźnik do tokenu elementu ModuleRef, który reprezentuje niezarządzaną bibliotekę obiektów docelowych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
