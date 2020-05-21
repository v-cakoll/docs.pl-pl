---
title: ICorRuntimeHost::SwitchInLogicalThreadState — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
ms.openlocfilehash: d830635b911fa5d80382e432f283c455c41af7a8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762685"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="edf5a-102">ICorRuntimeHost::SwitchInLogicalThreadState — Metoda</span><span class="sxs-lookup"><span data-stu-id="edf5a-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="edf5a-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="edf5a-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edf5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="edf5a-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edf5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="edf5a-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="edf5a-106">podczas Plik cookie wskazujący włókna do użycia.</span><span class="sxs-lookup"><span data-stu-id="edf5a-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edf5a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edf5a-107">Requirements</span></span>  
 <span data-ttu-id="edf5a-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edf5a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edf5a-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="edf5a-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="edf5a-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="edf5a-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="edf5a-111">**Wersja .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="edf5a-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf5a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edf5a-112">See also</span></span>

- [<span data-ttu-id="edf5a-113">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="edf5a-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
