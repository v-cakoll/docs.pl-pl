---
title: IMetaDataImport::FindMethod — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177248"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod — Metoda
Pobiera wskaźnik do MethodDef token dla metody, która <xref:System.Type> jest ujęta przez określony i który ma określoną nazwę i podpis metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [w] Token `mdTypeDef` dla typu (klasy lub interfejsu), który otacza element członkowski do wyszukania. Jeśli ta `mdTokenNil`wartość jest , a następnie wyszukiwanie jest wykonywane dla funkcji globalnej.  
  
 `szName`  
 [w] Nazwa metody wyszukiwania.  
  
 `pvSigBlob`  
 [w] Wskaźnik do podpisu binarnych metadanych metody.  
  
 `cbSigBlob`  
 [w] Rozmiar w bajtach . `pvSigBlob`  
  
 `pmb`  
 [na zewnątrz] Wskaźnik do pasującego tokenu MethodDef.  
  
## <a name="remarks"></a>Uwagi  
 Metodę można określić przy użyciu otaczającej jej klasy lub interfejsu (`td`), jej nazwy (`szName`i opcjonalnie jej podpisu (`pvSigBlob`). Może istnieć wiele metod o tej samej nazwie w klasie lub interfejsie. W takim przypadku należy przekazać podpis metody, aby znaleźć unikatowe dopasowanie.  
  
 Podpis przekazany `FindMethod` do musi zostały wygenerowane w bieżącym zakresie, ponieważ podpisy są powiązane z określonym zakresem. Podpis można osadzić token, który identyfikuje otaczającą klasę lub typ wartości. Token jest indeksem do lokalnej tabeli TypeDef. Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego zakresu `FindMethod`i użyć tego podpisu jako danych wejściowych do .  
  
 `FindMethod`znajduje tylko metody, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znajduje metod dziedziczonych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
