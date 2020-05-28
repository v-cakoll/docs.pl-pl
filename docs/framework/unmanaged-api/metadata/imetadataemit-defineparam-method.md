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
ms.openlocfilehash: a58e03875ec021b41479085fa9e27a4321ae965e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004364"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam — Metoda
Tworzy definicję parametru z określonym podpisem dla metody przywoływanej przez określony token i pobiera token dla tej definicji parametru.  
  
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
 podczas Token dla metody, której parametr jest definiowany.  
  
 `ulParamSeq`  
 podczas Numer sekwencyjny parametru.  
  
 `szName`  
 podczas Nazwa parametru w formacie Unicode.  
  
 `dwParamFlags`  
 podczas Flagi dla parametru. To jest maska bitów `CorParamAttr` wartości.  
  
 `dwCPlusTypeFlag`  
 [w] `ELEMENT_TYPE_` *\** dla wartości stałej.  
  
 `pValue`  
 podczas Stała wartość parametru.  
  
 `cchValue`  
 podczas Rozmiar, w znakach Unicode, z `pValue` .  
  
 `ppd`  
 określoną `mdParamDef`Przypisany token.  
  
## <a name="remarks"></a>Uwagi  
 Wartości sekwencji `ulParamSeq` zaczynają się od 1 dla parametrów. Wartość zwracana ma numer sekwencyjny równy 0.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
