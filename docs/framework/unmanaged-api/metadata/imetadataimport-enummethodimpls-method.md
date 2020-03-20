---
title: IMetaDataImport::EnumMethodImpls — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
ms.openlocfilehash: e766cec8fd84713e12c43cd1095650ed5b757bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175476"
---
# <a name="imetadataimportenummethodimpls-method"></a>IMetaDataImport::EnumMethodImpls — Metoda
Wylicza tokeny MethodBody i MethodDeclaration reprezentujące metody określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdToken     rMethodBody[],
   [out]     mdToken     rMethodDecl[],
   [in]      ULONG       cMax,
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, na zewnątrz] Wskaźnik do wyliczacza. Musi to być null dla pierwszego wywołania tej metody.  
  
 `td`  
 [w] A TypeDef token dla typu, którego implementacje metody do wyliczenia.  
  
 `rMethodBody`  
 [na zewnątrz] Tablica do przechowywania tokenów MethodBody.  
  
 `rMethodDecl`  
 [na zewnątrz] Tablica do przechowywania tokenów MethodDeclaration.  
  
 `cMax`  
 [w] Maksymalny rozmiar `rMethodBody` tablic `rMethodDecl` i tablic.  
  
 `pcTokens`  
 [w] Rzeczywista liczba metod `rMethodBody` zwróconych w i `rMethodDecl`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodImpls`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów metody do wyliczenia. W takim `pcTokens` przypadku wynosi zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
