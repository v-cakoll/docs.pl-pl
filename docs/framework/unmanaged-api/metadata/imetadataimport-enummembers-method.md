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
ms.openlocfilehash: cc3bc5140da0634b5172f6253de3de37bff487f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492039"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers — Metoda
Wylicza tokeny MemberDef reprezentujące składowe określonego typu.  
  
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
 [in. out] Wskaźnik do modułu wyliczającego.  
  
 `cl`  
 podczas Token TypeDef reprezentujący typ, którego składowe mają zostać wyliczone.  
  
 `rMembers`  
 określoną Tablica użyta do przechowywania tokenów MemberDef.  
  
 `cMax`  
 podczas Maksymalny rozmiar `rMembers` tablicy.  
  
 `pcTokens`  
 określoną Rzeczywista liczba tokenów MemberDef zwrócona w `rMembers` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers`pomyślnie zwrócono.|  
|`S_FALSE`|Brak tokenów MemberDef do wyliczenia. W takim przypadku `pcTokens` jest równa zero.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas wyliczania kolekcji elementów członkowskich klasy `EnumMembers` zwraca tylko elementy członkowskie (pola i metody, ale **nie** właściwości ani zdarzenia) zdefiniowane bezpośrednio w klasie. Nie zwraca żadnych elementów członkowskich, które dziedziczy Klasa, nawet jeśli Klasa dostarcza implementację dla tych dziedziczonych elementów członkowskich. Aby wyliczyć dziedziczone elementy członkowskie, obiekt wywołujący musi jawnie przeprowadzić łańcuch dziedziczenia. Należy zauważyć, że reguły dla łańcucha dziedziczenia mogą się różnić w zależności od języka lub kompilatora, który emituje oryginalne metadane.

 Właściwości i zdarzenia nie są wyliczane przez `EnumMembers` . Aby wyliczyć te, użyj [EnumProperties —](imetadataimport-enumproperties-method.md) lub [EnumEvents —](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
