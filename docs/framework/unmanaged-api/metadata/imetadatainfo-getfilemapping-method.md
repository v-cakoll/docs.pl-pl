---
title: IMetaDataInfo::GetFileMapping — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175268"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping — Metoda
Pobiera obszar pamięci zamapowany plik i typ mapowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppvData`  
 [na zewnątrz] Wskaźnik do początku zamapowany plik.  
  
 `pcbData`  
 [na zewnątrz] Rozmiar zamapowanych regionów. Jeśli `pdwMappingType` `fmFlat`tak , jest to rozmiar pliku.  
  
 `pdwMappingType`  
 [na zewnątrz] Wartość [CorFileMapping,](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) która wskazuje typ mapowania. Bieżąca implementacja środowiska wykonawczego języka wspólnego (CLR) zawsze zwraca `fmFlat`. Inne wartości są zarezerwowane do wykorzystania w przyszłości. Jednak zawsze należy sprawdzić zwracaną wartość, ponieważ inne wartości mogą być włączone w przyszłych wersjach lub wersjach usługi.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|Wszystkie wyjścia są wypełnione.|  
|`E_INVALIDARG`|Wartość NULL została przekazana jako wartość argumentu.|  
|`COR_E_NOTSUPPORTED`|Implementacja CLR nie może dostarczyć informacji o regionie pamięci. Może się to zdarzyć z następujących powodów:<br /><br /> - Zakres metadanych został `ofWrite` `ofCopyMemory` otwarty z lub flagi.<br />- Zakres metadanych został `ofReadOnly` otwarty bez flagi.<br />- Metoda [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) została użyta do otwarcia tylko części metadanych pliku.<br />- Plik nie jest przenośnym plikiem wykonywalnym (PE). **Uwaga:**  Warunki te zależą od implementacji CLR i mogą być osłabione w przyszłych wersjach CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Pamięć, `ppvData` która wskazuje jest prawidłowa tylko tak długo, jak zakres podstawowych metadanych jest otwarty.  
  
 Aby ta metoda działała, podczas mapowania metadanych pliku na dysku do pamięci przez [wywołanie IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metody, należy określić `ofReadOnly` flagę i nie należy określić `ofWrite` lub `ofCopyMemory` flagi.  
  
 Wybór typu mapowania plików dla każdego zakresu jest specyficzny dla danej implementacji CLR. Nie można go ustawić przez użytkownika. Bieżąca implementacja CLR `fmFlat` zawsze `pdwMappingType`zwraca w , ale może się to zmienić w przyszłych wersjach CLR lub w przyszłych wersjach usługi danej wersji. Zawsze należy sprawdzić zwróconą `pdwMappingType`wartość w , ponieważ różne typy będą miały różne układy i przesunięcia.  
  
 Przekazywanie null dla dowolnego z trzech parametrów nie jest obsługiwane. Metoda zwraca `E_INVALIDARG`, a żadne z wyjść nie są wypełnione. Ignorowanie typu mapowania lub rozmiaru regionu może spowodować nieprawidłowe zakończenie programu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataInfo, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping, wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
