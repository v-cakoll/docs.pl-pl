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
ms.openlocfilehash: ada126b41f1c634f7d8daa58480406ac26f92377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177903"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="f738a-102">ICeeGen::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="f738a-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="f738a-103">Pobiera ciąg przechowywany przy określonym względnym adresie wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="f738a-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="f738a-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="f738a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f738a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f738a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f738a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f738a-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="f738a-107">[w] Względny adres wirtualny ciągu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="f738a-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="f738a-108">[na zewnątrz] Zwrócony ciąg.</span><span class="sxs-lookup"><span data-stu-id="f738a-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f738a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f738a-109">Requirements</span></span>  
 <span data-ttu-id="f738a-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f738a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f738a-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="f738a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f738a-112">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f738a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f738a-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f738a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f738a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f738a-114">See also</span></span>

- [<span data-ttu-id="f738a-115">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f738a-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
