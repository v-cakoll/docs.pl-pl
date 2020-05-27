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
ms.openlocfilehash: a90deaf3e9ddf326c6fca558cbb4681fc40e022d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009057"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="b248e-102">IMetaDataAssemblyImport::GetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="b248e-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="b248e-103">Pobiera zestaw właściwości dla zestawu z określonym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="b248e-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b248e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b248e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b248e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b248e-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="b248e-106">[in].</span><span class="sxs-lookup"><span data-stu-id="b248e-106">[in].</span></span> <span data-ttu-id="b248e-107">`mdAssembly`Token metadanych reprezentujący zestaw, dla którego mają zostać pobrane właściwości.</span><span class="sxs-lookup"><span data-stu-id="b248e-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="b248e-108">określoną Wskaźnik do klucza publicznego lub tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="b248e-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="b248e-109">określoną Liczba bajtów w zwróconym kluczu publicznym.</span><span class="sxs-lookup"><span data-stu-id="b248e-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="b248e-110">określoną Wskaźnik do algorytmu używany do mieszania plików w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b248e-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="b248e-111">określoną Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="b248e-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b248e-112">podczas Rozmiar, w postaci szerokich znaków, z `szName` .</span><span class="sxs-lookup"><span data-stu-id="b248e-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b248e-113">określoną Liczba znaków dwubajtowych, które są w rzeczywistości zwracane `szName` .</span><span class="sxs-lookup"><span data-stu-id="b248e-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="b248e-114">określoną Wskaźnik do struktury ASSEMBLYMETADATA, która zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="b248e-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="b248e-115">określoną Flagi opisujące metadane zastosowane do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b248e-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="b248e-116">Ta wartość jest kombinacją co najmniej jednej wartości [CorAssemblyFlags —](corassemblyflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b248e-116">This value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b248e-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b248e-117">Requirements</span></span>  
 <span data-ttu-id="b248e-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b248e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b248e-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b248e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b248e-120">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b248e-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b248e-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b248e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b248e-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b248e-122">See also</span></span>

- [<span data-ttu-id="b248e-123">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b248e-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
