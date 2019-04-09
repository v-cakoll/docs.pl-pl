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
ms.openlocfilehash: 4c6a9473a698e4635c8b5cc9fb58963334dfd65e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081796"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping — Metoda
Pobiera region pamięci zamapowanego pliku, a Typ mapowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppvData`  
 [out] Wskaźnik do początku zamapowanego pliku.  
  
 `pcbData`  
 [out] Rozmiar mapowanego obszaru. Jeśli `pdwMappingType` jest `fmFlat`, jest to rozmiar pliku.  
  
 `pdwMappingType`  
 [out] A [corfilemapping —](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) wartość, która wskazuje typ mapowania. Bieżąca implementacja środowisko uruchomieniowe języka wspólnego (CLR) zawsze zwraca `fmFlat`. Inne wartości są zarezerwowane do użytku w przyszłości. Jednak musisz zawsze sprawdzić, zwrócona wartość, ponieważ inne wartości może być włączone w przyszłych wersjach lub usług wydań.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|Wszystkie dane wyjściowe są wypełnione.|  
|`E_INVALIDARG`|Wartość NULL została przekazana jako wartość argumentu.|  
|`COR_E_NOTSUPPORTED`|Implementacji środowiska CLR nie może dostarczyć informacji na temat regionu pamięci. Może się to zdarzyć z następujących powodów:<br /><br /> Zakres metadanych zostało otwarte z `ofWrite` lub `ofCopyMemory` flagi.<br />Zakres metadanych został otwarty bez `ofReadOnly` flagi.<br />[IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metoda użyty do otwarcia tylko część metadanych pliku.<br />-Plik nie jest plikiem przenośny plik wykonywalny (PE). **Uwaga:**  Te warunki są zależne od implementacji środowiska CLR i prawdopodobnie należy obniżyć poziom w przyszłych wersjach środowiska CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Pamięć, `ppvData` wskazuje jest prawidłowy tylko tak długo, jak podstawowy zakres metadanych jest otwarty.  
  
 W kolejności dla tej metody do pracy, kiedy mapujesz metadanych pliku na dysku do pamięci poprzez wywołanie [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metody, należy określić `ofReadOnly` flagę i nie mogą określać `ofWrite` lub `ofCopyMemory` flagi.  
  
 Wybór typu mapowanie pliku dla każdego zakresu jest specyficzne dla danego wdrożenia środowiska CLR. Nie można ustawić przez użytkownika. Bieżąca implementacja CLR zawsze zwraca `fmFlat` w `pdwMappingType`, ale mogą one zmienić w przyszłych wersji środowiska CLR, lub w przyszłych wydaniach usługa danej wersji. Należy zawsze sprawdzić zwracanej wartości `pdwMappingType`, ponieważ różne typy mają różne układy i przesunięcia.  
  
 Przekazanie wartości NULL dla każdego z trzech parametrów nie jest obsługiwane. Metoda ta zwraca `E_INVALIDARG`, a żadne dane wyjściowe są wypełniane. Ignorowanie typu mapowania lub rozmiar obszaru może spowodować Nienormalne zakończenie programu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataInfo — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping — Wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
