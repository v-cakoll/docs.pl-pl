---
title: "IMetaDataImport::EnumMethodImpls — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3350fb4513604a0edc47cbf47e257648ff0d75a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethodimpls-method"></a>IMetaDataImport::EnumMethodImpls — Metoda
Wylicza MethodBody i MethodDeclaration tokeny reprezentujący metody określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, out] Wskaźnik do modułu wyliczającego. Musi to być wartość NULL dla pierwsze wywołanie tej metody.  
  
 `td`  
 [in] Element TypeDef token dla typu którego implementacje metod do wyliczenia.  
  
 `rMethodBody`  
 [out] Tablica do przechowywania tokenów MethodBody.  
  
 `rMethodDecl`  
 [out] Tablica do przechowywania tokenów MethodDeclaration.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rMethodBody` i `rMethodDecl` tablic.  
  
 `pcTokens`  
 [in] Rzeczywista liczba metod zwracane w `rMethodBody` i `rMethodDecl`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodImpls`zwrócona pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów — metoda wyliczania. W takim przypadku `pcTokens` wynosi zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
