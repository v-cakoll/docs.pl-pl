---
title: ICeeGen::GetString — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: b7b15261d825c1bd5f217c4cecd82ed36a716d0e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008264"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="398ff-102">ICeeGen::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="398ff-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="398ff-103">Pobiera ciąg przechowywany w określonym względnym adresie wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="398ff-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="398ff-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="398ff-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="398ff-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="398ff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="398ff-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="398ff-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="398ff-107">podczas Względny adres wirtualny ciągu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="398ff-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="398ff-108">określoną Zwrócony ciąg.</span><span class="sxs-lookup"><span data-stu-id="398ff-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="398ff-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="398ff-109">Requirements</span></span>  
 <span data-ttu-id="398ff-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="398ff-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="398ff-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="398ff-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="398ff-112">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="398ff-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="398ff-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="398ff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="398ff-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="398ff-114">See also</span></span>

- [<span data-ttu-id="398ff-115">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="398ff-115">ICeeGen Interface</span></span>](iceegen-interface.md)
