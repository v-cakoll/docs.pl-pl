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
ms.openlocfilehash: 69e5e05012d2b44a76a986591ec990f66bf8ae20
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007328"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory — Metoda
Otwiera obszar pamięci, który zawiera istniejące metadane. Oznacza to, że ta metoda otwiera określony obszar pamięci, w której istniejące dane są traktowane jako metadane.  
  
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
 podczas Wskaźnik określający adres początkowy obszaru pamięci.  
  
 `cbData`  
 podczas Rozmiar obszaru pamięci (w bajtach).  
  
 `dwOpenFlags`  
 podczas Wartość wyliczenia [CorOpenFlags —](coropenflags-enumeration.md) w celu określenia trybu (odczyt, zapis itd.) do otwarcia.  
  
 `riid`  
 podczas Identyfikator IID żądanego interfejsu metadanych do zwrócenia; Obiekt wywołujący będzie używać interfejsu do importowania metadanych (odczytu) lub emisji (zapisu).  
  
 Wartość `riid` musi określać jeden z interfejsów "Import" lub "Emituj". Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.  
  
 `ppIUnk`  
 określoną Wskaźnik do zwracanego interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Kopię metadanych w pamięci można zbadać przy użyciu metod z jednego z interfejsów "Import" lub dodać do metod przy użyciu metody z jednego z interfejsów "Emituj".  
  
 `OpenScopeOnMemory`Metoda jest podobna do metody [IMetaDataDispenser:: OpenScope —](imetadatadispenser-openscope-method.md) , z tą różnicą, że metadane zainteresowania już istnieją w pamięci, a nie w pliku na dysku.  
  
 Jeśli obszar docelowy pamięci nie zawiera metadanych środowiska uruchomieniowego języka wspólnego (CLR), `OpenScopeOnMemory` Metoda zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataDispenser — Interfejs](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interfejs](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit — Interfejs](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport — Interfejs](imetadataassemblyimport-interface.md)
- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
