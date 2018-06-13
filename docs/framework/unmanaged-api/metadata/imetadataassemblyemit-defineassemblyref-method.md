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
ms.openlocfilehash: b6675d50d3222a43abc8838c3c86cb825d2dad16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445725"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef — Metoda
Tworzy `AssemblyRef` struktury zawierającej metadanych dla zestawu, który odwołuje się ten zestaw i zwraca token skojarzone metadane.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pbPublicKeyOrToken`  
 [in] Klucz publiczny wydawcy przywoływanego zestawu. Funkcja Pomocnika [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) można uzyskać skrótu klucza publicznego do przekazania jako parametr.  
  
 `cbPublicKeyOrToken`  
 [in] Wyrażony w bajtach rozmiar `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] Tekst zrozumiałą nazwę zestawu. Ta wartość nie może przekraczać 1024 znaków.  
  
 `pMetaData`  
 [in] Wystąpienie assemblymetadata —, który zawiera informacje o wersji, platform i ustawień regionalnych przywoływanego zestawu.  
  
 `pbHashValue`  
 [in] Skrót danych skojarzonych z przywoływanego zestawu. Opcjonalna.  
  
 `cbHashValue`  
 [in] Wyrażony w bajtach rozmiar `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] Bitowe połączenie [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości, które wywierania wpływu na zachowanie aparat wykonywania.  
  
 `pmdar`  
 [out] Wskaźnik do zwróconego `AssemblyRef` token metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Jeden `AssemblyRef` struktura metadanych musi być zdefiniowana dla każdego zestawu, który odwołuje się do tego zestawu.  
  
 W czasie wykonywania szczegółowe informacje o zestawie są przekazywane do rozpoznawania zestawu ze wskazaniem reprezentują one informacje "jako wbudowane". Mechanizm rozpoznawania zestawów następnie stosuje zasady.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
