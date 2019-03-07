---
title: ICeeGen::GetSectionDataLen — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3983916f56e8451e7628db3902001bd13f503114
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487931"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="48147-102">ICeeGen::GetSectionDataLen — Metoda</span><span class="sxs-lookup"><span data-stu-id="48147-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="48147-103">Pobiera długość określona sekcja.</span><span class="sxs-lookup"><span data-stu-id="48147-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="48147-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="48147-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48147-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="48147-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48147-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="48147-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="48147-107">[in] W sekcji danych, których długości mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="48147-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="48147-108">[out] Zwrócona długość określona sekcja.</span><span class="sxs-lookup"><span data-stu-id="48147-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48147-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48147-109">Remarks</span></span>  
 <span data-ttu-id="48147-110">Wywołaj `GetSectionDataLen` tylko wtedy, gdy masz sekcją wymagań, które nie są obsługiwane przy użyciu innych metod.</span><span class="sxs-lookup"><span data-stu-id="48147-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48147-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48147-111">Requirements</span></span>  
 <span data-ttu-id="48147-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48147-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48147-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="48147-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48147-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="48147-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48147-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48147-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48147-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48147-116">See also</span></span>
- [<span data-ttu-id="48147-117">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="48147-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
