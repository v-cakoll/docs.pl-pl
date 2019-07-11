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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 984ec5dea757971081ce05c858788473a0f616e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775275"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="3a6ce-102">IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a6ce-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="3a6ce-103">Modyfikuje określonego `AssemblyRef` struktury metadanych.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a6ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a6ce-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3a6ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a6ce-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="3a6ce-106">[in] Token metadanych, który określa `AssemblyRef` struktury metadanych do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="3a6ce-107">[in] Klucz publiczny wydawcy przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="3a6ce-108">[in] Rozmiar w bajtach `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="3a6ce-109">[in] Nazwa tekstowych zrozumiałych zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="3a6ce-110">[in] Wskaźnik na wystąpienie assemblymetadata —, który zawiera informacje o wersji, platformy i ustawienia regionalne dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="3a6ce-111">[in] Wskaźnik do danych wyznaczania wartości skrótu, skojarzone z zestawem.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="3a6ce-112">[in] Rozmiar w bajtach `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="3a6ce-113">[in] Bitowa kombinacja [assemblyrefflags —](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) wartości, które określają atrybuty przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a6ce-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a6ce-114">Remarks</span></span>  
 <span data-ttu-id="3a6ce-115">Aby utworzyć `AssemblyRef` struktury metadanych, użyj [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a6ce-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a6ce-116">Requirements</span></span>  
 <span data-ttu-id="3a6ce-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a6ce-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a6ce-118">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3a6ce-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a6ce-119">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a6ce-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a6ce-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a6ce-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a6ce-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a6ce-121">See also</span></span>

- [<span data-ttu-id="3a6ce-122">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a6ce-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
