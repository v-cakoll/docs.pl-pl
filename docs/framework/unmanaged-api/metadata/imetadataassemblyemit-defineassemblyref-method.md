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
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="edaf4-102">IMetaDataAssemblyEmit::DefineAssemblyRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="edaf4-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="edaf4-103">Tworzy `AssemblyRef` strukturę zawierającą metadane zestawu, do którego odwołuje się ten zestaw, i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="edaf4-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edaf4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="edaf4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="edaf4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="edaf4-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="edaf4-106">podczas Klucz publiczny wydawcy przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="edaf4-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="edaf4-107">Funkcja pomocnika [StrongNameTokenFromAssembly —](../strong-naming/strongnametokenfromassembly-function.md) może służyć do uzyskania skrótu klucza publicznego do przekazania jako ten parametr.</span><span class="sxs-lookup"><span data-stu-id="edaf4-107">The helper function [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="edaf4-108">podczas Rozmiar w bajtach `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="edaf4-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="edaf4-109">podczas Nazwa tekstu do odczytania przez człowieka.</span><span class="sxs-lookup"><span data-stu-id="edaf4-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="edaf4-110">Ta wartość nie może przekraczać 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="edaf4-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="edaf4-111">podczas Wystąpienie ASSEMBLYMETADATA, które zawiera wersję, platformę i informacje o ustawieniach regionalnych przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="edaf4-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="edaf4-112">podczas Dane skrótu skojarzone z przywoływanym zestawem.</span><span class="sxs-lookup"><span data-stu-id="edaf4-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="edaf4-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="edaf4-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="edaf4-114">podczas Rozmiar w bajtach `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="edaf4-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="edaf4-115">podczas Bitowa kombinacja wartości [CorAssemblyFlags —](corassemblyflags-enumeration.md) , które mają wpływ na zachowanie aparatu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="edaf4-115">[in] A bitwise combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="edaf4-116">określoną Wskaźnik do zwracanego `AssemblyRef` tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="edaf4-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edaf4-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="edaf4-117">Remarks</span></span>  
 <span data-ttu-id="edaf4-118">`AssemblyRef`Dla każdego zestawu, do którego odwołuje się ten zestaw, musi być zdefiniowana jedna struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="edaf4-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="edaf4-119">W czasie wykonywania szczegóły przywoływanego zestawu są przenoszone do programu rozpoznawania zestawu ze wskazaniem, że reprezentują informacje "jako skompilowane".</span><span class="sxs-lookup"><span data-stu-id="edaf4-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="edaf4-120">Program rozpoznawania zestawu stosuje zasady.</span><span class="sxs-lookup"><span data-stu-id="edaf4-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edaf4-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edaf4-121">Requirements</span></span>  
 <span data-ttu-id="edaf4-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edaf4-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edaf4-123">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="edaf4-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="edaf4-124">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="edaf4-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="edaf4-125">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edaf4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edaf4-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edaf4-126">See also</span></span>

- [<span data-ttu-id="edaf4-127">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="edaf4-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
