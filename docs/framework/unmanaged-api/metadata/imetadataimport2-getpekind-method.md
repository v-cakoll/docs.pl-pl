---
title: IMetaDataImport2::GetPEKind — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c938ef8783a122dec2a5f5bd3775661d68fba62c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449406"
---
# <a name="imetadataimport2getpekind-method"></a>IMetaDataImport2::GetPEKind — Metoda
Pobiera wartość identyfikujący rodzaj kod przenośny plik wykonywalny (PE) pliku, zwykle biblioteki DLL lub EXE pliku, który jest zdefiniowany w bieżącym zakresie metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwPEKind`  
 [out] Wskaźnik do wartości [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) wyliczenie opisujące pliku PE.  
  
 `pdwMachine`  
 [out] Wskaźnik do wartość, która identyfikuje Architektura maszyny. W następnej sekcji prawidłowych wartości.  
  
## <a name="remarks"></a>Uwagi  
 Wartość przywołana przez `pdwMachine` parametr może być jedną z następujących czynności.  
  
|Wartość|Architektura komputera|  
|-----------|--------------------------|  
|IMAGE_FILE_MACHINE_I386<br /><br /> 0x014C|x86|  
|IMAGE_FILE_MACHINE_IA64<br /><br /> 0x0200|Intel IPF|  
|IMAGE_FILE_MACHINE_AMD64<br /><br /> 0x8664|X64|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [CorPEKind, wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
