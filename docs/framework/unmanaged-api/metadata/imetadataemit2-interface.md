---
title: IMetaDataEmit2 — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87b5b60d75d5d28e100ec75192d0cacf51765927
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042976"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 — Interfejs
Rozszerza [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interfejsu głównie w celu zapewnienia możliwość współpracy z typów ogólnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DefineGenericParam, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|Tworzy definicję dla parametru typu ogólnego, a następnie pobiera tokenu służącego do tego parametru typu ogólnego.|  
|[DefineMethodSpec, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|Tworzy wystąpienia ogólnego metody, a następnie pobiera token do definicji.|  
|[GetDeltaSaveSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|Pobiera wartość wskazującą, różnica w rozmiarze danych, który jest wymagany do express zmian dla bieżącej sesji edit-and-continue.|  
|[ResetENCLog, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|Resetuje edit-and-continue dziennika i uruchamia nową sesję.|  
|[SaveDelta, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|Zapisuje zmiany z bieżącej sesji Edytuj i Kontynuuj do określonego pliku.|  
|[SaveDeltaToMemory, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|Zapisuje zmiany z bieżącej sesji edit-and-continue pamięci.|  
|[SaveDeltaToStream, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|Zapisuje zmiany z bieżącej sesji Edytuj i Kontynuuj do określonego strumienia.|  
|[SetGenericParamProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|Ustawia wartości właściwości dla definicji parametru ogólnego odwołuje się określony token.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
