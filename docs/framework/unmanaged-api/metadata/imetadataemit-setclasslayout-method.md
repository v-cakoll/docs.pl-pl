---
title: IMetaDataEmit::SetClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177562"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout — Metoda
Kończy układ pól dla klasy, która została zdefiniowana przez wcześniejsze wywołanie [metody DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [w] Token, `mdTypeDef` który określa klasę, która ma zostać rozmieszczona.  
  
 `dwPackSize`  
 [w] Rozmiar opakowania: 1, 2, 4, 8 lub 16 bajtów. Rozmiar opakowania to liczba bajtów między przyległymi polami.  
  
 `rFieldOffsets`  
 [w] Tablica [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktur, z których każda określa pole klasy i przesunięcie pola w klasie. Zakończ tablicę `mdTokenNil`za pomocą pliku .  
  
 `ulClassSize`  
 [w] Rozmiar w bajtach klasy.  
  
## <a name="remarks"></a>Uwagi  
 Klasa jest początkowo zdefiniowana przez [wywołanie metody IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) i określenie jednego z trzech układów dla pól klasy: automatycznego, sekwencyjnego lub jawnego. Zwykle można użyć układu automatycznego i niech środowisko uruchomieniowe wybrać najlepszy sposób rozmieszczenia pól.  
  
 Jednak może chcesz pola określone zgodnie z układem, który używa kodu niezarządzanego. W takim przypadku wybierz układ sekwencyjny lub `SetClassLayout` jawny i wywołaj, aby ukończyć układ pól:  
  
- Układ sekwencyjny: Określ rozmiar opakowania. Pole jest wyrównane zgodnie z jego naturalnym rozmiarem lub rozmiarem opakowania, w zależności od tego, co skutkuje mniejszym przesunięciem pola. Ustaw `rFieldOffsets` `ulClassSize` i na zero.  
  
- Jawny układ: Określ przesunięcie każdego pola lub określ rozmiar klasy i rozmiar opakowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
