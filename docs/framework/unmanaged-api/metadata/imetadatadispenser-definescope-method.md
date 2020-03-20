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
ms.openlocfilehash: 2f9325f3795262a0c33af02f87fc5d3a020658cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177632"
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
 [w] Identyfikator CLSID wersji struktur metadanych, które mają zostać utworzone. Ta wartość musi być CLSID_CorMetaDataRuntime dla programu .NET Framework w wersji 2.0.  
  
 `dwCreateFlags`  
 [w] Flagi określające opcje. Ta wartość musi wynosić zero dla programu .NET Framework 2.0.  
  
 `riid`  
 [w] Identyfikator żądanego interfejsu metadanych do zwrócona; wywołujący użyje interfejsu do utworzenia nowych metadanych.  
  
 Wartość `riid` musi określać jeden z interfejsów "emitować". Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit lub IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 [na zewnątrz] Wskaźnik do zwróconego interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 `DefineScope`tworzy zestaw tabel metadanych w pamięci, generuje unikatowy identyfikator GUID (identyfikator wersji modułu lub MVID) dla metadanych i tworzy wpis w tabeli modułów dla emitowanej jednostki kompilacji.  
  
 Atrybuty można dołączyć do zakresu metadanych jako całości przy użyciu [metody IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) lub [IMetaDataEmit::DefineCustomAttribute.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataDispenser — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
