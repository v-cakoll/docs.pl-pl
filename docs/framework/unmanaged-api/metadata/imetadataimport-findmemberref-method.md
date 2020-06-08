---
title: IMetaDataImport::FindMemberRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: 068014732cee91147edaec29fa0f954a741d8b5c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491667"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef — Metoda
Pobiera wskaźnik do tokenu MemberRef dla odwołania do elementu członkowskiego, który jest ujęty w określony <xref:System.Type> i który ma określoną nazwę i sygnaturę metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 podczas Token TypeRef dla klasy lub interfejsu, który obejmuje odwołanie do elementu członkowskiego do wyszukania. Jeśli ta wartość jest `mdTokenNil` , wyszukiwanie jest wykonywane dla zmiennej globalnej lub odwołania do funkcji globalnej.  
  
 `szName`  
 podczas Nazwa odwołania do elementu członkowskiego do wyszukania.  
  
 `pvSigBlob`  
 podczas Wskaźnik do binarnego podpisu metadanych odwołania do elementu członkowskiego.  
  
 `cbSigBlob`  
 podczas Rozmiar w bajtach `pvSigBlob` .  
  
 `pmr`  
 określoną Wskaźnik do zgodnego tokenu elementu MemberRef.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić składową przy użyciu jej klasy lub interfejsu ( `td` ), jej nazwy ( `szName` ) i opcjonalnie jej sygnatury ( `pvSigBlob` ).  
  
 Sygnatura przekazano do `FindMemberRef` musi być wygenerowana w bieżącym zakresie, ponieważ sygnatury są powiązane z konkretnym zakresem. Podpis może osadzić token, który identyfikuje otaczającą klasę lub typ wartości. Token jest indeksem tabeli lokalnych TypeDef. Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego zakresu i użyć tej sygnatury jako danych wejściowych `FindMemberRef` .  
  
 `FindMemberRef`znajduje tylko odwołania do elementu członkowskiego, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znaleziono dziedziczonych odwołań do członków.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
