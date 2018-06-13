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
ms.openlocfilehash: 9115657c52f31d9b7b7da3c843338670343da26c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446476"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly — Metoda
Tworzy `Assembly` struktury metadane zawierające dla określonego zestawu i zwraca token skojarzone metadane.  
  
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
 [in] Klucz publiczny, który identyfikuje wydawcy zestawu, lub wartość NULL, jeśli nie ma silnej nazwy zestawu.  
  
 `cbPublicKey`  
 [in] Wyrażony w bajtach rozmiar `pbPublicKey`.  
  
 `uHashAlgId`  
 [in] Identyfikator algorytmu wyznaczania wartości skrótu służące do szyfrowania plików w zestawu, lub wartość NULL, aby określić algorytm SHA-1.  
  
 `szName`  
 [in] Tekst zrozumiałą nazwę zestawu. Ta wartość nie może przekraczać 1024 znaków.  
  
 `pMetaData`  
 [in] Wskaźnik do wystąpienia assemblymetadata —, który zawiera informacje o wersji platformy i ustawień regionalnych dla zestawu.  
  
 `dwAssemblyFlags`  
 [in] Kombinację [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości, które opisują funkcje zestawu.  
  
 `pmda`  
 [out] Wskaźnik do token metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Tylko jeden `Assembly` struktura metadanych można zdefiniować w manifeście.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
