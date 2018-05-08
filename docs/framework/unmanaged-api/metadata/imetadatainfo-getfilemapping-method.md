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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 562b6fcd015441ce5eb6b5f0ab7a4f361bb229c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping — Metoda
Pobiera regionu pamięci zamapowanego pliku, a Typ mapowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppvData`  
 [out] Wskaźnik do początku zamapowanego pliku.  
  
 `pcbData`  
 [out] Rozmiar mapowanego regionu. Jeśli `pdwMappingType` jest `fmFlat`, rozmiar pliku.  
  
 `pdwMappingType`  
 [out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) wartość, która wskazuje typ mapowania. Bieżąca implementacja środowisko uruchomieniowe języka wspólnego (CLR) zawsze zwraca `fmFlat`. Inne wartości są zarezerwowane do użytku w przyszłości. Jednak należy zawsze sprawdzić zwrócona wartość ponieważ inne wartości może być włączone w przyszłych wersjach lub wersje usługi.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|Wszystkie dane wyjściowe są wypełnione.|  
|`E_INVALIDARG`|Wartości NULL został przekazany jako wartość argumentu.|  
|`COR_E_NOTSUPPORTED`|Implementacji środowiska CLR nie może dostarczyć informacji o regionie pamięci. Może się to zdarzyć w następujących sytuacjach:<br /><br /> -Zakres metadanych została otwarta z `ofWrite` lub `ofCopyMemory` flagi.<br />-Zakres metadanych został otwarty bez `ofReadOnly` flagi.<br />- [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) użyto metody można otworzyć tylko część metadane pliku.<br />-Plik nie jest plikiem przenośny plik wykonywalny (PE). **Uwaga:** te warunki są zależne od implementacji środowiska CLR i są prawdopodobnie obniżony w przyszłych wersjach środowiska CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Pamięć który `ppvData` punktów jest prawidłowy tylko tak długo, jak podstawowej zakres metadanych jest otwarty.  
  
 Aby tę metodę, aby pracować, podczas mapowania metadanych pliku na dysku w pamięci, wywołując [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metody, należy określić `ofReadOnly` flagi, a nie mogą określać `ofWrite` lub `ofCopyMemory` flagi.  
  
 Wybór typu mapowania pliku dla każdego zakresu jest specyficzne dla danego wdrożenia środowiska CLR. Nie można ustawić przez użytkownika. Bieżąca implementacja CLR zawsze zwraca `fmFlat` w `pdwMappingType`, ale ten może ulec zmianie w przyszłych wersji środowiska CLR lub w przyszłych wersjach usługi danej wersji. Zwrócone wartości należy zawsze sprawdzić `pdwMappingType`, ponieważ mają różne typy układów i przesunięcia.  
  
 Przekazywanie wartości NULL dla każdego z trzech parametrów nie jest obsługiwana. Metoda zwraca `E_INVALIDARG`, a żadne dane wyjściowe są wypełniane. Ignorowanie Typ mapowania lub rozmiar regionu może spowodować zakończenie nietypowe programu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataInfo, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 [CorFileMapping, wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
