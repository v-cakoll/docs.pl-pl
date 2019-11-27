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
ms.openlocfilehash: ae682c354a7a5188611b103008a3e18f8d821260
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431939"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="00628-102">IMetaDataAssemblyEmit::SetExportedTypeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="00628-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="00628-103">Modyfikuje określoną strukturę metadanych `ExportedType`.</span><span class="sxs-lookup"><span data-stu-id="00628-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00628-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00628-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00628-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00628-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="00628-106">podczas Token metadanych określający strukturę metadanych `ExportedType`, która ma zostać zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="00628-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="00628-107">podczas Token, typu `File`, `AssemblyRef`lub `ExportedType`, który określa sposób implementowania tego typu.</span><span class="sxs-lookup"><span data-stu-id="00628-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="00628-108">podczas Token `TypeDef`, do którego odwołuje się plik kodu.</span><span class="sxs-lookup"><span data-stu-id="00628-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="00628-109">podczas Bitowa kombinacja wartości, które określają atrybuty typu.</span><span class="sxs-lookup"><span data-stu-id="00628-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00628-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00628-110">Remarks</span></span>  
 <span data-ttu-id="00628-111">Aby utworzyć `ExportedType` strukturę metadanych, użyj metody [IMetaDataAssemblyEmit::D efineexportedtype](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="00628-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00628-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00628-112">Requirements</span></span>  
 <span data-ttu-id="00628-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00628-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00628-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="00628-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00628-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="00628-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00628-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00628-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00628-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00628-117">See also</span></span>

- [<span data-ttu-id="00628-118">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="00628-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
