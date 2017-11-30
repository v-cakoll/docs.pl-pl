---
title: "IMetaDataEmit::SetClassLayout — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a68d94cbea408bee90b117965f83f760ba7ea5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout — Metoda
Kończy układ pól dla klasy, która została zdefiniowana przez poprzednie wywołanie [DefineTypeDef — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [in] `mdTypeDef` Token, który określa klasę, do którego układ określa się.  
  
 `dwPackSize`  
 [in] Rozmiar pakowania: 1, 2, 4, 8 lub 16 bajtów. Rozmiar pakowania jest to liczba bajtów między polami sąsiadujących ze sobą.  
  
 `rFieldOffsets`  
 [in] Tablica [cor_field_offset —](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z których każdy określa przesunięcie pola klasy i należące do klasy. Przerwanie tablicy o `mdTokenNil`.  
  
 `ulClassSize`  
 [in] Rozmiar w bajtach klasy.  
  
## <a name="remarks"></a>Uwagi  
 Klasa jest wstępnie zdefiniowana przez wywołanie metody [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) — metoda i określania jednego z trzech układów pola klasy: automatyczna, sekwencyjny lub jawny. Możesz zazwyczaj używa automatyczny układ i let środowiska uruchomieniowego, wybierz najlepszy sposób, aby określić układ pól.  
  
 Jednak może być pola, którego układ określa się zgodnie z rozmieszczeniem, który używa kodu niezarządzanego. W takim przypadku wybierz układ sekwencyjny lub jawny i wywołanie `SetClassLayout` przeprowadzenie układ pól:  
  
-   Układ sekwencyjny: Określ rozmiar pakowania. Pole jest wyrównany zgodnie z jego rozmiar fizyczne lub rozmiar pakowania, niezależnie od wyników w mniejszych przesunięcie pola. Ustaw `rFieldOffsets` i `ulClassSize` od zera.  
  
-   Układ jawny: Określ przesunięcie każdego pola lub określić klasy i rozmiar pakowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
