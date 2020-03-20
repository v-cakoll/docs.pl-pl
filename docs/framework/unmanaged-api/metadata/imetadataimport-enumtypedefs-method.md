---
title: IMetaDataImport::EnumTypeDefs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 2d6e86a7f5a93b900e79907f8ee0762869d7f737
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177296"
---
# <a name="imetadataimportenumtypedefs-method"></a>IMetaDataImport::EnumTypeDefs — Metoda
Wylicza tokeny TypeDef reprezentujące wszystkie typy w bieżącym zakresie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [na zewnątrz] Wskaźnik do nowego wyliczacza. Musi to być null dla pierwszego wywołania tej metody.  
  
 `rTypeDefs`  
 [w] Tablica używana do przechowywania tokenów TypeDef.  
  
 `cMax`  
 [w] Maksymalny rozmiar `rTypeDefs` tablicy.  
  
 `pcTypeDefs`  
 [na zewnątrz] Liczba tokenów TypeDef zwrócona w `rTypeDefs`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów do wyliczenia. W takim `pcTypeDefs` przypadku wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 TypeDef token reprezentuje typ, takich jak klasa lub interfejs, a także dowolny typ dodany za pośrednictwem mechanizmu rozszerzalności.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
