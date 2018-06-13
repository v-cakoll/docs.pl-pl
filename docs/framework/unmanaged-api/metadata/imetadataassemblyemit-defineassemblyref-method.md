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
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="f8e60-102">IMetaDataAssemblyEmit::DefineAssemblyRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="f8e60-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="f8e60-103">Tworzy `AssemblyRef` struktury zawierającej metadanych dla zestawu, który odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="f8e60-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8e60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8e60-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f8e60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8e60-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="f8e60-106">[in] Klucz publiczny wydawcy przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f8e60-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="f8e60-107">Funkcja Pomocnika [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) można uzyskać skrótu klucza publicznego do przekazania jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f8e60-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="f8e60-108">[in] Wyrażony w bajtach rozmiar `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="f8e60-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="f8e60-109">[in] Tekst zrozumiałą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="f8e60-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="f8e60-110">Ta wartość nie może przekraczać 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="f8e60-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="f8e60-111">[in] Wystąpienie assemblymetadata —, który zawiera informacje o wersji, platform i ustawień regionalnych przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f8e60-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f8e60-112">[in] Skrót danych skojarzonych z przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f8e60-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="f8e60-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f8e60-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f8e60-114">[in] Wyrażony w bajtach rozmiar `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f8e60-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="f8e60-115">[in] Bitowe połączenie [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości, które wywierania wpływu na zachowanie aparat wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f8e60-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="f8e60-116">[out] Wskaźnik do zwróconego `AssemblyRef` token metadanych.</span><span class="sxs-lookup"><span data-stu-id="f8e60-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8e60-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8e60-117">Remarks</span></span>  
 <span data-ttu-id="f8e60-118">Jeden `AssemblyRef` struktura metadanych musi być zdefiniowana dla każdego zestawu, który odwołuje się do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f8e60-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="f8e60-119">W czasie wykonywania szczegółowe informacje o zestawie są przekazywane do rozpoznawania zestawu ze wskazaniem reprezentują one informacje "jako wbudowane".</span><span class="sxs-lookup"><span data-stu-id="f8e60-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="f8e60-120">Mechanizm rozpoznawania zestawów następnie stosuje zasady.</span><span class="sxs-lookup"><span data-stu-id="f8e60-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8e60-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8e60-121">Requirements</span></span>  
 <span data-ttu-id="f8e60-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8e60-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8e60-123">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f8e60-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8e60-124">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8e60-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8e60-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8e60-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8e60-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8e60-126">See Also</span></span>  
 [<span data-ttu-id="f8e60-127">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8e60-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
