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
ms.openlocfilehash: 77e801b048709949c384f642fc0d0ecb5d7eb512
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178387"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="0b067-102">ICorPublishProcess::GetDisplayName — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b067-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="0b067-103">Pobiera pełną ścieżkę pliku wykonywalnego dla procesu, do którego odwołuje się ten [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0b067-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b067-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b067-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b067-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b067-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0b067-106">[w] Rozmiar tablicy. `szName`</span><span class="sxs-lookup"><span data-stu-id="0b067-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0b067-107">[na zewnątrz] Liczba znaków szerokości zwróconych `szName` w tablicy.</span><span class="sxs-lookup"><span data-stu-id="0b067-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="0b067-108">[na zewnątrz] Tablica do przechowywania nazwy, w tym pełnej ścieżki, pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="0b067-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="0b067-109">Nazwa jest anulowana z wartością null.</span><span class="sxs-lookup"><span data-stu-id="0b067-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b067-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b067-110">Requirements</span></span>  
 <span data-ttu-id="0b067-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b067-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b067-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="0b067-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0b067-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b067-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b067-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b067-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b067-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b067-115">See also</span></span>

- [<span data-ttu-id="0b067-116">ICorPublishProcess — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0b067-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
