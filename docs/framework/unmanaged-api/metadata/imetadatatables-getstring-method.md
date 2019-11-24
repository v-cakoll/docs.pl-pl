---
title: IMetaDataTables::GetString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 055499230f500cb7249746e1acbf46b4548d25bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426799"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="b46d7-102">IMetaDataTables::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="b46d7-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="b46d7-103">Gets the string at the specified index from the table column in the current reference scope.</span><span class="sxs-lookup"><span data-stu-id="b46d7-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b46d7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b46d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b46d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b46d7-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="b46d7-106">[in] The index at which to start to search for the next value.</span><span class="sxs-lookup"><span data-stu-id="b46d7-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="b46d7-107">[out] A pointer to a pointer to the returned string value.</span><span class="sxs-lookup"><span data-stu-id="b46d7-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b46d7-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b46d7-108">Requirements</span></span>  
 <span data-ttu-id="b46d7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b46d7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b46d7-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b46d7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b46d7-111">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b46d7-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b46d7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b46d7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b46d7-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b46d7-113">See also</span></span>

- [<span data-ttu-id="b46d7-114">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="b46d7-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="b46d7-115">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b46d7-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
