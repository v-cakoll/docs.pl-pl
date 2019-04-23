---
title: ICLRDataTarget::GetImageBase — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e823911280f52e16c745c9c77fe17b49bd35dc0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129834"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="4ef0c-102">ICLRDataTarget::GetImageBase — Metoda</span><span class="sxs-lookup"><span data-stu-id="4ef0c-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="4ef0c-103">Pobiera adres podstawowy pamięci określonego obrazu.</span><span class="sxs-lookup"><span data-stu-id="4ef0c-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ef0c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ef0c-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ef0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ef0c-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="4ef0c-106">[in] Nazwa pliku obrazu, wraz ze ścieżką.</span><span class="sxs-lookup"><span data-stu-id="4ef0c-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="4ef0c-107">[out] Wskaźnik do CLRDATA_ADDRESS, która przechowuje adres podstawowy obrazu.</span><span class="sxs-lookup"><span data-stu-id="4ef0c-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ef0c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ef0c-108">Remarks</span></span>  
 <span data-ttu-id="4ef0c-109">Nazwa pliku obrazu może lub nie może być ścieżką.</span><span class="sxs-lookup"><span data-stu-id="4ef0c-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="4ef0c-110">Jeśli ścieżka jest określona, dopasowanie jest wykonywane na całej ścieżce; w przeciwnym razie dopasowanie jest wykonywane tylko na nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="4ef0c-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ef0c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ef0c-111">Requirements</span></span>  
 <span data-ttu-id="4ef0c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ef0c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ef0c-113">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4ef0c-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4ef0c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ef0c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ef0c-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ef0c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef0c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ef0c-116">See also</span></span>

- [<span data-ttu-id="4ef0c-117">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ef0c-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
