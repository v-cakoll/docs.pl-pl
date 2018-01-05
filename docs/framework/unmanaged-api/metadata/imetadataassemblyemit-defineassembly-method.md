---
title: "IMetaDataAssemblyEmit::DefineAssembly — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35bc85cdc4380ee112b7095866c05e5d7639200b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="c9c10-102">IMetaDataAssemblyEmit::DefineAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="c9c10-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="c9c10-103">Tworzy `Assembly` struktury metadane zawierające dla określonego zestawu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="c9c10-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9c10-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9c10-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c9c10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9c10-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="c9c10-106">[in] Klucz publiczny, który identyfikuje wydawcy zestawu, lub wartość NULL, jeśli nie ma silnej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9c10-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="c9c10-107">[in] Wyrażony w bajtach rozmiar `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="c9c10-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="c9c10-108">[in] Identyfikator algorytmu wyznaczania wartości skrótu służące do szyfrowania plików w zestawu, lub wartość NULL, aby określić algorytm SHA-1.</span><span class="sxs-lookup"><span data-stu-id="c9c10-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="c9c10-109">[in] Tekst zrozumiałą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9c10-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="c9c10-110">Ta wartość nie może przekraczać 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="c9c10-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="c9c10-111">[in] Wskaźnik do wystąpienia assemblymetadata —, który zawiera informacje o wersji platformy i ustawień regionalnych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9c10-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="c9c10-112">[in] Kombinację [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości, które opisują funkcje zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9c10-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="c9c10-113">[out] Wskaźnik do token metadanych.</span><span class="sxs-lookup"><span data-stu-id="c9c10-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9c10-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9c10-114">Remarks</span></span>  
 <span data-ttu-id="c9c10-115">Tylko jeden `Assembly` struktura metadanych można zdefiniować w manifeście.</span><span class="sxs-lookup"><span data-stu-id="c9c10-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9c10-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9c10-116">Requirements</span></span>  
 <span data-ttu-id="c9c10-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9c10-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9c10-118">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9c10-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9c10-119">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9c10-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9c10-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9c10-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c10-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9c10-121">See Also</span></span>  
 [<span data-ttu-id="c9c10-122">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9c10-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
