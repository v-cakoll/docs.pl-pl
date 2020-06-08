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
ms.openlocfilehash: c2abf2813c6e1a9db4264bded32d9cb9c58a2bcb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491059"
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
 podczas Żądany rozmiar w postaci znaków dwubajtowych `szName` .  
  
 `pchName`  
 określoną Zwrócony rozmiar w postaci znaków dwubajtowych `szName` .  
  
 `pdwAttr`  
 określoną Wskaźnik do dowolnych flag atrybutów skojarzonych z parametrem. To jest maska bitów `CorParamAttr` wartości.  
  
 `pdwCPlusTypeFlag`  
 określoną Wskaźnik do flagi wskazującej, że parametr jest <xref:System.ValueType> .  
  
 `ppValue`  
 określoną Wskaźnik do stałego ciągu zwracanego przez parametr.  
  
 `pcchValue`  
 określoną Rozmiar znaków dwubajtowych `ppValue` lub zero, jeśli nie zawiera `ppValue` ciągu.  
  
## <a name="remarks"></a>Uwagi

Wartości sekwencji `pulSequence` zaczynają się od 1 dla parametrów. Wartość zwracana ma numer sekwencyjny równy 0.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
