---
title: "IMetaDataAssemblyEmit::SetExportedTypeProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bebcf827488912431cb0f94f5527d3445fc41125
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="5c7e4-102">IMetaDataAssemblyEmit::SetExportedTypeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c7e4-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="5c7e4-103">Modyfikuje określony `ExportedType` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="5c7e4-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c7e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c7e4-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c7e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c7e4-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="5c7e4-106">[in] Token metadanych, który określa `ExportedType` struktura metadanych ma być zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="5c7e4-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="5c7e4-107">[in] Token typu `File`, `AssemblyRef`, lub `ExportedType`, który określa sposób implementacji tego typu.</span><span class="sxs-lookup"><span data-stu-id="5c7e4-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="5c7e4-108">[in] `TypeDef` Token występujący w odwołaniu w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="5c7e4-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="5c7e4-109">[in] Bitowe połączenie wartości, które określają atrybuty typu.</span><span class="sxs-lookup"><span data-stu-id="5c7e4-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c7e4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c7e4-110">Remarks</span></span>  
 <span data-ttu-id="5c7e4-111">Aby utworzyć `ExportedType` metadanych struktury, użyj [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="5c7e4-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c7e4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c7e4-112">Requirements</span></span>  
 <span data-ttu-id="5c7e4-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c7e4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c7e4-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c7e4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c7e4-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c7e4-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c7e4-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c7e4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c7e4-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c7e4-117">See Also</span></span>  
 [<span data-ttu-id="5c7e4-118">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="5c7e4-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
