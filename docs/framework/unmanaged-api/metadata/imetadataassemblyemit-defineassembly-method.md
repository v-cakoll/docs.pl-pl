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
ms.openlocfilehash: 86002eb38d72ee628dbf54d0b5691f0816e6f996
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="9234f-102">IMetaDataAssemblyEmit::DefineAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="9234f-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="9234f-103">Tworzy `Assembly` struktury metadane zawierające dla określonego zestawu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="9234f-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9234f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9234f-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9234f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9234f-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="9234f-106">[in] Klucz publiczny, który identyfikuje wydawcy zestawu, lub wartość NULL, jeśli nie ma silnej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="9234f-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="9234f-107">[in] Wyrażony w bajtach rozmiar `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="9234f-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="9234f-108">[in] Identyfikator algorytmu wyznaczania wartości skrótu służące do szyfrowania plików w zestawu, lub wartość NULL, aby określić algorytm SHA-1.</span><span class="sxs-lookup"><span data-stu-id="9234f-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="9234f-109">[in] Tekst zrozumiałą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="9234f-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="9234f-110">Ta wartość nie może przekraczać 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="9234f-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="9234f-111">[in] Wskaźnik do wystąpienia assemblymetadata —, który zawiera informacje o wersji platformy i ustawień regionalnych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="9234f-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="9234f-112">[in] Kombinację [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości, które opisują funkcje zestawu.</span><span class="sxs-lookup"><span data-stu-id="9234f-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="9234f-113">[out] Wskaźnik do token metadanych.</span><span class="sxs-lookup"><span data-stu-id="9234f-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9234f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9234f-114">Remarks</span></span>  
 <span data-ttu-id="9234f-115">Tylko jeden `Assembly` struktura metadanych można zdefiniować w manifeście.</span><span class="sxs-lookup"><span data-stu-id="9234f-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9234f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9234f-116">Requirements</span></span>  
 <span data-ttu-id="9234f-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9234f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9234f-118">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9234f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9234f-119">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9234f-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9234f-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9234f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9234f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9234f-121">See Also</span></span>  
 [<span data-ttu-id="9234f-122">IMetaDataAssemblyEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="9234f-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
