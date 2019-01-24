---
title: IMetaDataAssemblyEmit::SetAssemblyProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37d91ca7935e114504864683075f4809de7270fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599117"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps — Metoda
Modyfikuje określonego `Assembly` struktury metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pma`  
 [in] Token metadanych, który określa `Assembly` struktury metadanych do zmodyfikowania.  
  
 `pbPublicKey`  
 [in] Wskaźnik do klucza publicznego wydawcy zestawu.  
  
 `cbPublicKey`  
 [in] Rozmiar w bajtach `pbPublicKey`.  
  
 `ulHashAlgId`  
 [in] Identyfikator algorytmu mieszania używany do tworzenia skrótu plików zestawu.  
  
 `szName`  
 [in] Nazwa tekstowych zrozumiałych zestawu.  
  
 `pMetaData`  
 [in] Wskaźnik do assemblymetadata —, który zawiera informacje o wersji, platformy i ustawienia regionalne dla zestawu.  
  
 `dwAssemblyFlags`  
 [in] Bitowa kombinacja [assemblyflags —](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) wartości, które określają różne atrybuty zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć `Assembly` struktury metadanych, użyj [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
