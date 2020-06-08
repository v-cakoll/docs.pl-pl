---
title: IMetaDataImport::EnumMembersWithName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
ms.openlocfilehash: ea451bdd645d2d4dea4c5dd00408e0bc51804803
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492073"
---
# <a name="imetadataimportenummemberswithname-method"></a>IMetaDataImport::EnumMembersWithName — Metoda
Wylicza tokeny MemberDef reprezentujące elementy członkowskie określonego typu o określonej nazwie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in. out] Wskaźnik do modułu wyliczającego.  
  
 `cl`  
 podczas Token TypeDef reprezentujący typ z elementami członkowskimi do wyliczenia.  
  
 `szName`  
 podczas Nazwa elementu członkowskiego, który ogranicza zakres modułu wyliczającego.  
  
 `rMembers`  
 określoną Tablica służąca do przechowywania tokenów MemberDef.  
  
 `cMax`  
 podczas Maksymalny rozmiar `rMembers` tablicy.  
  
 `pcTokens`  
 określoną Rzeczywista liczba tokenów MemberDef zwrócona w `rMembers` .  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wylicza pola i metody, ale nie właściwości ani zdarzenia. W przeciwieństwie do [IMetaDataImport:: EnumMembers —](imetadataimport-enummembers-method.md), `EnumMembersWithName` odrzuca wszystkie tokeny pola i elementu członkowskiego, które nie mają określonej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`pomyślnie zwrócono.|  
|`S_FALSE`|Brak tokenów MemberDef do wyliczenia. W takim przypadku `pcTokens` jest równa zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
