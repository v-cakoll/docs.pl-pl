---
title: IMetaDataImport::EnumMembers — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175489"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers — Metoda
Wylicza tokeny MemberDef reprezentujące członków określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, na zewnątrz] Wskaźnik do wyliczacza.  
  
 `cl`  
 [w] A TypeDef token reprezentujący typ, którego elementy członkowskie mają być wyliczone.  
  
 `rMembers`  
 [na zewnątrz] Tablica używana do przechowywania tokenów MemberDef.  
  
 `cMax`  
 [w] Maksymalny rozmiar `rMembers` tablicy.  
  
 `pcTokens`  
 [na zewnątrz] Rzeczywista liczba tokenów MemberDef `rMembers`zwrócona w .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów MemberDef do wyliczenia. W takim `pcTokens` przypadku wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas wyliczania kolekcji członków dla `EnumMembers` klasy zwraca tylko elementy członkowskie (pola i metody, ale **nie** właściwości lub zdarzenia) zdefiniowane bezpośrednio w klasie. Nie zwraca żadnych elementów członkowskich, które dziedziczy klasa, nawet jeśli klasa zapewnia implementację dla tych członków dziedziczone. Aby wyliczyć odziedziczone elementy członkowskie, obiektu wywołującego należy jawnie chodzić łańcucha dziedziczenia. Należy zauważyć, że reguły dla łańcucha dziedziczenia mogą się różnić w zależności od języka lub kompilatora, który emitował oryginalne metadane.

 Właściwości i zdarzenia nie są wyliczone przez `EnumMembers`. Aby je wyliczyć, należy użyć [właściwości EnumProperties](imetadataimport-enumproperties-method.md) lub [EnumEvents](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
