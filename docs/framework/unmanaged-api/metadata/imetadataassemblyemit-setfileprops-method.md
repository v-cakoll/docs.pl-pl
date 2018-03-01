---
title: "IMetaDataAssemblyEmit::SetFileProps — Metoda"
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
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc0f0b2cbc22a7e9d6dcac6e359f36f365d368af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="8ad15-102">IMetaDataAssemblyEmit::SetFileProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ad15-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="8ad15-103">Modyfikuje określony `File` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="8ad15-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad15-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ad15-104">Syntax</span></span>  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ad15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ad15-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="8ad15-106">[in] Token metadanych, który określa `File` struktura metadanych ma być zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="8ad15-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="8ad15-107">[in] Wskaźnik do wyznaczania wartości skrótu danych skojarzonych z plikiem.</span><span class="sxs-lookup"><span data-stu-id="8ad15-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="8ad15-108">[in] Wyrażony w bajtach rozmiar `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="8ad15-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="8ad15-109">[in] Bitowe połączenie [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) wartości, które określają różne atrybuty pliku.</span><span class="sxs-lookup"><span data-stu-id="8ad15-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ad15-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ad15-110">Remarks</span></span>  
 <span data-ttu-id="8ad15-111">Aby utworzyć `File` metadanych struktury, użyj [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8ad15-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ad15-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ad15-112">Requirements</span></span>  
 <span data-ttu-id="8ad15-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ad15-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ad15-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8ad15-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ad15-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ad15-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ad15-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ad15-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad15-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ad15-117">See Also</span></span>  
 [<span data-ttu-id="8ad15-118">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ad15-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
