---
title: IMetaDataAssemblyEmit::SetExportedTypeProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: dd1d6f1da6e49837eebd9356500f403c199b011b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177853"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a>IMetaDataAssemblyEmit::SetExportedTypeProps — Metoda
Modyfikuje `ExportedType` strukturę określonych metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ct`  
 [w] Token metadanych, który `ExportedType` określa strukturę metadanych, która ma zostać zmodyfikowana.  
  
 `tkImplementation`  
 [w] Token, typu `File`, `AssemblyRef`lub `ExportedType`, który określa, jak ten typ jest implementowany.  
  
 `tkTypeDef`  
 [w] Token, `TypeDef` do którego odwołuje się plik kodu.  
  
 `dwExportedTypeFlags`  
 [w] Bitowa kombinacja wartości określających atrybuty typu.  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć `ExportedType` strukturę metadanych, należy użyć [metody IMetaDataAssemblyEmit::DefineExportedType.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
