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
ms.openlocfilehash: d53409e0be43dbf5d0cf7ba0fcbc170e2117f6a1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745812"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="fc431-102">IMetaDataAssemblyEmit::DefineAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc431-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="fc431-103">Tworzy `Assembly` struktury zawierającymi metadane dla określonego zestawu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="fc431-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc431-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc431-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="fc431-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc431-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="fc431-106">[in] Klucz publiczny, który identyfikuje wydawcy zestawu lub wartość NULL, jeśli zestaw nie ma silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fc431-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="fc431-107">[in] Rozmiar w bajtach `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="fc431-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="fc431-108">[in] Identyfikator algorytmu wyznaczania wartości skrótu służące do szyfrowania plików w zestawie lub o wartości NULL do określenia algorytmu SHA-1.</span><span class="sxs-lookup"><span data-stu-id="fc431-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="fc431-109">[in] Nazwa tekstowych zrozumiałych zestawu.</span><span class="sxs-lookup"><span data-stu-id="fc431-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="fc431-110">Ta wartość nie może przekraczać 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="fc431-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="fc431-111">[in] Wskaźnik na wystąpienie assemblymetadata —, który zawiera informacje o wersji, platformy i ustawienia regionalne dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="fc431-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="fc431-112">[in] Kombinacji [corassemblyflags —](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości, które opisano funkcje zestawu.</span><span class="sxs-lookup"><span data-stu-id="fc431-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="fc431-113">[out] Wskaźnik do tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="fc431-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc431-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc431-114">Remarks</span></span>  
 <span data-ttu-id="fc431-115">Tylko jeden `Assembly` struktury metadanych można zdefiniować w manifeście.</span><span class="sxs-lookup"><span data-stu-id="fc431-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc431-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc431-116">Requirements</span></span>  
 <span data-ttu-id="fc431-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc431-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc431-118">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fc431-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc431-119">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc431-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc431-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc431-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc431-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc431-121">See also</span></span>

- [<span data-ttu-id="fc431-122">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc431-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
