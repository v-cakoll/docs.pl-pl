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
ms.openlocfilehash: 1855c73849c35bf709b0af261a88e6cd7a40abfb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008303"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="a3d97-102">ICeeGen::GetSectionDataLen — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3d97-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="a3d97-103">Pobiera długość określonej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a3d97-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="a3d97-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="a3d97-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3d97-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3d97-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3d97-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3d97-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="a3d97-107">podczas Sekcja danych, której długość zostanie pobrana.</span><span class="sxs-lookup"><span data-stu-id="a3d97-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="a3d97-108">określoną Zwrócona długość określonej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a3d97-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3d97-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3d97-109">Remarks</span></span>  
 <span data-ttu-id="a3d97-110">Wywołanie `GetSectionDataLen` tylko wtedy, gdy istnieją specjalne wymagania sekcji, które nie są obsługiwane przez inne metody.</span><span class="sxs-lookup"><span data-stu-id="a3d97-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3d97-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3d97-111">Requirements</span></span>  
 <span data-ttu-id="a3d97-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3d97-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3d97-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a3d97-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3d97-114">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a3d97-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a3d97-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3d97-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d97-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3d97-116">See also</span></span>

- [<span data-ttu-id="a3d97-117">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a3d97-117">ICeeGen Interface</span></span>](iceegen-interface.md)
