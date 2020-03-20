---
title: IMetaDataEmit::DefineParam — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177690"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam — Metoda
Tworzy definicję parametru z określonym podpisem dla metody, do którego odwołuje się określony token i pobiera token dla tej definicji parametru.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `md`  
 [w] Token dla metody, której parametr jest definiowany.  
  
 `ulParamSeq`  
 [w] Numer sekwencyjny parametru.  
  
 `szName`  
 [w] Nazwa parametru w Unicode.  
  
 `dwParamFlags`  
 [w] Flagi dla parametru. Jest to maska `CorParamAttr` bitowa wartości.  
  
 `dwCPlusTypeFlag`  
 [w] `ELEMENT_TYPE_` dla wartości stałej. *\**  
  
 `pValue`  
 [w] Stała wartość parametru.  
  
 `cchValue`  
 [w] Rozmiar w znakach Unicode `pValue`.  
  
 `ppd`  
 [na zewnątrz] Token `mdParamDef` przypisany.  
  
## <a name="remarks"></a>Uwagi  
 Wartości sekwencji `ulParamSeq` na początku od 1 dla parametrów. Zwracana wartość ma numer sekwencyjny 0.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
