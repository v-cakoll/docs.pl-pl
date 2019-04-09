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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b94987631f7dbbe39e585a8ea2c2252b9427613
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079607"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope — Metoda
Otwiera istniejący plik na dysku i mapuje jego metadane do pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szScope`  
 [in] Nazwa pliku, który ma zostać otwarty. Plik musi zawierać wspólnego języka wspólnego (CLR) metadanych.  
  
 `dwOpenFlags`  
 [in] Wartość [coropenflags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczeniu, aby określić tryb (Odczyt, zapis i tak dalej) otwierania.  
  
 `riid`  
 [in] IID interfejsu żądaną metadanych ma zostać zwrócona; obiekt wywołujący użyje interfejsu do zaimportowania (odczyt) lub emitować metadane (Zapisz).  
  
 Wartość `riid` należy określić jeden z interfejsów "import" lub "Dodaj". Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [out] Wskaźnik do interfejsu zwrócone.  
  
## <a name="remarks"></a>Uwagi  
 Kopia w pamięci metadanych mogą być przeszukiwane przy użyciu metod z jednego z interfejsów "import" lub dodane do przy użyciu metod z jednego z interfejsów "Dodaj".  
  
 Jeśli plik docelowy nie zawiera metadanych CLR `OpenScope` metoda zakończy się niepowodzeniem.  
  
 W programie .NET Framework w wersji 1.0 i w wersji 1.1, jeśli zakres jest otwierany przy użyciu `dwOpenFlags` wartość ofRead, jest uprawniony do udostępniania. Oznacza to jeśli jest to kolejne wywołania `OpenScope` — dostęp próbny nazwę pliku, który był wcześniej otwarty, istniejący zakres jest ponownie i nie powstaje nowy zestaw struktur danych. Jednak problemy mogą wystąpić z powodu udostępnianie to.  
  
 W programie .NET Framework 2.0, zakresy otwartej z `dwOpenFlags` równa ofRead nie będą udostępniane. Użyj wartości ofReadOnly, aby zezwolić na zakres, który ma zostać udostępniony. Po udostępnieniu zakres zapytań, które używają "odczytu/zapisu" interfejsy metadanych nie powiedzie się.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataDispenser — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
