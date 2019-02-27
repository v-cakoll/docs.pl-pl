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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de4bf2cf647682062fbacb4484ffae905d1b7995
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835372"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers — Metoda
Wylicza tokenów MemberDef reprezentujących elementy określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [out w] Wskaźnik do modułu wyliczającego.  
  
 `cl`  
 [in] TypeDef token reprezentujący typ, której członkami są do wyliczenia.  
  
 `rMembers`  
 [out] Tablica, używane do przechowywania tokenów MemberDef.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rMembers` tablicy.  
  
 `pcTokens`  
 [out] Rzeczywista liczba tokenów MemberDef zwracane w `rMembers`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` pomyślnie zwrócił.|  
|`S_FALSE`|Nie ma żadnych tokeny MemberDef do wyliczenia. W takim przypadku `pcTokens` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas wyliczania kolekcji elementów członkowskich klasy, `EnumMembers` zwraca tylko elementy członkowskie (pola i metody, ale **nie** właściwości lub zdarzenia) zdefiniowany bezpośrednio na klasie. Nie zwraca żadnych elementów członkowskich, które klasa dziedziczy, nawet wtedy, gdy klasa udostępnia implementację dla tych dziedziczonych elementów członkowskich. Aby wyliczyć dziedziczone elementy członkowskie, obiekt wywołujący jawnie prowadzą użytkownika łańcuch dziedziczenia. Należy pamiętać, że zasady łańcuch dziedziczenia, mogą się różnić w zależności od języka i kompilatora, które są emitowane odpowiednich oryginalnych metadanych.
 
 Właściwości i zdarzenia nie są wyliczane przez `EnumMembers`. Aby wyliczyć te, należy użyć [enumproperties —](imetadataimport-enumproperties-method.md) lub [enumevents —](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
