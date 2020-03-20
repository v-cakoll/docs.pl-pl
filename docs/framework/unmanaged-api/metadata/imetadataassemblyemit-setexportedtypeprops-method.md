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
ms.openlocfilehash: dd1d6f1da6e49837eebd9356500f403c199b011b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177853"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="356aa-102">IMetaDataAssemblyEmit::SetExportedTypeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="356aa-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="356aa-103">Modyfikuje `ExportedType` strukturę określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="356aa-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="356aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="356aa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="356aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="356aa-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="356aa-106">[w] Token metadanych, który `ExportedType` określa strukturę metadanych, która ma zostać zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="356aa-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="356aa-107">[w] Token, typu `File`, `AssemblyRef`lub `ExportedType`, który określa, jak ten typ jest implementowany.</span><span class="sxs-lookup"><span data-stu-id="356aa-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="356aa-108">[w] Token, `TypeDef` do którego odwołuje się plik kodu.</span><span class="sxs-lookup"><span data-stu-id="356aa-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="356aa-109">[w] Bitowa kombinacja wartości określających atrybuty typu.</span><span class="sxs-lookup"><span data-stu-id="356aa-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="356aa-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="356aa-110">Remarks</span></span>  
 <span data-ttu-id="356aa-111">Aby utworzyć `ExportedType` strukturę metadanych, należy użyć [metody IMetaDataAssemblyEmit::DefineExportedType.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)</span><span class="sxs-lookup"><span data-stu-id="356aa-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="356aa-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="356aa-112">Requirements</span></span>  
 <span data-ttu-id="356aa-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="356aa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="356aa-114">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="356aa-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="356aa-115">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="356aa-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="356aa-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="356aa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356aa-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="356aa-117">See also</span></span>

- [<span data-ttu-id="356aa-118">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="356aa-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
