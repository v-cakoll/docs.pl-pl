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
ms.openlocfilehash: 34636f1ca8e42c452aa41f6145d439a26f01b0a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436396"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="0b164-102">ICeeGen::AllocateMethodBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b164-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="0b164-103">Tworzy bufor o określonym rozmiarze dla metody i pobiera względny adres wirtualny metody.</span><span class="sxs-lookup"><span data-stu-id="0b164-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="0b164-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="0b164-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b164-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b164-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b164-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b164-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="0b164-107">podczas Długość buforu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="0b164-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="0b164-108">określoną Zwrócony bufor.</span><span class="sxs-lookup"><span data-stu-id="0b164-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="0b164-109">określoną Względny adres wirtualny metody.</span><span class="sxs-lookup"><span data-stu-id="0b164-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b164-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b164-110">Requirements</span></span>  
 <span data-ttu-id="0b164-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b164-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b164-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0b164-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b164-113">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0b164-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b164-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b164-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b164-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b164-115">See also</span></span>

- [<span data-ttu-id="0b164-116">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b164-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
