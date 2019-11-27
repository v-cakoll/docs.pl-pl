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
ms.openlocfilehash: 8c8ecab9d957e72bb6c0817af07c863fcff97cde
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436327"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="31223-102">ICeeGen::GetMethodBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="31223-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="31223-103">Pobiera bufor odpowiedniego rozmiaru dla metody pod określonym względnym adresem wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="31223-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="31223-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="31223-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31223-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="31223-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31223-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="31223-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="31223-107">podczas Względny adres wirtualny metody, dla której ma zostać zwrócony bufor.</span><span class="sxs-lookup"><span data-stu-id="31223-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="31223-108">określoną Wskaźnik do zwróconego buforu.</span><span class="sxs-lookup"><span data-stu-id="31223-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31223-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31223-109">Requirements</span></span>  
 <span data-ttu-id="31223-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31223-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31223-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="31223-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31223-112">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="31223-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31223-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31223-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31223-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31223-114">See also</span></span>

- [<span data-ttu-id="31223-115">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="31223-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
