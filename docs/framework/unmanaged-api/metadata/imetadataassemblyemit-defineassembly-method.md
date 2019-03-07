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
ms.openlocfilehash: bf6e0c1de9bfb920932e5c22adb4eb8573125506
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489967"
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
  
## <a name="parameters"></a>Parametry  
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
