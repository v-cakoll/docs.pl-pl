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
ms.openlocfilehash: 125a63638a41707b8eed918253cb1f93abb907eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434335"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize — Metoda
Pobiera Szacowany rozmiar binarny zestawu i jego metadanych w bieżącym zakresie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fSave`  
 podczas Wartość wyliczenia [CorSaveSize —](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) , która określa, czy ma być pobierany dokładny czy przybliżony rozmiar. Prawidłowe są tylko trzy wartości: cssAccurate, cssQuick i cssDiscardTransientCAs:  
  
- cssAccurate zwraca dokładny rozmiar zapisu, ale trwa dłużej.  
  
- cssQuick zwraca rozmiar, uzupełniony pod kątem bezpieczeństwa, ale zajmuje mniej czasu na obliczenia.  
  
- cssDiscardTransientCAs informuje `GetSaveSize`, że może zgłosić atrybuty niestandardowe odrzucane.  
  
 `pdwSaveSize`  
 określoną Wskaźnik do rozmiaru, który jest wymagany do zapisania pliku.  
  
## <a name="remarks"></a>Uwagi  
 `GetSaveSize` oblicza wymaganą ilość miejsca (w bajtach), aby zapisać zestaw i wszystkie jego metadane w bieżącym zakresie. (Wywołanie metody [IMetaDataEmit:: SaveToStream —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) emituje tę liczbę bajtów).  
  
 Jeśli obiekt wywołujący implementuje interfejs [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) (za pośrednictwem [IMetaDataEmit:: sethandleer](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) lub [IMetaDataEmit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` wykona dwa przekazanie metadanych w celu optymalizacji i skompresowania. W przeciwnym razie optymalizacje nie są wykonywane.  
  
 W przypadku przeprowadzania optymalizacji pierwsze przejście po prostu sortuje struktury metadanych w celu dostosowania wydajności wyszukiwania w czasie importu. Ten krok zazwyczaj skutkuje przenoszeniem rekordów, a efektem ubocznym, które tokeny są przechowywane przez narzędzie do przyszłego odwołania, są unieważnione. Metadane nie informują o tym, że wywołujący te zmiany tokenu są jednak do momentu drugiego przejścia. W drugim przebiegu są wykonywane różne optymalizacje, które mają na celu zmniejszenie całkowitego rozmiaru metadanych, takich jak optymalizacja (wczesne wiązanie) `mdTypeRef` i `mdMemberRef` tokeny, gdy odwołanie dotyczy typu lub elementu członkowskiego, który jest zadeklarowany w bieżącym zakresie metadanych. W tym przebiegu występuje inne mapowanie tokenu. Po tym przejściu aparat metadanych powiadamia obiekt wywołujący za pomocą interfejsu `IMapToken` o wszelkich zmienionych wartościach tokenów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
