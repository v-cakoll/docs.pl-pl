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
ms.openlocfilehash: 14ea8dab2c4258fe490ef362fd527d80bd8a0178
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746104"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="c930f-102">ICeeGen::GetMethodBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="c930f-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="c930f-103">Pobiera odpowiedni rozmiar buforu dla metody o określonym względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="c930f-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="c930f-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="c930f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c930f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c930f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c930f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c930f-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="c930f-107">[in] Wirtualny adres względny metody, dla której ma zostać zwrócone do buforu.</span><span class="sxs-lookup"><span data-stu-id="c930f-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="c930f-108">[out] Wskaźnik do buforu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="c930f-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c930f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c930f-109">Requirements</span></span>  
 <span data-ttu-id="c930f-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c930f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c930f-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c930f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c930f-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c930f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c930f-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c930f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c930f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c930f-114">See also</span></span>

- [<span data-ttu-id="c930f-115">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="c930f-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
