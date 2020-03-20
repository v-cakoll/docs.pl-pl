---
title: IMetaDataDispenser::OpenScopeOnMemory — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 492c37540ad68b5b134520218eedc59013c68519
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175931"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory — Metoda
Otwiera obszar pamięci zawierający istniejące metadane. Oznacza to, że ta metoda otwiera określony obszar pamięci, w którym istniejące dane są traktowane jako metadane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pData`  
 [w] Wskaźnik określający adres początkowy obszaru pamięci.  
  
 `cbData`  
 [w] Rozmiar obszaru pamięci w bajtach.  
  
 `dwOpenFlags`  
 [w] Wartość [wyliczenia CorOpenFlags,](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) aby określić tryb (odczyt, zapis i tak dalej) do otwarcia.  
  
 `riid`  
 [w] Identyfikator żądanego interfejsu metadanych do zwrócona; wywołujący użyje interfejsu do importowania (odczytu) lub emitowania (zapisu) metadanych.  
  
 Wartość `riid` musi określać jeden z interfejsów "import" lub "emituj". Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [na zewnątrz] Wskaźnik do zwróconego interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Kopię metadanych w pamięci można zbadać przy użyciu metod z jednego z interfejsów "importuj" lub dodać do przy użyciu metod z jednego z interfejsów "emituj".  
  
 Metoda `OpenScopeOnMemory` jest podobna do [metody IMetaDataDispenser::OpenScope,](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) z tą różnicą, że metadane będące przedmiotem zainteresowania już istnieją w pamięci, a nie w pliku na dysku.  
  
 Jeśli obszar docelowy pamięci nie zawiera metadanych wspólnego środowiska `OpenScopeOnMemory` wykonawczego języka (CLR), metoda zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataDispenser — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
