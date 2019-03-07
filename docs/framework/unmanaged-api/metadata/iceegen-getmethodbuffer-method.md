---
title: ICeeGen::GetMethodBuffer — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d8ccaa1b03ae1afc87eb7b0a66dd517bba8fcf8a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497473"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="e3264-102">ICeeGen::GetMethodBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3264-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="e3264-103">Pobiera odpowiedni rozmiar buforu dla metody o określonym względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="e3264-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="e3264-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="e3264-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3264-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3264-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3264-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3264-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="e3264-107">[in] Wirtualny adres względny metody, dla której ma zostać zwrócone do buforu.</span><span class="sxs-lookup"><span data-stu-id="e3264-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="e3264-108">[out] Wskaźnik do buforu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e3264-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3264-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3264-109">Requirements</span></span>  
 <span data-ttu-id="e3264-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3264-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3264-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e3264-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3264-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3264-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3264-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3264-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3264-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3264-114">See also</span></span>
- [<span data-ttu-id="e3264-115">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3264-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
