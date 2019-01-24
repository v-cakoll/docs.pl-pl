---
title: IMetaDataAssemblyEmit::SetExportedTypeProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bdd5e92ce7423fbbe0708f8a35368b871508a70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493433"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="d8ced-102">IMetaDataAssemblyEmit::SetExportedTypeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="d8ced-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="d8ced-103">Modyfikuje określonego `ExportedType` struktury metadanych.</span><span class="sxs-lookup"><span data-stu-id="d8ced-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ced-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8ced-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8ced-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8ced-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="d8ced-106">[in] Token metadanych, który określa `ExportedType` struktury metadanych do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="d8ced-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="d8ced-107">[in] Token typu `File`, `AssemblyRef`, lub `ExportedType`, który określa sposób implementacji tego typu.</span><span class="sxs-lookup"><span data-stu-id="d8ced-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="d8ced-108">[in] `TypeDef` Token odwołania w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="d8ced-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="d8ced-109">[in] Bitowa kombinacja wartości, które określają atrybuty typu.</span><span class="sxs-lookup"><span data-stu-id="d8ced-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8ced-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8ced-110">Remarks</span></span>  
 <span data-ttu-id="d8ced-111">Aby utworzyć `ExportedType` struktury metadanych, użyj [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d8ced-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ced-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d8ced-112">Requirements</span></span>  
 <span data-ttu-id="d8ced-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ced-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ced-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d8ced-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8ced-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8ced-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8ced-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ced-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ced-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8ced-117">See also</span></span>
- [<span data-ttu-id="d8ced-118">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="d8ced-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
