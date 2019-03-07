---
title: IMetaDataEmit::DefineMemberRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad2b3e5c452a5fc79e7a1cc0342cfc1d119a5fbd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481992"
---
# <a name="imetadataemitdefinememberref-method"></a>IMetaDataEmit::DefineMemberRef — Metoda
Określa odwołanie do elementu członkowskiego modułu poza bieżącym zakresem, a następnie pobiera token do tej definicji odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tkImport`  
 [in] Tokenu dla docelowego elementu członkowskiego klasy lub interfejsu, jeśli element nie jest globalne; Jeśli element jest globalnym, `mdModuleRef` tokenu dla tego innego pliku.  
  
 `szName`  
 [in] Nazwa elementu docelowego.  
  
 `pvSigBlob`  
 [in] Podpis elementu docelowego.  
  
 `cbSigBlob`  
 [in] Liczba bajtów w `pvSigBlob`.  
  
 `pmr`  
 [out] `mdMemberRef` Token przypisany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
