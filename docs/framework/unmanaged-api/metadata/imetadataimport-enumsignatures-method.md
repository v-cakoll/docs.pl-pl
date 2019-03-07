---
title: IMetaDataImport::EnumSignatures — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de21f4bb91198a5eb77f94789d0389d97123b7a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472489"
---
# <a name="imetadataimportenumsignatures-method"></a>IMetaDataImport::EnumSignatures — Metoda
Wylicza tokenów sygnatur reprezentujący autonomicznej podpisów w bieżącym zakresie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out w] Wskaźnik do modułu wyliczającego. Musi to być wartość NULL dla pierwszego wywołania tej metody.  
  
 `rSignatures`  
 [out] Tablica do przechowywania tokenów sygnatur.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rSignatures` tablicy.  
  
 `pcSignatures`  
 [out] Liczba tokenów sygnatur zwracane w `rSignatures`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumSignatures` pomyślnie zwrócił.|  
|`S_FALSE`|Nie ma żadnych tokeny do wyliczenia. W takim przypadku `pcSignatures` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Tokeny sygnatury są tworzone przez [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
