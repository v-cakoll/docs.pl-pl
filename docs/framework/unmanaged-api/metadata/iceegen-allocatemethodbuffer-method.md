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
ms.openlocfilehash: 8dc7f439cac56c2d55916ff8631ec3095c67680d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008888"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="bfb1b-102">ICeeGen::AllocateMethodBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="bfb1b-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="bfb1b-103">Tworzy bufor o określonym rozmiarze dla metody i pobiera względny adres wirtualny metody.</span><span class="sxs-lookup"><span data-stu-id="bfb1b-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="bfb1b-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="bfb1b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb1b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bfb1b-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfb1b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfb1b-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="bfb1b-107">podczas Długość buforu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb1b-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="bfb1b-108">określoną Zwrócony bufor.</span><span class="sxs-lookup"><span data-stu-id="bfb1b-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="bfb1b-109">określoną Względny adres wirtualny metody.</span><span class="sxs-lookup"><span data-stu-id="bfb1b-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfb1b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bfb1b-110">Requirements</span></span>  
 <span data-ttu-id="bfb1b-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfb1b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfb1b-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bfb1b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bfb1b-113">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bfb1b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bfb1b-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfb1b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb1b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bfb1b-115">See also</span></span>

- [<span data-ttu-id="bfb1b-116">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bfb1b-116">ICeeGen Interface</span></span>](iceegen-interface.md)
