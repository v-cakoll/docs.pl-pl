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
ms.openlocfilehash: 22c0a317777a12294ba7a90f7af1ceeca3ad0a47
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009265"
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
 podczas Wartość wyliczenia [CorSaveSize —](corsavesize-enumeration.md) , która określa, czy ma być pobierany dokładny czy przybliżony rozmiar. Prawidłowe są tylko trzy wartości: cssAccurate, cssQuick i cssDiscardTransientCAs:  
  
- cssAccurate zwraca dokładny rozmiar zapisu, ale trwa dłużej.  
  
- cssQuick zwraca rozmiar, uzupełniony pod kątem bezpieczeństwa, ale zajmuje mniej czasu na obliczenia.  
  
- cssDiscardTransientCAs informuje `GetSaveSize` o tym, że może zgłosić atrybuty niestandardowe odrzucone.  
  
 `pdwSaveSize`  
 określoną Wskaźnik do rozmiaru, który jest wymagany do zapisania pliku.  
  
## <a name="remarks"></a>Uwagi  
 `GetSaveSize`oblicza wymagane miejsce, w bajtach, do zapisania zestawu i wszystkich jego metadanych w bieżącym zakresie. (Wywołanie metody [IMetaDataEmit:: SaveToStream —](imetadataemit-savetostream-method.md) emituje tę liczbę bajtów).  
  
 Jeśli obiekt wywołujący implementuje interfejs [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) (za pośrednictwem [IMetaDataEmit:: sethandleer](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) lub [IMetaDataEmit:: Merge](imetadataemit-merge-method.md)), `GetSaveSize` program wykona dwa przekazanie metadanych w celu optymalizacji i skompresowania. W przeciwnym razie optymalizacje nie są wykonywane.  
  
 W przypadku przeprowadzania optymalizacji pierwsze przejście po prostu sortuje struktury metadanych w celu dostosowania wydajności wyszukiwania w czasie importu. Ten krok zazwyczaj skutkuje przenoszeniem rekordów, a efektem ubocznym, które tokeny są przechowywane przez narzędzie do przyszłego odwołania, są unieważnione. Metadane nie informują o tym, że wywołujący te zmiany tokenu są jednak do momentu drugiego przejścia. W drugim przebiegu są wykonywane różne optymalizacje, które mają na celu zmniejszenie całkowitego rozmiaru metadanych, takich jak optymalizacja (wczesne wiązanie) `mdTypeRef` i `mdMemberRef` tokeny, gdy odwołanie dotyczy typu lub elementu członkowskiego, który jest zadeklarowany w bieżącym zakresie metadanych. W tym przebiegu występuje inne mapowanie tokenu. Po tym przejściu aparat metadanych powiadamia obiekt wywołujący `IMapToken` o wszystkich zmienionych wartościach tokenu za pomocą interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
