---
title: IMetaDataImport::GetPropertyProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81680825daff2cd2358da7b3956782020edf4791
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672061"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps — Metoda
Pobiera metadane dla właściwości reprezentowanej przez określony token.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prop`  
 [in] Token, który reprezentuje właściwość, można zwrócić metadanych dla.  
  
 `pClass`  
 [out] Wskaźnik do TypeDef token, który reprezentuje typ, który implementuje właściwości.  
  
 `szProperty`  
 [out] Bufor do przechowywania nazwy właściwości.  
  
 `cchProperty`  
 [in] Rozmiar w znaków `szProperty`.  
  
 `pchProperty`  
 [out] Liczba znaków dwubajtowych zwracane w `szProperty`.  
  
 `pdwPropFlags`  
 [out] Wskaźnik do flag atrybut stosowany do właściwości. Ta wartość jest z [corpropertyattr —](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) wyliczenia.  
  
 `ppvSig`  
 [out] Wskaźnik do podpisania metadanych właściwości.  
  
 `pbSig`  
 [out] Liczba bajtów zwróconych w `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [out] Flaga określająca typ stałej, która jest wartością domyślną właściwości. Ta wartość pochodzi z corelementtype — wyliczenie.  
  
 `ppDefaultValue`  
 [out] Wskaźnik na bajty, które przechowują wartość domyślna tej właściwości.  
  
 `pcchDefaultValue`  
 [out] Rozmiar w znaków `ppDefaultValue`, jeśli `pdwCPlusTypeFlag` jest ELEMENT_TYPE_STRING; w przeciwnym razie ta wartość nie jest ważna. W takim przypadku długość `ppDefaultValue` jest wnioskowany z typu, który jest określony przez `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 [out] Wskaźnik do tokenu MethodDef, który reprezentuje metody dostępu set dla właściwości.  
  
 `pmdGetter`  
 [out] Wskaźnik do tokenu MethodDef, który reprezentuje metody dostępu get dla właściwości.  
  
 `rmdOtherMethod`  
 [out] Tablica MethodDef, które reprezentują inne metody skojarzony z właściwością.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rmdOtherMethod` tablicy. Jeśli nie podasz, tablica jest wystarczająco duży, aby pomieścić wszystkie metody, są one pomijane bez ostrzeżenia.  
  
 `pcOtherMethod`  
 [out] Liczba tokenów MethodDef zwracane w `rmdOtherMethod`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
