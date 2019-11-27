---
title: IMetaDataImport::EnumUnresolvedMethods — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: ff9827174e43fd62f3a995e9f477c6fff66b227a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449954"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a>IMetaDataImport::EnumUnresolvedMethods — Metoda
Wylicza tokeny MemberDef reprezentujące nierozpoznane metody w bieżącym zakresie metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in. out] Wskaźnik do modułu wyliczającego. Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.  
  
 `rMethods`  
 określoną Tablica służąca do przechowywania tokenów MemberDef.  
  
 `cMax`  
 podczas Maksymalny rozmiar tablicy `rMethods`.  
  
 `pcTokens`  
 określoną Liczba tokenów MemberDef zwróconych w `rMethods`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods` pomyślnie zwrócone.|  
|`S_FALSE`|Brak tokenów do wyliczenia. W takim przypadku `pcTokens` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Nierozpoznana Metoda jest taka, która została zadeklarowana, ale nie została zaimplementowana. Metoda jest uwzględniona w wyliczeniu, jeśli metoda jest oznaczona `miForwardRef` i `mdPinvokeImpl` albo `miRuntime` jest ustawiona na zero. Innymi słowy, Nierozpoznana Metoda jest metodą klasy, która jest oznaczona `miForwardRef`, ale która nie jest zaimplementowana w kodzie niezarządzanym (osiągane za pośrednictwem PInvoke) ani nie została zaimplementowana wewnętrznie przez samo środowisko uruchomieniowe  
  
 Wyliczenie wyklucza wszystkie metody, które są zdefiniowane w zakresie modułu (Globals) lub w klasach interfejsów lub klas abstrakcyjnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
