---
title: "IMetaDataImport::GetPropertyProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc3a1ce1d07bda50b2b578e7d20870324d60edc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [in] Token, który reprezentuje właściwość do zwracania metadanych.  
  
 `pClass`  
 [out] Wskaźnik do TypeDef token, który reprezentuje typ, który implementuje właściwości.  
  
 `szProperty`  
 [out] Bufor do przechowywania nazwy właściwości.  
  
 `cchProperty`  
 [in] Rozmiar w znaki dwubajtowe `szProperty`.  
  
 `pchProperty`  
 [out] Liczba zwracanych w znaki dwubajtowe `szProperty`.  
  
 `pdwPropFlags`  
 [out] Wskaźnik do flagi, atrybut zastosowany do właściwości. Ta wartość jest maską bitów z [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) wyliczenia.  
  
 `ppvSig`  
 [out] Wskaźnik do podpisania metadanych właściwości.  
  
 `pbSig`  
 [out] Liczba bajtów zwrócona w `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [out] Flaga określający typ stałej, która jest wartością domyślną właściwości. Ta wartość jest z corelementtype — wyliczenie.  
  
 `ppDefaultValue`  
 [out] Wskaźnik do bajtów, które przechowują wartość domyślna dla tej właściwości.  
  
 `pcchDefaultValue`  
 [out] Rozmiar w znaki dwubajtowe `ppDefaultValue`, jeśli `pdwCPlusTypeFlag` jest ELEMENT_TYPE_STRING; w przeciwnym razie wartość ta nie jest ważna. W takim przypadku długość `ppDefaultValue` jest wywnioskowany na podstawie typu, który jest określony przez `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 [out] Wskaźnik do tokenu MethodDef, który reprezentuje metody dostępu set dla właściwości.  
  
 `pmdGetter`  
 [out] Wskaźnik do tokenu MethodDef, który reprezentuje metodę dostępu get dla właściwości.  
  
 `rmdOtherMethod`  
 [out] Tablica MethodDef reprezentujących innych metod skojarzony z właściwością.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rmdOtherMethod` tablicy. Tablica jest wystarczająco duży, aby pomieścić wszystkie metody nie zostaną podane, są pominięcie bez ostrzeżenia.  
  
 `pcOtherMethod`  
 [out] Liczba tokenów MethodDef zwracane w `rmdOtherMethod`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
