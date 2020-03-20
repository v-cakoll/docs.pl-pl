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
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177889"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="6586f-102">IMetaDataAssemblyEmit::DefineAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="6586f-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="6586f-103">Tworzy `Assembly` strukturę zawierającą metadane dla określonego zestawu i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="6586f-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6586f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6586f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6586f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6586f-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="6586f-106">[w] Klucz publiczny, który identyfikuje wydawcy zestawu lub NULL, jeśli zestaw nie jest silnie nazwany.</span><span class="sxs-lookup"><span data-stu-id="6586f-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="6586f-107">[w] Rozmiar w bajtach . `pbPublicKey`</span><span class="sxs-lookup"><span data-stu-id="6586f-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="6586f-108">[w] Identyfikator algorytmu mieszania do szyfrowania plików w zestawie lub NULL, aby określić algorytm SHA-1.</span><span class="sxs-lookup"><span data-stu-id="6586f-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="6586f-109">[w] Nazwa tekstowa zestawu czytelna dla człowieka.</span><span class="sxs-lookup"><span data-stu-id="6586f-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="6586f-110">Ta wartość nie może przekraczać 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="6586f-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="6586f-111">[w] Wskaźnik do assemblymetadata wystąpienie, który zawiera informacje o wersji, platformy i ustawień regionalnych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="6586f-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="6586f-112">[w] Kombinacja [Wartości CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) opisujące operacje złożenia.</span><span class="sxs-lookup"><span data-stu-id="6586f-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="6586f-113">[na zewnątrz] Wskaźnik do tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="6586f-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6586f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6586f-114">Remarks</span></span>  
 <span data-ttu-id="6586f-115">Tylko `Assembly` jedna struktura metadanych można zdefiniować w manifeście.</span><span class="sxs-lookup"><span data-stu-id="6586f-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6586f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6586f-116">Requirements</span></span>  
 <span data-ttu-id="6586f-117">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6586f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6586f-118">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="6586f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6586f-119">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6586f-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6586f-120">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6586f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6586f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6586f-121">See also</span></span>

- [<span data-ttu-id="6586f-122">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6586f-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
