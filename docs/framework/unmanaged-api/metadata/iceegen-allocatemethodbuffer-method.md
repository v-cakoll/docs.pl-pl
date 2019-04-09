---
title: ICeeGen::AllocateMethodBuffer — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7be1bd2934fbb2e09a39c3042fa9ae314e89d629
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083767"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="b75f4-102">ICeeGen::AllocateMethodBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="b75f4-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="b75f4-103">Tworzy buforu rozmiaru określonego dla metody, a następnie pobiera adres względny wirtualnej metody.</span><span class="sxs-lookup"><span data-stu-id="b75f4-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="b75f4-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="b75f4-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b75f4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b75f4-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b75f4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b75f4-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="b75f4-107">[in] Długość buforu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="b75f4-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="b75f4-108">[out] Bufor zwrócone.</span><span class="sxs-lookup"><span data-stu-id="b75f4-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="b75f4-109">[out] Wirtualny adres względny metody.</span><span class="sxs-lookup"><span data-stu-id="b75f4-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b75f4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b75f4-110">Requirements</span></span>  
 <span data-ttu-id="b75f4-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b75f4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b75f4-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b75f4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b75f4-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b75f4-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="b75f4-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b75f4-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b75f4-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b75f4-115">See also</span></span>

- [<span data-ttu-id="b75f4-116">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b75f4-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
