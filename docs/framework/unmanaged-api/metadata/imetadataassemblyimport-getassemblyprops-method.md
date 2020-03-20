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
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177790"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="dfb57-102">IMetaDataAssemblyImport::GetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="dfb57-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="dfb57-103">Pobiera zestaw właściwości dla zestawu z określonym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="dfb57-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfb57-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfb57-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dfb57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfb57-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="dfb57-106">[w].</span><span class="sxs-lookup"><span data-stu-id="dfb57-106">[in].</span></span> <span data-ttu-id="dfb57-107">Token `mdAssembly` metadanych, który reprezentuje zestaw, dla którego mają zostać właściwości.</span><span class="sxs-lookup"><span data-stu-id="dfb57-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="dfb57-108">[na zewnątrz] Wskaźnik do klucza publicznego lub tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="dfb57-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="dfb57-109">[na zewnątrz] Liczba bajtów w zwróconym kluczu publicznym.</span><span class="sxs-lookup"><span data-stu-id="dfb57-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="dfb57-110">[na zewnątrz] Wskaźnik do algorytmu używanego do mieszania plików w zestawie.</span><span class="sxs-lookup"><span data-stu-id="dfb57-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="dfb57-111">[na zewnątrz] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="dfb57-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="dfb57-112">[w] Rozmiar, w szerokich znaków, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="dfb57-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="dfb57-113">[na zewnątrz] Liczba szerokich znaków rzeczywiście `szName`zwrócona w .</span><span class="sxs-lookup"><span data-stu-id="dfb57-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="dfb57-114">[na zewnątrz] Wskaźnik do ASSEMBLYMETADATA struktury, która zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="dfb57-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="dfb57-115">[na zewnątrz] Flagi opisujące metadane zastosowane do zestawu.</span><span class="sxs-lookup"><span data-stu-id="dfb57-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="dfb57-116">Ta wartość jest kombinacją jednej lub więcej wartości [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="dfb57-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfb57-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfb57-117">Requirements</span></span>  
 <span data-ttu-id="dfb57-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfb57-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfb57-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="dfb57-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dfb57-120">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dfb57-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dfb57-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfb57-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb57-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfb57-122">See also</span></span>

- [<span data-ttu-id="dfb57-123">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dfb57-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
