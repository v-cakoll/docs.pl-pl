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
ms.openlocfilehash: a093b18f72cc99c53951b3dc588ce0cff3c7fefd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442611"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="07832-102">ICeeGen::GetMethodBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="07832-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="07832-103">Pobiera odpowiedni rozmiar buforu dla metody pod określonym adresem wirtualnego względną.</span><span class="sxs-lookup"><span data-stu-id="07832-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="07832-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="07832-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07832-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="07832-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07832-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="07832-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="07832-107">[in] Wirtualny adres względny metody, dla którego ma zostać zwrócona w buforze.</span><span class="sxs-lookup"><span data-stu-id="07832-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="07832-108">[out] Wskaźnik do buforu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="07832-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07832-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07832-109">Requirements</span></span>  
 <span data-ttu-id="07832-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07832-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07832-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="07832-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07832-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07832-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="07832-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07832-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07832-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07832-114">See Also</span></span>  
 [<span data-ttu-id="07832-115">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="07832-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
