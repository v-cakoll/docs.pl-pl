---
title: ICorPublishProcess::GetDisplayName — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 815f2e2f695837c973210a21ab3631ef307c23d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423640"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="53e30-102">ICorPublishProcess::GetDisplayName — Metoda</span><span class="sxs-lookup"><span data-stu-id="53e30-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="53e30-103">Pobiera pełną ścieżkę do pliku wykonywalnego procesu, który odwołuje się ten [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="53e30-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e30-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53e30-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53e30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53e30-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="53e30-106">[in] Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="53e30-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="53e30-107">[out] Liczba zwracanych w znaki dwubajtowe `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="53e30-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="53e30-108">[out] Tablica, aby zapisać nazwę, łącznie z pełną ścieżką do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="53e30-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="53e30-109">Nazwa jest zerem.</span><span class="sxs-lookup"><span data-stu-id="53e30-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e30-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53e30-110">Requirements</span></span>  
 <span data-ttu-id="53e30-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e30-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e30-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="53e30-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="53e30-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53e30-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53e30-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e30-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e30-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53e30-115">See Also</span></span>  
 [<span data-ttu-id="53e30-116">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="53e30-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
