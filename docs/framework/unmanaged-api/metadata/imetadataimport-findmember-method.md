---
title: IMetaDataImport::FindMember — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caec760cea52cb14d3fdb5d4cf0b59adcae5633b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782516"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember — Metoda
Pobiera wskaźnik do MemberDef tokenu dla pola lub metody, która jest ujęta w określonym <xref:System.Type> i ma określoną sygnaturą nazwy i metadane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] Token element TypeDef dla klasy lub interfejsu, który otacza elementu członkowskiego do wyszukania. Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane dla zmiennej globalnej lub globalnego funkcji.  
  
 `szName`  
 [in] Nazwa elementu członkowskiego do wyszukania.  
  
 `pvSigBlob`  
 [in] Wskaźnik do podpisu binarne metadanych elementu członkowskiego.  
  
 `cbSigBlob`  
 [in] Rozmiar w bajtach `pvSigBlob`.  
  
 `pmb`  
 [out] Wskaźnik do zgodnego tokenu MemberDef.  
  
## <a name="remarks"></a>Uwagi  
 Określ element członkowski przy użyciu jego otaczającej klasy lub interfejsu (`td`), jego nazwę (`szName`) i opcjonalnie jeho signatura (`pvSigBlob`). Może istnieć wiele składowych o tej samej nazwie w klasie lub interfejsie. W takim przypadku należy przekazać podpisu elementu członkowskiego, aby znaleźć unikatowego dopasowania.  
  
 Podpis jest przekazywany do `FindMember` musi zostać wygenerowane w bieżącym zakresie ponieważ podpisy są powiązane z określonego zakresu. Podpis można osadzić token, który identyfikuje typ otaczający klasy lub wartości. Token jest to indeks w lokalnej tabeli TypeDef. Nie można tworzyć sygnatury czasu wykonywania poza kontekstem bieżącego zakresu i za ten podpis jako dane wejściowe do wprowadzania `FindMember`.  
  
 `FindMember` Umożliwia znalezienie tylko elementy członkowskie, które zostały zdefiniowane bezpośrednio w klasę lub interfejs; dziedziczone elementy członkowskie nie zostanie znaleziona.  
  
> [!NOTE]
>  `FindMember` jest metodą pomocnika. Wywołuje [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Jeśli jest to wywołanie nie znajdzie dopasowania `FindMember` następnie wywołuje [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
