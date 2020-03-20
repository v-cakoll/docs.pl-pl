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
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177889"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly — Metoda
Tworzy `Assembly` strukturę zawierającą metadane dla określonego zestawu i zwraca skojarzony token metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 [w] Klucz publiczny, który identyfikuje wydawcy zestawu lub NULL, jeśli zestaw nie jest silnie nazwany.  
  
 `cbPublicKey`  
 [w] Rozmiar w bajtach . `pbPublicKey`  
  
 `uHashAlgId`  
 [w] Identyfikator algorytmu mieszania do szyfrowania plików w zestawie lub NULL, aby określić algorytm SHA-1.  
  
 `szName`  
 [w] Nazwa tekstowa zestawu czytelna dla człowieka. Ta wartość nie może przekraczać 1024 znaków.  
  
 `pMetaData`  
 [w] Wskaźnik do assemblymetadata wystąpienie, który zawiera informacje o wersji, platformy i ustawień regionalnych dla zestawu.  
  
 `dwAssemblyFlags`  
 [w] Kombinacja [Wartości CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) opisujące operacje złożenia.  
  
 `pmda`  
 [na zewnątrz] Wskaźnik do tokenu metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Tylko `Assembly` jedna struktura metadanych można zdefiniować w manifeście.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
