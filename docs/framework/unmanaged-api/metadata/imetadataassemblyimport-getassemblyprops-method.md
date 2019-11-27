---
title: IMetaDataAssemblyImport::GetAssemblyProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: c3c57074ae53e2e1d8d41aa04cb6eb6089db58b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449441"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="ce586-102">IMetaDataAssemblyImport::GetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce586-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="ce586-103">Pobiera zestaw właściwości dla zestawu z określonym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="ce586-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce586-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce586-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce586-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce586-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="ce586-106">[in].</span><span class="sxs-lookup"><span data-stu-id="ce586-106">[in].</span></span> <span data-ttu-id="ce586-107">`mdAssembly` token metadanych reprezentujący zestaw, dla którego mają zostać pobrane właściwości.</span><span class="sxs-lookup"><span data-stu-id="ce586-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="ce586-108">określoną Wskaźnik do klucza publicznego lub tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="ce586-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="ce586-109">określoną Liczba bajtów w zwróconym kluczu publicznym.</span><span class="sxs-lookup"><span data-stu-id="ce586-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="ce586-110">określoną Wskaźnik do algorytmu używany do mieszania plików w zestawie.</span><span class="sxs-lookup"><span data-stu-id="ce586-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="ce586-111">określoną Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="ce586-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ce586-112">podczas Rozmiar, w postaci szerokich znaków, `szName`.</span><span class="sxs-lookup"><span data-stu-id="ce586-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="ce586-113">określoną Liczba znaków dwubajtowych faktycznie zwracanych w `szName`.</span><span class="sxs-lookup"><span data-stu-id="ce586-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="ce586-114">określoną Wskaźnik do struktury ASSEMBLYMETADATA, która zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="ce586-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="ce586-115">określoną Flagi opisujące metadane zastosowane do zestawu.</span><span class="sxs-lookup"><span data-stu-id="ce586-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="ce586-116">Ta wartość jest kombinacją co najmniej jednej wartości [CorAssemblyFlags —](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ce586-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce586-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce586-117">Requirements</span></span>  
 <span data-ttu-id="ce586-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce586-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce586-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ce586-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce586-120">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ce586-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ce586-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce586-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce586-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce586-122">See also</span></span>

- [<span data-ttu-id="ce586-123">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce586-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
