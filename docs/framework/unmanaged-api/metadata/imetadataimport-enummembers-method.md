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
ms.openlocfilehash: acb772a64c8f13405f2836bb5f4f308986dce414
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447654"
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
 podczas Maksymalny rozmiar tablicy `rMembers`.  
  
 `pcTokens`  
 określoną Rzeczywista liczba tokenów MemberDef zwróconych w `rMembers`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` pomyślnie zwrócone.|  
|`S_FALSE`|Brak tokenów MemberDef do wyliczenia. W takim przypadku `pcTokens` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas wyliczania kolekcji elementów członkowskich klasy `EnumMembers` zwraca tylko elementy członkowskie (pola i metody, ale **nie** właściwości ani zdarzenia) zdefiniowane bezpośrednio w klasie. Nie zwraca żadnych elementów członkowskich, które dziedziczy Klasa, nawet jeśli Klasa dostarcza implementację dla tych dziedziczonych elementów członkowskich. Aby wyliczyć dziedziczone elementy członkowskie, obiekt wywołujący musi jawnie przeprowadzić łańcuch dziedziczenia. Należy zauważyć, że reguły dla łańcucha dziedziczenia mogą się różnić w zależności od języka lub kompilatora, który emituje oryginalne metadane.
 
 Właściwości i zdarzenia nie są wyliczane przez `EnumMembers`. Aby wyliczyć te, użyj [EnumProperties —](imetadataimport-enumproperties-method.md) lub [EnumEvents —](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
