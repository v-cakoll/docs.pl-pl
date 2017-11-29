---
title: "IMetaDataAssemblyEmit::SetAssemblyProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2c9336855d706a9861d4e832e5f0234cdf04db7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps — Metoda
Modyfikuje określony `Assembly` struktura metadanych.  
  
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
 [in] Token metadanych, który określa `Assembly` struktura metadanych ma być zmodyfikowana.  
  
 `pbPublicKey`  
 [in] Wskaźnik do klucza publicznego zestawu wydawcy.  
  
 `cbPublicKey`  
 [in] Wyrażony w bajtach rozmiar `pbPublicKey`.  
  
 `ulHashAlgId`  
 [in] Identyfikator algorytmu wyznaczania wartości skrótu używany do tworzenia skrótu pliki zestawu.  
  
 `szName`  
 [in] Tekst zrozumiałą nazwę zestawu.  
  
 `pMetaData`  
 [in] Wskaźnik do assemblymetadata —, który zawiera informacje o wersji platformy i ustawień regionalnych dla zestawu.  
  
 `dwAssemblyFlags`  
 [in] Bitowe połączenie [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) wartości, które określają różne atrybuty zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć `Assembly` metadanych struktury, użyj [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
