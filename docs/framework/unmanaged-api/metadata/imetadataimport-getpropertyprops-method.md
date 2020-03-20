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
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175333"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps — Metoda
Pobiera metadane dla właściwości reprezentowane przez określony token.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `prop`  
 [w] Token, który reprezentuje właściwość do zwrócenia metadanych.  
  
 `pClass`  
 [na zewnątrz] Wskaźnik do TypeDef token, który reprezentuje typ, który implementuje właściwość.  
  
 `szProperty`  
 [na zewnątrz] Bufor do przechowywania nazwy właściwości.  
  
 `cchProperty`  
 [w] Rozmiar w szerokich `szProperty`znaków .  
  
 `pchProperty`  
 [na zewnątrz] Liczba szerokich znaków `szProperty`zwróconych w pliku .  
  
 `pdwPropFlags`  
 [na zewnątrz] Wskaźnik do wszystkich flag atrybutów stosowanych do właściwości. Ta wartość jest maską bitową z [wyliczenia CorPropertyAttr.](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)  
  
 `ppvSig`  
 [na zewnątrz] Wskaźnik do podpisu metadanych właściwości.  
  
 `pbSig`  
 [na zewnątrz] Liczba bajtów zwróconych w `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [na zewnątrz] Flaga określająca typ stałej, która jest wartością domyślną właściwości. Ta wartość jest z wyliczenia CorElementType.  
  
 `ppDefaultValue`  
 [na zewnątrz] Wskaźnik do bajtów, które przechowują wartość domyślną dla tej właściwości.  
  
 `pcchDefaultValue`  
 [na zewnątrz] Rozmiar w szerokich `ppDefaultValue`znakach , jeśli `pdwCPlusTypeFlag` jest ELEMENT_TYPE_STRING; w przeciwnym razie wartość ta nie jest istotna. W takim przypadku długość `ppDefaultValue` jest wywnioskowana z `pdwCPlusTypeFlag`typu określonego przez .  
  
 `pmdSetter`  
 [na zewnątrz] Wskaźnik do MethodDef token, który reprezentuje metodę akcesora zestawu dla właściwości.  
  
 `pmdGetter`  
 [na zewnątrz] Wskaźnik do MethodDef token, który reprezentuje get metody akcesora dla właściwości.  
  
 `rmdOtherMethod`  
 [na zewnątrz] Tablica tokenów MethodDef, które reprezentują inne metody skojarzone z właściwością.  
  
 `cMax`  
 [w] Maksymalny rozmiar `rmdOtherMethod` tablicy. Jeśli nie podasz tablicy wystarczająco duże, aby pomieścić wszystkie metody, są pomijane bez ostrzeżenia.  
  
 `pcOtherMethod`  
 [na zewnątrz] Liczba tokenów MethodDef zwrócona w `rmdOtherMethod`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
