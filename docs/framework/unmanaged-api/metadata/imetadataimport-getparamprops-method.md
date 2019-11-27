---
title: IMetaDataImport::GetParamProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: bb73ccdd9eee4b5a655a56b5d6757e0c6003fbc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437126"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps — Metoda
Pobiera wartości metadanych dla parametru, do którego odwołuje się określony token ParamDef.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 podczas Token ParamDef reprezentujący parametr, dla którego mają zostać zwrócone metadane.  
  
 `pmd`  
 określoną Wskaźnik do tokenu MethodDef reprezentujący metodę, która pobiera parametr.  
  
 `pulSequence`  
 określoną Pozycja porządkowa parametru na liście argumentów metody.  
  
 `szName`  
 określoną Bufor służący do przechowywania nazwy parametru.  
  
 `cchName`  
 podczas Żądany rozmiar w szerokich znakach `szName`.  
  
 `pchName`  
 określoną Zwrócony rozmiar w szerokich znakach `szName`.  
  
 `pdwAttr`  
 określoną Wskaźnik do dowolnych flag atrybutów skojarzonych z parametrem. To jest maska bitów wartości `CorParamAttr`.  
  
 `pdwCPlusTypeFlag`  
 określoną Wskaźnik do flagi określającej, że parametr jest <xref:System.ValueType>.  
  
 `ppValue`  
 określoną Wskaźnik do stałego ciągu zwracanego przez parametr.  
  
 `pcchValue`  
 określoną Rozmiar `ppValue` w postaci dwubajtowej lub zero, jeśli `ppValue` nie zawiera ciągu.  
  
## <a name="remarks"></a>Uwagi

Wartości sekwencji w `pulSequence` zaczynają się od 1 dla parametrów. Wartość zwracana ma numer sekwencyjny równy 0.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
