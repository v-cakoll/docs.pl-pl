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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28aa8313e7ba0c071187d0f1f6d78431b16fc005
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164804"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod — Metoda
Pobiera wskaźnik do MethodDef tokenu dla metody, która jest ujęta w określonym <xref:System.Type> i ma określoną sygnaturą nazwy i metadane.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] `mdTypeDef` Tokenu dla typu (klasę lub interfejs), który otacza elementu członkowskiego do wyszukania. Jeśli ta wartość jest `mdTokenNil`, a następnie wyszukiwanie jest wykonywane na potrzeby funkcją globalną.  
  
 `szName`  
 [in] Nazwa metody do wyszukiwania.  
  
 `pvSigBlob`  
 [in] Wskaźnik do binarnych metadanych podpis metody.  
  
 `cbSigBlob`  
 [in] Rozmiar w bajtach `pvSigBlob`.  
  
 `pmb`  
 [out] Wskaźnik do zgodnego tokenu MethodDef.  
  
## <a name="remarks"></a>Uwagi  
 Określ metody przy użyciu jego otaczającej klasy lub interfejsu (`td`), jego nazwę (`szName`) i opcjonalnie jeho signatura (`pvSigBlob`). Może istnieć wiele metod o tej samej nazwie w klasie lub interfejsie. W takim przypadku należy przekazać sygnaturę metody i nie może znaleźć unikatowego dopasowania.  
  
 Podpis jest przekazywany do `FindMethod` musi zostać wygenerowane w bieżącym zakresie ponieważ podpisy są powiązane z określonego zakresu. Podpis można osadzić token, który identyfikuje typ otaczający klasy lub wartości. Token jest to indeks w lokalnej tabeli TypeDef. Nie można tworzyć sygnatury czasu wykonywania poza kontekstem bieżącego zakresu i za ten podpis jako dane wejściowe do wprowadzania `FindMethod`.  
  
 `FindMethod` Umożliwia znalezienie tylko tych metod, które zostały zdefiniowane bezpośrednio klasę lub interfejs; nie odnajdzie metody dziedziczone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
