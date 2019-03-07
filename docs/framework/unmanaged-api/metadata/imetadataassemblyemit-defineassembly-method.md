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
ms.openlocfilehash: bf6e0c1de9bfb920932e5c22adb4eb8573125506
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489967"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="7695c-102">IMetaDataAssemblyEmit::DefineAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="7695c-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="7695c-103">Tworzy `Assembly` struktury zawierającymi metadane dla określonego zestawu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="7695c-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7695c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7695c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7695c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7695c-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="7695c-106">[in] Klucz publiczny, który identyfikuje wydawcy zestawu lub wartość NULL, jeśli zestaw nie ma silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="7695c-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="7695c-107">[in] Rozmiar w bajtach `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="7695c-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="7695c-108">[in] Identyfikator algorytmu wyznaczania wartości skrótu służące do szyfrowania plików w zestawie lub o wartości NULL do określenia algorytmu SHA-1.</span><span class="sxs-lookup"><span data-stu-id="7695c-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="7695c-109">[in] Nazwa tekstowych zrozumiałych zestawu.</span><span class="sxs-lookup"><span data-stu-id="7695c-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="7695c-110">Ta wartość nie może przekraczać 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="7695c-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="7695c-111">[in] Wskaźnik na wystąpienie assemblymetadata —, który zawiera informacje o wersji, platformy i ustawienia regionalne dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="7695c-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="7695c-112">[in] Kombinacji [corassemblyflags —](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości, które opisano funkcje zestawu.</span><span class="sxs-lookup"><span data-stu-id="7695c-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="7695c-113">[out] Wskaźnik do tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="7695c-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7695c-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7695c-114">Remarks</span></span>  
 <span data-ttu-id="7695c-115">Tylko jeden `Assembly` struktury metadanych można zdefiniować w manifeście.</span><span class="sxs-lookup"><span data-stu-id="7695c-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7695c-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7695c-116">Requirements</span></span>  
 <span data-ttu-id="7695c-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7695c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7695c-118">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7695c-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7695c-119">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7695c-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7695c-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7695c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7695c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7695c-121">See also</span></span>
- [<span data-ttu-id="7695c-122">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="7695c-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
