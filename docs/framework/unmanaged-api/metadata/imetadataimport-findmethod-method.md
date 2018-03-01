---
title: "IMetaDataImport::FindMethod — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e59cc440ba004545c31d6b25d36cca4fdfb58899
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod — Metoda
Pobiera wskaźnik do elementu MethodDef token metodę, która jest zawarta w określonym <xref:System.Type> z określoną sygnaturą nazwy i metadanych.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [in] `mdTypeDef` Tokenu dla typu (klasy lub interfejsu) ograniczający element członkowski do wyszukania. Jeśli ta wartość jest `mdTokenNil`, a następnie wyszukiwanie jest wykonywane na potrzeby funkcji globalnej.  
  
 `szName`  
 [in] Nazwa metody do wyszukiwania.  
  
 `pvSigBlob`  
 [in] Wskaźnik do metadanych binarne sygnatury metody.  
  
 `cbSigBlob`  
 [in] Wyrażony w bajtach rozmiar `pvSigBlob`.  
  
 `pmb`  
 [out] Wskaźnik do dopasowania tokenu MethodDef.  
  
## <a name="remarks"></a>Uwagi  
 Określ metodę, za pomocą jego otaczającej klasy lub interfejsu (`td`), jego nazwa (`szName`) i opcjonalnie jego podpis (`pvSigBlob`). Może istnieć wiele metod o tej samej nazwie w klasie lub interfejs. W takim przypadku należy przekazać podpis metody można znaleźć unikatowego dopasowania.  
  
 Podpis przekazany do `FindMethod` musi został wygenerowany w bieżącym zakresie, ponieważ podpisy są powiązane z określonego zakresu. Podpis osadzić token, który identyfikuje typ otaczający klasy lub wartości. Token jest indeks do lokalnej tabeli TypeDef. Nie można skompilować podpisu środowiska wykonawczego poza kontekstem bieżącego zakresu i używania jako danych wejściowych do danych wejściowych do tego podpisu `FindMethod`.  
  
 `FindMethod`znajduje tylko metody, które zostały zdefiniowane bezpośrednio w klasy lub interfejsu; nie odnajdzie dziedziczonej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.MethodInfo>  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
