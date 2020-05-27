---
title: IMetaDataAssemblyEmit::DefineAssemblyRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
ms.openlocfilehash: 612463bca18c23fac0b086adde2d208a0fbc5ae5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008173"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef — Metoda
Tworzy `AssemblyRef` strukturę zawierającą metadane zestawu, do którego odwołuje się ten zestaw, i zwraca skojarzony token metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyOrToken`  
 podczas Klucz publiczny wydawcy przywoływanego zestawu. Funkcja pomocnika [StrongNameTokenFromAssembly —](../strong-naming/strongnametokenfromassembly-function.md) może służyć do uzyskania skrótu klucza publicznego do przekazania jako ten parametr.  
  
 `cbPublicKeyOrToken`  
 podczas Rozmiar w bajtach `pbPublicKeyOrToken` .  
  
 `szName`  
 podczas Nazwa tekstu do odczytania przez człowieka. Ta wartość nie może przekraczać 1024 znaków.  
  
 `pMetaData`  
 podczas Wystąpienie ASSEMBLYMETADATA, które zawiera wersję, platformę i informacje o ustawieniach regionalnych przywoływanego zestawu.  
  
 `pbHashValue`  
 podczas Dane skrótu skojarzone z przywoływanym zestawem. Opcjonalny.  
  
 `cbHashValue`  
 podczas Rozmiar w bajtach `pbHashValue` .  
  
 `dwAssemblyRefFlags`  
 podczas Bitowa kombinacja wartości [CorAssemblyFlags —](corassemblyflags-enumeration.md) , które mają wpływ na zachowanie aparatu wykonywania.  
  
 `pmdar`  
 określoną Wskaźnik do zwracanego `AssemblyRef` tokenu metadanych.  
  
## <a name="remarks"></a>Uwagi  
 `AssemblyRef`Dla każdego zestawu, do którego odwołuje się ten zestaw, musi być zdefiniowana jedna struktura metadanych.  
  
 W czasie wykonywania szczegóły przywoływanego zestawu są przenoszone do programu rozpoznawania zestawu ze wskazaniem, że reprezentują informacje "jako skompilowane". Program rozpoznawania zestawu stosuje zasady.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](imetadataassemblyemit-interface.md)
