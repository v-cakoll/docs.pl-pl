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
ms.openlocfilehash: a6e7aa845f104ef734f039d46e1eeaba5fd01c73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704092"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="c4947-102">ICorPublishProcess::GetDisplayName — Metoda</span><span class="sxs-lookup"><span data-stu-id="c4947-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="c4947-103">Pobiera pełną ścieżkę pliku wykonywalnego procesu odwołuje się ten [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c4947-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4947-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4947-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4947-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4947-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c4947-106">[in] Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c4947-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c4947-107">[out] Liczba znaków dwubajtowych zwracane w `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c4947-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="c4947-108">[out] Tablica do przechowywania nazwy, łącznie z pełną ścieżkę pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c4947-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="c4947-109">Nazwa jest zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="c4947-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4947-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4947-110">Requirements</span></span>  
 <span data-ttu-id="c4947-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4947-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4947-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="c4947-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c4947-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4947-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4947-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4947-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4947-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4947-115">See also</span></span>

- [<span data-ttu-id="c4947-116">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="c4947-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
