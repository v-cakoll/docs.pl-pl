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
ms.openlocfilehash: 7410f91a853f3a677a105dc2e12a86d723c9fad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177320"
---
# <a name="imetadataimportenummemberswithname-method"></a>IMetaDataImport::EnumMembersWithName — Metoda
Wylicza tokeny MemberDef reprezentujące członków określonego typu o określonej nazwie.  
  
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
 [w, na zewnątrz] Wskaźnik do wyliczacza.  
  
 `cl`  
 [w] Token TypeDef reprezentujący typ z członkami do wyliczenia.  
  
 `szName`  
 [w] Nazwa elementu członkowskiego, która ogranicza zakres wyliczacza.  
  
 `rMembers`  
 [na zewnątrz] Tablica używana do przechowywania tokenów MemberDef.  
  
 `cMax`  
 [w] Maksymalny rozmiar `rMembers` tablicy.  
  
 `pcTokens`  
 [na zewnątrz] Rzeczywista liczba tokenów MemberDef `rMembers`zwrócona w .  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wylicza pola i metody, ale nie właściwości lub zdarzenia. W przeciwieństwie do [IMetaDataImport::EnumMembers,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md) `EnumMembersWithName` odrzuca wszystkie tokeny pól i elementów członkowskich, które nie mają określonej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów MemberDef do wyliczenia. W takim `pcTokens` przypadku wynosi zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
