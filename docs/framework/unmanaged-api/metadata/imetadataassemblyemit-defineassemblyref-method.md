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
ms.openlocfilehash: f82fca1d7701921a10c1feb9cce19371729ff01e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493473"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="11f9b-102">IMetaDataAssemblyEmit::DefineAssemblyRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="11f9b-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="11f9b-103">Tworzy `AssemblyRef` struktury zawierający metadane dla zestawu, który odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="11f9b-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11f9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11f9b-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="11f9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11f9b-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="11f9b-106">[in] Klucz publiczny wydawcy przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="11f9b-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="11f9b-107">Funkcja Pomocnika [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) umożliwia uzyskanie skrótu klucza publicznego do przekazania jako parametr.</span><span class="sxs-lookup"><span data-stu-id="11f9b-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="11f9b-108">[in] Rozmiar w bajtach `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="11f9b-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="11f9b-109">[in] Nazwa tekstowych zrozumiałych zestawu.</span><span class="sxs-lookup"><span data-stu-id="11f9b-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="11f9b-110">Ta wartość nie może przekraczać 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="11f9b-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="11f9b-111">[in] Wystąpienie assemblymetadata —, który zawiera informacje o wersji, platformy i ustawienia regionalne przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="11f9b-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="11f9b-112">[in] Dane wyznaczania wartości skrótu, skojarzone z przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="11f9b-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="11f9b-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="11f9b-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="11f9b-114">[in] Rozmiar w bajtach `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="11f9b-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="11f9b-115">[in] Bitowa kombinacja [corassemblyflags —](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości, które mają wpływ na zachowanie aparatu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="11f9b-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="11f9b-116">[out] Wskaźnik do zwracanego `AssemblyRef` token metadanych.</span><span class="sxs-lookup"><span data-stu-id="11f9b-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11f9b-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11f9b-117">Remarks</span></span>  
 <span data-ttu-id="11f9b-118">Jeden `AssemblyRef` struktury metadanych musi być zdefiniowana dla każdego zestawu, który odwołuje się do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="11f9b-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="11f9b-119">W czasie wykonywania szczegółowe informacje o zestawie odwołania są przekazywane do programu rozpoznawania nazw zestawów ze wskazaniem, czy stanowią one informacje "jak skompilowana".</span><span class="sxs-lookup"><span data-stu-id="11f9b-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="11f9b-120">Mechanizm rozpoznawania zestawów następnie stosuje zasady.</span><span class="sxs-lookup"><span data-stu-id="11f9b-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11f9b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11f9b-121">Requirements</span></span>  
 <span data-ttu-id="11f9b-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11f9b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11f9b-123">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="11f9b-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11f9b-124">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11f9b-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11f9b-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11f9b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11f9b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11f9b-126">See also</span></span>
- [<span data-ttu-id="11f9b-127">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="11f9b-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
