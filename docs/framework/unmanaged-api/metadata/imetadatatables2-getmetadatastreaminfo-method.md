---
title: IMetaDataTables2::GetMetaDataStreamInfo — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
ms.openlocfilehash: 279e34689169d31ad89772e90155e7f50bdbac08
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426215"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="ea307-102">IMetaDataTables2::GetMetaDataStreamInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea307-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="ea307-103">Gets the name, size, and contents of the metadata stream at the specified index.</span><span class="sxs-lookup"><span data-stu-id="ea307-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea307-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea307-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea307-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea307-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="ea307-106">[in] The index of the requested metadata stream.</span><span class="sxs-lookup"><span data-stu-id="ea307-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="ea307-107">[out] A pointer to the name of the stream.</span><span class="sxs-lookup"><span data-stu-id="ea307-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="ea307-108">[out] A pointer to the metadata stream.</span><span class="sxs-lookup"><span data-stu-id="ea307-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="ea307-109">[out] The size, in bytes, of `ppv`.</span><span class="sxs-lookup"><span data-stu-id="ea307-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea307-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea307-110">Requirements</span></span>  
 <span data-ttu-id="ea307-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea307-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea307-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ea307-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea307-113">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea307-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea307-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea307-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea307-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea307-115">See also</span></span>

- [<span data-ttu-id="ea307-116">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea307-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="ea307-117">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea307-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
