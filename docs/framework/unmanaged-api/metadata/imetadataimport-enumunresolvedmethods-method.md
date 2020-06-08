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
ms.openlocfilehash: c991c0af845bc6825db6b3bf258fe0809d5db804
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503702"
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
 podczas Maksymalny rozmiar `rMethods` tablicy.  
  
 `pcTokens`  
 określoną Liczba tokenów MemberDef zwróconych w `rMethods` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods`pomyślnie zwrócono.|  
|`S_FALSE`|Brak tokenów do wyliczenia. W takim przypadku `pcTokens` jest równa zero.|  
  
## <a name="remarks"></a>Uwagi  
 Nierozpoznana Metoda jest taka, która została zadeklarowana, ale nie została zaimplementowana. Metoda jest uwzględniona w wyliczeniu, jeśli metoda jest oznaczona `miForwardRef` i `mdPinvokeImpl` albo `miRuntime` jest ustawiona na zero. Innymi słowy, Nierozpoznana Metoda jest metodą klasy, która jest oznaczona, `miForwardRef` ale nie jest zaimplementowana w kodzie niezarządzanym (osiąganym przez PInvoke) ani zaimplementowana wewnętrznie przez samo środowisko uruchomieniowe  
  
 Wyliczenie wyklucza wszystkie metody, które są zdefiniowane w zakresie modułu (Globals) lub w klasach interfejsów lub klas abstrakcyjnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
