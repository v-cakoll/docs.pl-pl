---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: fb381a872cbeb787da0c6920f2cdeef434fb33ea
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008095"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="65762-102">IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="65762-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="65762-103">Modyfikuje określoną `AssemblyRef` strukturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="65762-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65762-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65762-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65762-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65762-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="65762-106">podczas Token metadanych określający `AssemblyRef` strukturę metadanych, która ma zostać zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="65762-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="65762-107">podczas Klucz publiczny wydawcy przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="65762-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="65762-108">podczas Rozmiar w bajtach `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="65762-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="65762-109">podczas Nazwa tekstu do odczytania przez człowieka.</span><span class="sxs-lookup"><span data-stu-id="65762-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="65762-110">podczas Wskaźnik do wystąpienia ASSEMBLYMETADATA, który zawiera wersję, platformę i informacje o ustawieniach regionalnych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="65762-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="65762-111">podczas Wskaźnik do danych skrótu skojarzonych z zestawem.</span><span class="sxs-lookup"><span data-stu-id="65762-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="65762-112">podczas Rozmiar w bajtach `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="65762-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="65762-113">podczas Bitowa kombinacja wartości [AssemblyRefFlags —](assemblyrefflags-enumeration.md) , które określają atrybuty przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="65762-113">[in] A bitwise combination of [AssemblyRefFlags](assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65762-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65762-114">Remarks</span></span>  
 <span data-ttu-id="65762-115">Aby utworzyć `AssemblyRef` strukturę metadanych, użyj metody [IMetaDataAssemblyEmit::D efineassemblyref](imetadataassemblyemit-defineassemblyref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="65762-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65762-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65762-116">Requirements</span></span>  
 <span data-ttu-id="65762-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65762-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65762-118">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="65762-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65762-119">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="65762-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65762-120">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65762-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65762-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65762-121">See also</span></span>

- [<span data-ttu-id="65762-122">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="65762-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
