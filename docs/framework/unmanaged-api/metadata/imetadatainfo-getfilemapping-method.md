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
ms.openlocfilehash: 0cd2071d4410615a08e774ba30e0e8fe8d1fa7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436176"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping — Metoda
Pobiera region pamięci zamapowanego pliku i typ mapowania.  
  
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
 określoną Wskaźnik do początku zamapowanego pliku.  
  
 `pcbData`  
 określoną Rozmiar zamapowanego regionu. Jeśli `pdwMappingType` jest `fmFlat`, jest to rozmiar pliku.  
  
 `pdwMappingType`  
 określoną Wartość [CorFileMapping —](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) , która wskazuje typ mapowania. Bieżąca implementacja środowiska uruchomieniowego języka wspólnego (CLR) zawsze zwraca `fmFlat`. Inne wartości są zarezerwowane do użytku w przyszłości. Należy jednak zawsze zweryfikować zwracaną wartość, ponieważ inne wartości mogą być włączone w przyszłych wersjach lub wersjach usługi.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|Wszystkie dane wyjściowe są wypełnione.|  
|`E_INVALIDARG`|Jako wartość argumentu przekazano wartość NULL.|  
|`COR_E_NOTSUPPORTED`|Implementacja środowiska CLR nie może dostarczyć informacji o regionie pamięci. Przyczyny mogą być następujące:<br /><br /> -Zakres metadanych został otwarty z flagą `ofWrite` lub `ofCopyMemory`.<br />-Zakres metadanych został otwarty bez flagi `ofReadOnly`.<br />-Metoda [IMetaDataDispenser:: OpenScopeOnMemory —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) została użyta do otwarcia tylko części metadanych pliku.<br />-Plik nie jest przenośnym plikiem wykonywalnym (PE). **Uwaga:**  Te warunki są zależne od implementacji środowiska CLR i mogą być osłabione w przyszłych wersjach środowiska CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Pamięć, do której wskazuje `ppvData`, jest prawidłowa tylko tak długo, jak źródłowy zakres metadanych jest otwarty.  
  
 Aby ta metoda działała, podczas mapowania metadanych pliku na dysk do pamięci przez wywołanie metody [IMetaDataDispenser:: OpenScope —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) należy określić flagę `ofReadOnly` i nie należy określać flagi `ofWrite` lub `ofCopyMemory`.  
  
 Wybór typu mapowania plików dla każdego zakresu jest specyficzny dla danej implementacji środowiska CLR. Nie można go ustawić przez użytkownika. Bieżąca implementacja środowiska CLR zawsze zwraca `fmFlat` w `pdwMappingType`, ale może to zmienić w przyszłych wersjach środowiska CLR lub w przyszłych wersjach usługi danej wersji. Należy zawsze sprawdzać wartość zwracaną w `pdwMappingType`, ponieważ różne typy będą mieć różne układy i przesunięcia.  
  
 Przekazywanie wartości NULL dla dowolnego z trzech parametrów nie jest obsługiwane. Metoda zwraca `E_INVALIDARG`i żadne wyjście nie jest wypełnione. Ignorowanie typu mapowania lub rozmiaru regionu może spowodować nietypowe zakończenie działania programu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataInfo, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping, wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
