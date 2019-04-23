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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e480c408c10eb9e135f260426750f7747e5d8ce5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117355"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef — Metoda
Tworzy `AssemblyRef` struktury zawierający metadane dla zestawu, który odwołuje się ten zestaw i zwraca token skojarzone metadane.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Klucz publiczny wydawcy przywoływanego zestawu. Funkcja Pomocnika [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) umożliwia uzyskanie skrótu klucza publicznego do przekazania jako parametr.  
  
 `cbPublicKeyOrToken`  
 [in] Rozmiar w bajtach `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] Nazwa tekstowych zrozumiałych zestawu. Ta wartość nie może przekraczać 1024 znaków.  
  
 `pMetaData`  
 [in] Wystąpienie assemblymetadata —, który zawiera informacje o wersji, platformy i ustawienia regionalne przywoływanego zestawu.  
  
 `pbHashValue`  
 [in] Dane wyznaczania wartości skrótu, skojarzone z przywoływanego zestawu. Opcjonalna.  
  
 `cbHashValue`  
 [in] Rozmiar w bajtach `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] Bitowa kombinacja [corassemblyflags —](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości, które mają wpływ na zachowanie aparatu wykonywania.  
  
 `pmdar`  
 [out] Wskaźnik do zwracanego `AssemblyRef` token metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Jeden `AssemblyRef` struktury metadanych musi być zdefiniowana dla każdego zestawu, który odwołuje się do tego zestawu.  
  
 W czasie wykonywania szczegółowe informacje o zestawie odwołania są przekazywane do programu rozpoznawania nazw zestawów ze wskazaniem, czy stanowią one informacje "jak skompilowana". Mechanizm rozpoznawania zestawów następnie stosuje zasady.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
