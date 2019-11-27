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
ms.openlocfilehash: 7ceae6f7713ab0eb1feff550838325df0ea52de2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447916"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 — Interfejs
Rozszerza interfejs [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) przede wszystkim, aby zapewnić możliwość pracy z typami ogólnymi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DefineGenericParam, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|Tworzy definicję parametru typu ogólnego i pobiera token do tego parametru typu ogólnego.|  
|[DefineMethodSpec, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|Tworzy wystąpienie ogólne metody i pobiera token do definicji.|  
|[GetDeltaSaveSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|Pobiera wartość wskazującą różnicę rozmiaru danych, które są wymagane do wyrażenia zmian w bieżącej sesji Edit-and-Continue.|  
|[ResetENCLog, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|Resetuje dziennik Edytuj i Kontynuuj i uruchamia nową sesję.|  
|[SaveDelta, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|Zapisuje zmiany z bieżącej sesji Edit-and-Continue do określonego pliku.|  
|[SaveDeltaToMemory, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|Zapisuje zmiany z bieżącej sesji edycji i kontynuowania w pamięci.|  
|[SaveDeltaToStream, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|Zapisuje zmiany z bieżącej sesji Edit-and-Continue do określonego strumienia.|  
|[SetGenericParamProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|Ustawia wartości właściwości dla definicji parametru generycznego, do której odwołuje się określony token.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
