---
title: "IMetaDataImport::FindField — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3178d3ff3c64de5390e1150445f0c49c560aa32a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField — Metoda
Pobiera wskaźnik do FieldDef token pola, które jest ujęte przez określony <xref:System.Type> z określoną sygnaturą nazwy i metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [in] Token TypeDef dla klasy lub interfejsu, który umieszcza pole wyszukiwania. Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane na potrzeby zmiennej globalnej.  
  
 `szName`  
 [in] Nazwa pola do wyszukania.  
  
 `pvSigBlob`  
 [in] Wskaźnik do metadanych binarne podpis pola.  
  
 `cbSigBlob`  
 [in] Wyrażony w bajtach rozmiar `pvSigBlob`.  
  
 `pmb`  
 [out] Wskaźnik do dopasowania tokenie FieldDef.  
  
## <a name="remarks"></a>Uwagi  
 Określ pola przy użyciu jego otaczającej klasy lub interfejsu (`td`), jego nazwa (`szName`) i opcjonalnie jego podpis (`pvSigBlob`).  
  
 Podpis przekazany do `FindField` musi został wygenerowany w bieżącym zakresie, ponieważ podpisy są powiązane z określonego zakresu. Podpis osadzić token, który identyfikuje typ otaczający klasy lub wartości. (Token jest indeks do lokalnej tabeli TypeDef). Nie kompilacji podpisu środowiska wykonawczego poza kontekstem bieżącego zakresu i używają tego podpisu jako dane wejściowe `FindField`.  
  
 `FindField`Wyszukuje tylko pola, które zostały zdefiniowane bezpośrednio w klasy lub interfejsu; pola dziedziczonych nie zostanie znaleziona.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
