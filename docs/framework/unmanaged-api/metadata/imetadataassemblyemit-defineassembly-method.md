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
ms.openlocfilehash: 17c91200730431c4c6e230b8c1561ce7c4863868
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008186"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="4c367-102">IMetaDataAssemblyEmit::DefineAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c367-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="4c367-103">Tworzy `Assembly` strukturę zawierającą metadane dla określonego zestawu i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="4c367-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c367-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c367-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4c367-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c367-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="4c367-106">podczas Klucz publiczny, który identyfikuje wydawcę zestawu lub wartość NULL, jeśli zestaw nie ma silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4c367-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="4c367-107">podczas Rozmiar w bajtach `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="4c367-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="4c367-108">podczas Identyfikator algorytmu wyznaczania wartości skrótu, który ma być używany do szyfrowania plików w zestawie, lub wartość NULL, aby określić algorytm SHA-1.</span><span class="sxs-lookup"><span data-stu-id="4c367-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="4c367-109">podczas Nazwa tekstu do odczytania przez człowieka.</span><span class="sxs-lookup"><span data-stu-id="4c367-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="4c367-110">Ta wartość nie może przekraczać 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="4c367-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="4c367-111">podczas Wskaźnik do wystąpienia ASSEMBLYMETADATA, który zawiera wersję, platformę i informacje o ustawieniach regionalnych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="4c367-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="4c367-112">podczas Kombinacja wartości [CorAssemblyFlags —](corassemblyflags-enumeration.md) , które opisują funkcje zestawu.</span><span class="sxs-lookup"><span data-stu-id="4c367-112">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="4c367-113">określoną Wskaźnik do tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="4c367-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c367-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c367-114">Remarks</span></span>  
 <span data-ttu-id="4c367-115">`Assembly`W manifeście można zdefiniować tylko jedną strukturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="4c367-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c367-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c367-116">Requirements</span></span>  
 <span data-ttu-id="4c367-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c367-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c367-118">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4c367-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c367-119">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4c367-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c367-120">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c367-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c367-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c367-121">See also</span></span>

- [<span data-ttu-id="4c367-122">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4c367-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
