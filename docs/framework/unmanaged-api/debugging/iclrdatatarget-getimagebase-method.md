---
title: "ICLRDataTarget::GetImageBase — Metoda"
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
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 504c3ce7115cbab11d0510eaa2ebb0fdd9f1888b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="2b929-102">ICLRDataTarget::GetImageBase — Metoda</span><span class="sxs-lookup"><span data-stu-id="2b929-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="2b929-103">Pobiera adres podstawowy pamięci określonego obrazu.</span><span class="sxs-lookup"><span data-stu-id="2b929-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b929-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b929-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b929-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b929-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="2b929-106">[in] Nazwa pliku obrazu, wraz ze ścieżką.</span><span class="sxs-lookup"><span data-stu-id="2b929-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="2b929-107">[out] Wskaźnik do CLRDATA_ADDRESS, która przechowuje adres podstawowy obraz.</span><span class="sxs-lookup"><span data-stu-id="2b929-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b929-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b929-108">Remarks</span></span>  
 <span data-ttu-id="2b929-109">Nazwa pliku obrazu może lub nie ma ścieżki.</span><span class="sxs-lookup"><span data-stu-id="2b929-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="2b929-110">Jeśli ścieżka jest określona, dopasowywanie odbywa się na całej ścieżce; w przeciwnym razie dopasowania odbywa się tylko na nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="2b929-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b929-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b929-111">Requirements</span></span>  
 <span data-ttu-id="2b929-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b929-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b929-113">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2b929-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2b929-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b929-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b929-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b929-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b929-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b929-116">See Also</span></span>  
 [<span data-ttu-id="2b929-117">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b929-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
