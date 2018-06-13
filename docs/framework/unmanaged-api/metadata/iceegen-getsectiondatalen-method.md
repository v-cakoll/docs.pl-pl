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
ms.openlocfilehash: b85cdee4a65e91c51fdb014bdcc4797b99214daf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446134"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="7b0fc-102">ICeeGen::GetSectionDataLen — Metoda</span><span class="sxs-lookup"><span data-stu-id="7b0fc-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="7b0fc-103">Pobiera długość określonej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7b0fc-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="7b0fc-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="7b0fc-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b0fc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b0fc-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b0fc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b0fc-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="7b0fc-107">[in] Sekcji danych, którego długość zostanie pobrany.</span><span class="sxs-lookup"><span data-stu-id="7b0fc-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="7b0fc-108">[out] Zwrócona długość określonej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7b0fc-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b0fc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b0fc-109">Remarks</span></span>  
 <span data-ttu-id="7b0fc-110">Wywołanie `GetSectionDataLen` tylko wtedy, gdy sekcja specjalne wymagania, które nie są obsługiwane za pomocą innych metod.</span><span class="sxs-lookup"><span data-stu-id="7b0fc-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b0fc-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b0fc-111">Requirements</span></span>  
 <span data-ttu-id="7b0fc-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b0fc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b0fc-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7b0fc-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b0fc-114">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7b0fc-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7b0fc-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b0fc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b0fc-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b0fc-116">See Also</span></span>  
 [<span data-ttu-id="7b0fc-117">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b0fc-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
