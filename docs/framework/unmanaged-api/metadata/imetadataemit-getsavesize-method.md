---
title: IMetaDataEmit::GetSaveSize — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7337222f7f419c68ae21d604d1673158acca85ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777392"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize — Metoda
Szacowany rozmiar binarne zestawu i jego metadane są pobierane w bieżącym zakresie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fSave`  
 [in] Wartość [corsavesize —](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) wyliczenie, które określa, czy uzyskać dokładne lub Przybliżony rozmiar. Tylko dla trzech wartości są prawidłowe: cssAccurate, cssQuick i cssDiscardTransientCAs:  
  
- cssAccurate zwraca dokładnie Zapisz rozmiar, ale trwa dłużej do obliczenia.  
  
- cssQuick zwraca rozmiar, uzupełniona na potrzeby bezpieczeństwa, ale zajmuje mniej czasu, aby obliczyć.  
  
- informuje cssDiscardTransientCAs `GetSaveSize` , może ona zgłosić natychmiast discardable atrybutów niestandardowych.  
  
 `pdwSaveSize`  
 [out] Wskaźnik do rozmiaru który jest wymagany, aby zapisać plik.  
  
## <a name="remarks"></a>Uwagi  
 `GetSaveSize` Obliczanie miejsca wymaganego w bajtach, można zapisać zestawu i wszystkich jego metadane w bieżącym zakresie. (Po wywołaniu [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) metoda może emitować to liczba bajtów.)  
  
 Jeśli obiekt wywołujący implementuje [imaptoken —](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interfejsu (za pośrednictwem [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) lub [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` wykona dwa przebiegi za pośrednictwem metadane do optymalizacji i skompresować je. W przeciwnym razie są wykonywane nie optymalizacji.  
  
 Jeśli będzie przeprowadzana Optymalizacja, pierwszym przebiegu po prostu sortuje struktur metadanych, aby dostosować wydajność wyszukiwania w trakcie importu. Zazwyczaj ten krok powoduje przeniesienie rekordów wokół, za pomocą efekt uboczny, że tokeny zachowywane przez narzędzie do użytku w przyszłości nie są unieważniane. Metadane nie informuje obiekt wywołujący o tych zmianach token aż do po drugim — dostęp próbny, jednak. W drugim przebiegu, wykonywane są różne optymalizacje, które są przeznaczone do redukowania łącznego rozmiaru metadane, takie jak Optymalizacja odkładania (wczesne powiązania) `mdTypeRef` i `mdMemberRef` tokenów w przypadku odwołania do typu lub elementu członkowskiego, które są zadeklarowane w bieżący zakres metadanych. W tym przebiegu kolejną porcję tokenu mapowanie występuje. Po tym przebiegu aparatu metadanych powiadamia obiekt wywołujący, za pośrednictwem jego `IMapToken` interfejsu dowolnego zmienione wartości tokenu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
