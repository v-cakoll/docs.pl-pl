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
ms.openlocfilehash: 5214298c6ad9594548ab45ed583cb5b14ce1f30d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441764"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout — Metoda
Uzupełnia układ pól dla klasy, która została zdefiniowana przez poprzednie wywołanie [metody DefineTypeDef —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
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
 podczas Token `mdTypeDef` określający klasę, która ma zostać ustanowiona.  
  
 `dwPackSize`  
 podczas Rozmiar pakowania: 1, 2, 4, 8 lub 16 bajtów. Rozmiar pakowania to liczba bajtów między sąsiednimi polami.  
  
 `rFieldOffsets`  
 podczas Tablica struktur [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) , z których każdy określa pole klasy i przesunięcie pola w klasie. Przerwij tablicę, używając `mdTokenNil`.  
  
 `ulClassSize`  
 podczas Rozmiar klasy w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 Klasa jest początkowo definiowana przez wywołanie metody [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) i określenie jednego z trzech układów dla pól klasy: automatyczne, sekwencyjne lub jawne. Zwykle należy używać automatycznego układu i pozwolić, aby środowisko uruchomieniowe było najlepszym sposobem ułożenia pól.  
  
 Jednakże można chcieć, aby pola zostały określone zgodnie z rozmieszczeniem, które jest używane w kodzie niezarządzanym. W takim przypadku wybierz Układ sekwencyjny lub jawny i Wywołaj `SetClassLayout`, aby zakończyć układ pól:  
  
- Układ sekwencyjny: Określ rozmiar pakowania. Pole jest wyrównane do rozmiaru naturalnego lub rozmiaru pakowania, w zależności od tego, czy jest to mniejsze przesunięcie pola. Ustaw `rFieldOffsets` i `ulClassSize` na zero.  
  
- Układ jawny: Określ przesunięcie każdego pola lub Określ rozmiar klasy oraz rozmiar pakowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
