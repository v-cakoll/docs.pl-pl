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
ms.openlocfilehash: 99eef11c294dbb17b30b2ef28e65999d4d60f817
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008332"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="2fedc-102">ICeeGen::GetMethodBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="2fedc-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="2fedc-103">Pobiera bufor odpowiedniego rozmiaru dla metody pod określonym względnym adresem wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="2fedc-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="2fedc-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="2fedc-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fedc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fedc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fedc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fedc-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="2fedc-107">podczas Względny adres wirtualny metody, dla której ma zostać zwrócony bufor.</span><span class="sxs-lookup"><span data-stu-id="2fedc-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="2fedc-108">określoną Wskaźnik do zwróconego buforu.</span><span class="sxs-lookup"><span data-stu-id="2fedc-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fedc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2fedc-109">Requirements</span></span>  
 <span data-ttu-id="2fedc-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fedc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fedc-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2fedc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2fedc-112">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2fedc-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2fedc-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fedc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fedc-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fedc-114">See also</span></span>

- [<span data-ttu-id="2fedc-115">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2fedc-115">ICeeGen Interface</span></span>](iceegen-interface.md)
