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
ms.openlocfilehash: f56376d4400f4e24aefe2d1e5d4ad504b1d281cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="6a494-102">ICeeGen::AllocateMethodBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a494-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="6a494-103">Tworzy buforu o określonym rozmiarze metody i pobiera adres względny wirtualnej metody.</span><span class="sxs-lookup"><span data-stu-id="6a494-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="6a494-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="6a494-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a494-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a494-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a494-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a494-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="6a494-107">[in] Długość buforu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="6a494-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="6a494-108">[out] Zwrócony buforu.</span><span class="sxs-lookup"><span data-stu-id="6a494-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="6a494-109">[out] Wirtualny adres względny metody.</span><span class="sxs-lookup"><span data-stu-id="6a494-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a494-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a494-110">Requirements</span></span>  
 <span data-ttu-id="6a494-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a494-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a494-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6a494-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a494-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a494-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a494-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a494-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a494-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a494-115">See Also</span></span>  
 [<span data-ttu-id="6a494-116">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="6a494-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
