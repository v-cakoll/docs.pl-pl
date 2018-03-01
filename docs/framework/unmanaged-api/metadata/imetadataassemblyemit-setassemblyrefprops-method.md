---
title: "IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 446137d28fdd64d7f9e5c84cc57e9ec967982430
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="95d74-102">IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="95d74-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="95d74-103">Modyfikuje określony `AssemblyRef` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="95d74-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95d74-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="95d74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95d74-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="95d74-106">[in] Token metadanych, który określa `AssemblyRef` struktura metadanych ma być zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="95d74-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="95d74-107">[in] Klucz publiczny wydawcy przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="95d74-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="95d74-108">[in] Wyrażony w bajtach rozmiar `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="95d74-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="95d74-109">[in] Tekst zrozumiałą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="95d74-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="95d74-110">[in] Wskaźnik do wystąpienia assemblymetadata —, który zawiera informacje o wersji platformy i ustawień regionalnych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="95d74-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="95d74-111">[in] Wskaźnik do wyznaczania wartości skrótu skojarzonych z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="95d74-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="95d74-112">[in] Wyrażony w bajtach rozmiar `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="95d74-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="95d74-113">[in] Bitowe połączenie [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) wartości, które określają atrybuty przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="95d74-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95d74-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95d74-114">Remarks</span></span>  
 <span data-ttu-id="95d74-115">Aby utworzyć `AssemblyRef` metadanych struktury, użyj [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="95d74-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95d74-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95d74-116">Requirements</span></span>  
 <span data-ttu-id="95d74-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95d74-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95d74-118">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="95d74-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95d74-119">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95d74-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95d74-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95d74-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d74-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95d74-121">See Also</span></span>  
 [<span data-ttu-id="95d74-122">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="95d74-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
