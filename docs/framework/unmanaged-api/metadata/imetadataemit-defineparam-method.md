---
title: "IMetaDataEmit::DefineParam — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5abe9cf0385a42645468bf58c2f81223ac4eeead
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam — Metoda
Tworzy definicję parametru z określoną sygnaturą dla metody odwołuje się określony token i pobiera token dla tej definicji parametru.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `md`  
 [in] Token metody zdefiniowano którego parametr.  
  
 `ulParamSeq`  
 [in] Numer sekwencji parametru.  
  
 `szName`  
 [in] Nazwa parametru w standardzie Unicode.  
  
 `dwParamFlags`  
 [in] Flagi dla parametru. To jest maską bitów z `CorParamAttr` wartości.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_`  *\**  wartości stałej.  
  
 `pValue`  
 [in] Wartość stała dla parametru.  
  
 `cchValue`  
 [in] Rozmiar w znaki Unicode z `pValue`.  
  
 `ppd`  
 [out] `mdParamDef` Token przypisany.  
  
## <a name="remarks"></a>Uwagi  
 Sekwencja wartości w `ulParamSeq` zaczynać się od 1 do parametrów. Wartość zwrotna ma numer sekwencji 0.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
