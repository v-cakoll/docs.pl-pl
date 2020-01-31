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
ms.openlocfilehash: fcf0ab73c79a5fa116a89cdfcc2e73b17d9eabfc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785493"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="7952d-102">ICLRDataTarget::GetImageBase — Metoda</span><span class="sxs-lookup"><span data-stu-id="7952d-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="7952d-103">Pobiera adres pamięci podstawowej określonego obrazu.</span><span class="sxs-lookup"><span data-stu-id="7952d-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7952d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7952d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7952d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7952d-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="7952d-106">podczas Nazwa pliku obrazu, łącznie z jego ścieżką.</span><span class="sxs-lookup"><span data-stu-id="7952d-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="7952d-107">określoną Wskaźnik do CLRDATA_ADDRESS, w którym przechowywany jest podstawowy adres obrazu.</span><span class="sxs-lookup"><span data-stu-id="7952d-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7952d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7952d-108">Remarks</span></span>  
 <span data-ttu-id="7952d-109">Nazwa pliku obrazu może być nieścieżką lub nie może mieć ścieżki.</span><span class="sxs-lookup"><span data-stu-id="7952d-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="7952d-110">Jeśli ścieżka jest określona, dopasowywanie jest wykonywane na całej ścieżce; w przeciwnym razie dopasowanie jest wykonywane tylko na nazwie pliku.</span><span class="sxs-lookup"><span data-stu-id="7952d-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7952d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7952d-111">Requirements</span></span>  
 <span data-ttu-id="7952d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7952d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7952d-113">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="7952d-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7952d-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7952d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7952d-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7952d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7952d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7952d-116">See also</span></span>

- [<span data-ttu-id="7952d-117">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="7952d-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
