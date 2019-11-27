---
title: IMetaDataDispenser::DefineScope — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: 381c38542dcde242c0a1a4e71e9b99316328159d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436245"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope — Metoda
Tworzy nowy obszar w pamięci, w którym można tworzyć nowe metadane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `rclsid`  
 podczas Identyfikator CLSID wersji struktur metadanych, które mają zostać utworzone. Ta wartość musi być CLSID_CorMetaDataRuntime dla .NET Framework wersja 2,0.  
  
 `dwCreateFlags`  
 podczas Flagi określające opcje. Ta wartość musi być równa zero dla .NET Framework 2,0.  
  
 `riid`  
 podczas Identyfikator IID żądanego interfejsu metadanych do zwrócenia; Obiekt wywołujący użyje interfejsu do utworzenia nowych metadanych.  
  
 Wartość `riid` musi określać jeden z interfejsów "Emituj". Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit lub IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 określoną Wskaźnik do zwracanego interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 `DefineScope` tworzy zestaw tabel metadanych w pamięci, generuje unikatowy identyfikator GUID (identyfikator wersji modułu lub MVID) dla metadanych i tworzy wpis w tabeli modułów dla wyemitowanej jednostki kompilacji.  
  
 Można dołączać atrybuty do zakresu metadanych jako całości przy użyciu metody [IMetaDataEmit:: SetModuleProps —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) lub [IMetaDataEmit::D efinecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) , zgodnie z potrzebami.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
