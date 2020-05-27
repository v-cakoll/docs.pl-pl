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
ms.openlocfilehash: 8d9de753f1c44338a96e990def80643d591f2a8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007471"
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
 podczas Wartość wyliczenia [CorOpenFlags —](coropenflags-enumeration.md) w celu określenia trybu (odczyt, zapis itd.) do otwarcia.  
  
 `riid`  
 podczas Identyfikator IID żądanego interfejsu metadanych do zwrócenia; Obiekt wywołujący będzie używać interfejsu do importowania metadanych (odczytu) lub emisji (zapisu).  
  
 Wartość `riid` musi określać jeden z interfejsów "Import" lub "Emituj". Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.  
  
 `ppIUnk`  
 określoną Wskaźnik do zwracanego interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Kopię metadanych w pamięci można zbadać przy użyciu metod z jednego z interfejsów "Import" lub dodać do metod przy użyciu metody z jednego z interfejsów "Emituj".  
  
 Jeśli plik docelowy nie zawiera metadanych CLR, `OpenScope` Metoda zakończy się niepowodzeniem.  
  
 W .NET Framework w wersji 1,0 i 1,1, jeśli zakres jest otwarty z `dwOpenFlags` ustawionym na ofRead, kwalifikuje się do udostępniania. Oznacza to, że jeśli kolejne wywołania `OpenScope` przekazane do nazwy pliku, który został wcześniej otwarty, istniejący zakres jest ponownie używany i nie zostanie utworzony nowy zestaw struktur danych. Problemy mogą jednak wystąpić z powodu tego udostępniania.  
  
 W .NET Framework w wersji 2,0 zakresy otwarte z `dwOpenFlags` ustawionym na ofRead nie są już udostępniane. Użyj wartości ofReadOnly, aby zezwolić na udostępnianie zakresu. Po udostępnieniu zakresu zapytania, które używają interfejsów metadanych "Odczyt/zapis", zakończą się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
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
