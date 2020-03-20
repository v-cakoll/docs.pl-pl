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
ms.openlocfilehash: 4c914e00987053b1c1e9e00bf8e54632175e1de8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178159"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="f34ce-102">GetRealProcAddress — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f34ce-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="f34ce-103">Pobiera adres określonej funkcji, która jest eksportowana z najnowszej zainstalowanej wersji środowiska wykonawczego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f34ce-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="f34ce-104">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f34ce-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f34ce-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f34ce-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f34ce-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f34ce-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="f34ce-107">[w] Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="f34ce-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="f34ce-108">[na zewnątrz] Lokalizacja, która odbiera wskaźnik do adresu funkcji.</span><span class="sxs-lookup"><span data-stu-id="f34ce-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f34ce-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f34ce-109">Return Value</span></span>  
 <span data-ttu-id="f34ce-110">Ta metoda zwraca standardowe kody błędów modelu com (Component Object Model), zgodnie z definicją w pliku WinError.h, oprócz następujących wartości zdefiniowanych w pliku CorError.h.</span><span class="sxs-lookup"><span data-stu-id="f34ce-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="f34ce-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="f34ce-111">Return code</span></span>|<span data-ttu-id="f34ce-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f34ce-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f34ce-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f34ce-113">S_OK</span></span>|<span data-ttu-id="f34ce-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f34ce-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="f34ce-115">E_pointer</span><span class="sxs-lookup"><span data-stu-id="f34ce-115">E_POINTER</span></span>|<span data-ttu-id="f34ce-116">`ppv`jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="f34ce-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="f34ce-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="f34ce-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="f34ce-118">Funkcja nie jest eksportowana ze środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="f34ce-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f34ce-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f34ce-119">Requirements</span></span>  
 <span data-ttu-id="f34ce-120">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f34ce-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f34ce-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f34ce-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f34ce-122">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f34ce-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f34ce-123">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f34ce-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f34ce-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f34ce-124">See also</span></span>

- [<span data-ttu-id="f34ce-125">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="f34ce-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
