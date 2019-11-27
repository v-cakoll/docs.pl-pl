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
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431690"
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
 podczas Flagi dla parametru. To jest maska bitów wartości `CorParamAttr`.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** dla wartości stałej.  
  
 `pValue`  
 podczas Stała wartość parametru.  
  
 `cchValue`  
 podczas Rozmiar w znakach Unicode `pValue`.  
  
 `ppd`  
 określoną Przypisany token `mdParamDef`.  
  
## <a name="remarks"></a>Uwagi  
 Wartości sekwencji w `ulParamSeq` zaczynają się od 1 dla parametrów. Wartość zwracana ma numer sekwencyjny równy 0.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
