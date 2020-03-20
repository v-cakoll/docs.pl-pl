---
title: IMetaDataDispenser::OpenScope — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175944"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope — Metoda
Otwiera istniejący plik na dysku i mapuje jego metadane w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szScope`  
 [w] Nazwa pliku, który ma zostać otwarty. Plik musi zawierać metadane wspólnego środowiska wykonawczego języka (CLR).  
  
 `dwOpenFlags`  
 [w] Wartość [wyliczenia CorOpenFlags,](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) aby określić tryb (odczyt, zapis i tak dalej) do otwarcia.  
  
 `riid`  
 [w] Identyfikator żądanego interfejsu metadanych do zwrócona; wywołujący użyje interfejsu do importowania (odczytu) lub emitowania (zapisu) metadanych.  
  
 Wartość `riid` musi określać jeden z interfejsów "import" lub "emituj". Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [na zewnątrz] Wskaźnik do zwróconego interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Kopię metadanych w pamięci można zbadać przy użyciu metod z jednego z interfejsów "importuj" lub dodać do przy użyciu metod z jednego z interfejsów "emituj".  
  
 Jeśli plik docelowy nie zawiera metadanych CLR, metoda zakończy się niepowodzeniem. `OpenScope`  
  
 W .NET Framework w wersji 1.0 i wersji 1.1, jeśli zakres jest otwarty z `dwOpenFlags` zestawem doread, kwalifikuje się do udostępniania. Oznacza to, że `OpenScope` jeśli kolejne wywołania przekazania w nazwie pliku, który został wcześniej otwarty, istniejący zakres jest ponownie i nowy zestaw struktur danych nie jest tworzony. Jednak problemy mogą pojawić się z powodu tego udostępniania.  
  
 W .NET Framework w wersji 2.0 `dwOpenFlags` zakresy otwarte z zestawem doread nie są już współużytkowane. Użyj ofReadOnly wartość, aby umożliwić zakres do udostępnienia. Gdy zakres jest współużytkowany, kwerendy, które używają interfejsów metadanych "odczyt/zapis" zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
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
