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
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177283"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember — Metoda
Pobiera wskaźnik do MemberDef token dla pola lub metody, <xref:System.Type> która jest ujęta przez określony i który ma określoną nazwę i podpis metadanych.  
  
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
 [w] TypeDef token dla klasy lub interfejsu, który otacza element członkowski do wyszukania. Jeśli ta `mdTokenNil`wartość jest , wyszukiwanie jest wykonywane dla zmiennej globalnej lub funkcji globalnej.  
  
 `szName`  
 [w] Nazwa członka do wyszukania.  
  
 `pvSigBlob`  
 [w] Wskaźnik do podpisu binarnych metadanych członka.  
  
 `cbSigBlob`  
 [w] Rozmiar w bajtach . `pvSigBlob`  
  
 `pmb`  
 [na zewnątrz] Wskaźnik do pasującego tokenu MemberDef.  
  
## <a name="remarks"></a>Uwagi  
 Element członkowski można określić za`td`pomocą otaczającej`szName`go klasy lub`pvSigBlob`interfejsu ( ), jego nazwy ( i opcjonalnie jego podpisu ( ). Może istnieć wiele elementów członkowskich o tej samej nazwie w klasie lub interfejsie. W takim przypadku przekaż podpis członka, aby znaleźć unikatowe dopasowanie.  
  
 Podpis przekazany `FindMember` do musi zostały wygenerowane w bieżącym zakresie, ponieważ podpisy są powiązane z określonym zakresem. Podpis można osadzić token, który identyfikuje otaczającą klasę lub typ wartości. Token jest indeksem do lokalnej tabeli TypeDef. Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego zakresu `FindMember`i użyć tego podpisu jako danych wejściowych do .  
  
 `FindMember`znajduje tylko elementy członkowskie, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znajduje odziedziczonych członków.  
  
> [!NOTE]
> `FindMember`jest metodą pomocniczą. Wywołuje [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); jeśli to wywołanie nie `FindMember` znajdzie dopasowania, wywoła [iMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
