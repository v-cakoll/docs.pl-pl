---
title: IMetaDataAssemblyEmit::DefineAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d860a6518014e0232f9372a7ccbf34604096adfd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54747885"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly — Metoda
Tworzy `Assembly` struktury zawierającymi metadane dla określonego zestawu i zwraca token skojarzone metadane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbPublicKey`  
 [in] Klucz publiczny, który identyfikuje wydawcy zestawu lub wartość NULL, jeśli zestaw nie ma silnej nazwy.  
  
 `cbPublicKey`  
 [in] Rozmiar w bajtach `pbPublicKey`.  
  
 `uHashAlgId`  
 [in] Identyfikator algorytmu wyznaczania wartości skrótu służące do szyfrowania plików w zestawie lub o wartości NULL do określenia algorytmu SHA-1.  
  
 `szName`  
 [in] Nazwa tekstowych zrozumiałych zestawu. Ta wartość nie może przekraczać 1024 znaków.  
  
 `pMetaData`  
 [in] Wskaźnik na wystąpienie assemblymetadata —, który zawiera informacje o wersji, platformy i ustawienia regionalne dla zestawu.  
  
 `dwAssemblyFlags`  
 [in] Kombinacji [corassemblyflags —](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości, które opisano funkcje zestawu.  
  
 `pmda`  
 [out] Wskaźnik do tokenu metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Tylko jeden `Assembly` struktury metadanych można zdefiniować w manifeście.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
