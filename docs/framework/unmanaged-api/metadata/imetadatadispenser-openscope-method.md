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
ms.openlocfilehash: 5ce1af82631531f8f7105fbf92ba78db3cca437b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442330"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope — Metoda
Otwiera istniejący plik na dysku i mapuje jego metadane do pamięci.  
  
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
 podczas Nazwa pliku, który ma zostać otwarty. Plik musi zawierać metadane środowiska uruchomieniowego języka wspólnego (CLR).  
  
 `dwOpenFlags`  
 podczas Wartość wyliczenia [CorOpenFlags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) w celu określenia trybu (odczyt, zapis itd.) do otwarcia.  
  
 `riid`  
 podczas Identyfikator IID żądanego interfejsu metadanych do zwrócenia; Obiekt wywołujący będzie używać interfejsu do importowania metadanych (odczytu) lub emisji (zapisu).  
  
 Wartość `riid` musi określać jeden z interfejsów "Import" lub "Emituj". Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.  
  
 `ppIUnk`  
 określoną Wskaźnik do zwracanego interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Kopię metadanych w pamięci można zbadać przy użyciu metod z jednego z interfejsów "Import" lub dodać do metod przy użyciu metody z jednego z interfejsów "Emituj".  
  
 Jeśli plik docelowy nie zawiera metadanych CLR, Metoda `OpenScope` zakończy się niepowodzeniem.  
  
 W .NET Framework w wersji 1,0 i 1,1, jeśli zakres jest otwarty z `dwOpenFlags` ustawiony na ofRead, kwalifikuje się do udostępniania. Oznacza to, że jeśli kolejne wywołania `OpenScope` przekażą nazwę wcześniej otwartego pliku, istniejący zakres jest ponownie używany i nie zostanie utworzony nowy zestaw struktur danych. Problemy mogą jednak wystąpić z powodu tego udostępniania.  
  
 W .NET Framework w wersji 2,0 zakresy otwarte przy użyciu `dwOpenFlags` ustawione na ofRead nie są już udostępniane. Użyj wartości ofReadOnly, aby zezwolić na udostępnianie zakresu. Po udostępnieniu zakresu zapytania, które używają interfejsów metadanych "Odczyt/zapis", zakończą się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
