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
ms.openlocfilehash: fce4f3875fbdb110134d6b7f684eff40821f6bdd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503682"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember — Metoda
Pobiera wskaźnik do tokenu MemberDef dla pola lub metody, która jest ujęta w określony <xref:System.Type> i który ma określoną nazwę i sygnaturę metadanych.  
  
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
 podczas Token TypeDef dla klasy lub interfejsu, który obejmuje element członkowski do wyszukania. Jeśli ta wartość jest `mdTokenNil` , wyszukiwanie jest wykonywane dla zmiennej globalnej lub funkcji globalnej.  
  
 `szName`  
 podczas Nazwa elementu członkowskiego do wyszukania.  
  
 `pvSigBlob`  
 podczas Wskaźnik do binarnego podpisu metadanych elementu członkowskiego.  
  
 `cbSigBlob`  
 podczas Rozmiar w bajtach `pvSigBlob` .  
  
 `pmb`  
 określoną Wskaźnik do zgodnego tokenu MemberDef.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić składową przy użyciu jej klasy lub interfejsu ( `td` ), jej nazwy ( `szName` ) i opcjonalnie jej sygnatury ( `pvSigBlob` ). Może istnieć wiele elementów członkowskich o tej samej nazwie w klasie lub interfejsie. W takim przypadku Przekaż podpis elementu członkowskiego, aby znaleźć unikatowe dopasowanie.  
  
 Sygnatura przekazano do `FindMember` musi być wygenerowana w bieżącym zakresie, ponieważ sygnatury są powiązane z konkretnym zakresem. Podpis może osadzić token, który identyfikuje otaczającą klasę lub typ wartości. Token jest indeksem tabeli lokalnych TypeDef. Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego zakresu i użyć tej sygnatury jako danych wejściowych do `FindMember` .  
  
 `FindMember`znajduje tylko elementy członkowskie, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znajduje dziedziczonych elementów członkowskich.  
  
> [!NOTE]
> `FindMember`jest metodą pomocnika. Wywołuje [IMetaDataImport:: FindMethod —](imetadataimport-findmethod-method.md); Jeśli to wywołanie nie znajdzie dopasowania, `FindMember` wówczas wywołuje [IMetaDataImport:: FindField —](imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
