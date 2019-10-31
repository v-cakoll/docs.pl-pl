---
title: GetRealProcAddress — Funkcja
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
ms.openlocfilehash: 9dffc3d197b05bb71443aa60c101260daabadadd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136394"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="8b5e6-102">GetRealProcAddress — Funkcja</span><span class="sxs-lookup"><span data-stu-id="8b5e6-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="8b5e6-103">Pobiera adres określonej funkcji wyeksportowanej z najnowszej zainstalowanej wersji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="8b5e6-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="8b5e6-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8b5e6-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5e6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b5e6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b5e6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b5e6-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="8b5e6-107">podczas Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="8b5e6-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="8b5e6-108">określoną Lokalizacja, która otrzymuje wskaźnik na adres funkcji.</span><span class="sxs-lookup"><span data-stu-id="8b5e6-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b5e6-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8b5e6-109">Return Value</span></span>  
 <span data-ttu-id="8b5e6-110">Ta metoda zwraca kody błędów standardowego Component Object Model (COM), jak zdefiniowano w WinError. h, oprócz następujących wartości zdefiniowanych w CorError. h.</span><span class="sxs-lookup"><span data-stu-id="8b5e6-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="8b5e6-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="8b5e6-111">Return code</span></span>|<span data-ttu-id="8b5e6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8b5e6-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8b5e6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b5e6-113">S_OK</span></span>|<span data-ttu-id="8b5e6-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8b5e6-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="8b5e6-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8b5e6-115">E_POINTER</span></span>|<span data-ttu-id="8b5e6-116">`ppv` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8b5e6-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="8b5e6-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="8b5e6-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="8b5e6-118">Funkcja nie została wyeksportowana z środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8b5e6-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b5e6-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b5e6-119">Requirements</span></span>  
 <span data-ttu-id="8b5e6-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b5e6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b5e6-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8b5e6-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b5e6-122">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8b5e6-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b5e6-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b5e6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5e6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b5e6-124">See also</span></span>

- [<span data-ttu-id="8b5e6-125">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="8b5e6-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
