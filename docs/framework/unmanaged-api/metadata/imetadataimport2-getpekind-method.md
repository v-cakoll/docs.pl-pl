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
ms.openlocfilehash: a3d0ee533ec0ece308f87c170846ef102bd3a3b9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478881"
---
# <a name="imetadataimport2getpekind-method"></a>IMetaDataImport2::GetPEKind — Metoda
Pobiera wartość identyfikujący rodzaj kodu w pliku wykonalnego (PE) pliku, zazwyczaj pliku DLL lub EXE, który jest zdefiniowany w bieżącym zakresie metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwPEKind`  
 [out] Wskaźnik do wartości [corpekind —](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) wyliczenie opisujące pliku PE.  
  
 `pdwMachine`  
 [out] Wskaźnik do wartość, która identyfikuje architektury maszyny. Zobacz następną sekcję uzyskać odpowiednie wartości.  
  
## <a name="remarks"></a>Uwagi  
 Wartość przywołana przez `pdwMachine` parametr może być jedną z następujących czynności.  
  
|Wartość|Architektura komputera|  
|-----------|--------------------------|  
|IMAGE_FILE_MACHINE_I386<br /><br /> 0x014C|x86|  
|IMAGE_FILE_MACHINE_IA64<br /><br /> 0x0200|Intel IPF|  
|IMAGE_FILE_MACHINE_AMD64<br /><br /> 0x8664|X64|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [CorPEKind, wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
