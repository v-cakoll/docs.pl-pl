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
ms.openlocfilehash: 88b8f874400d68110fa5e8fb66ca910b8e7231e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645967"
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
  
#### <a name="parameters"></a>Parametry  
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
 Podczas wyliczania kolekcji elementów członkowskich dla klasy `EnumMembers` zwraca tylko elementy członkowskie zdefiniowane bezpośrednio w klasie. Nie zwraca żadnych elementów członkowskich, które klasa dziedziczy, nawet wtedy, gdy klasa udostępnia implementację dla tych dziedziczonych elementów członkowskich. Aby wyliczyć dziedziczone elementy członkowskie, obiekt wywołujący jawnie prowadzą użytkownika łańcuch dziedziczenia. Należy pamiętać, że zasady łańcuch dziedziczenia, mogą się różnić w zależności od języka i kompilatora, które są emitowane odpowiednich oryginalnych metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
