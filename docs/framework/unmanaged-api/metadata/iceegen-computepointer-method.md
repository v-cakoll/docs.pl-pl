---
title: ICeeGen::ComputePointer — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
ms.openlocfilehash: 206dcd3a0a82da9b6211c8c2045e4e9d3d991973
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008875"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="8270c-102">ICeeGen::ComputePointer — Metoda</span><span class="sxs-lookup"><span data-stu-id="8270c-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="8270c-103">Określa bufor dla określonej sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="8270c-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="8270c-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="8270c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8270c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8270c-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8270c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8270c-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="8270c-107">podczas Sekcja kodu, dla której ma zostać zwrócony bufor.</span><span class="sxs-lookup"><span data-stu-id="8270c-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="8270c-108">podczas Względny adres wirtualny metody, dla której ma zostać pobrany wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="8270c-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="8270c-109">określoną Wskaźnik do zwróconego buforu.</span><span class="sxs-lookup"><span data-stu-id="8270c-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8270c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8270c-110">Requirements</span></span>  
 <span data-ttu-id="8270c-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8270c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8270c-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8270c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8270c-113">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8270c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8270c-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8270c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8270c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8270c-115">See also</span></span>

- [<span data-ttu-id="8270c-116">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8270c-116">ICeeGen Interface</span></span>](iceegen-interface.md)
