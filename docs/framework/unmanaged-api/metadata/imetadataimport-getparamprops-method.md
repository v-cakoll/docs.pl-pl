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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9d2c74adecdfb0201f9f0c08998feba674f9e0f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778925"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps — Metoda
Pobiera metadane wartości dla parametru odwołuje się określona ParamDef token.  
  
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
 [in] Token ParamDef, który reprezentuje parametr można zwrócić metadanych dla.  
  
 `pmd`  
 [out] Wskaźnik do tokenu MethodDef reprezentujący metodę, która przyjmuje parametr.  
  
 `pulSequence`  
 [out] Numer porządkowy pozycja parametru na liście argumentów metody.  
  
 `szName`  
 [out] Bufor do przechowywania nazwy parametru.  
  
 `cchName`  
 [in] Żądany rozmiar w znaków `szName`.  
  
 `pchName`  
 [out] Rozmiar zwrócony w znaków `szName`.  
  
 `pdwAttr`  
 [out] Wskaźnik do flag atrybut skojarzony z parametrem. Jest to z `CorParamAttr` wartości.  
  
 `pdwCPlusTypeFlag`  
 [out] Wskaźnik do określania flagi, że parametr jest <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Wskaźnik ze stałym ciągiem zwrócone przez parametr.  
  
 `pcchValue`  
 [out] Rozmiar `ppValue` znaków dwubajtowych lub zero, jeśli `ppValue` nie zawiera ciągu.  
  
## <a name="remarks"></a>Uwagi

Sekwencja wartości w `pulSequence` zaczynają się od 1 dla parametrów. Wartość zwracana ma kolejny numer 0.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
