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
ms.openlocfilehash: 6bbf8366054c58543444a4b710a687198f365e6e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617207"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="723fc-102">GetRealProcAddress — Funkcja</span><span class="sxs-lookup"><span data-stu-id="723fc-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="723fc-103">Pobiera adres określonej funkcji wyeksportowanej z najnowszej zainstalowanej wersji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="723fc-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="723fc-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="723fc-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="723fc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="723fc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="723fc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="723fc-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="723fc-107">podczas Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="723fc-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="723fc-108">określoną Lokalizacja, która otrzymuje wskaźnik na adres funkcji.</span><span class="sxs-lookup"><span data-stu-id="723fc-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="723fc-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="723fc-109">Return Value</span></span>  
 <span data-ttu-id="723fc-110">Ta metoda zwraca kody błędów standardowego Component Object Model (COM), jak zdefiniowano w WinError. h, oprócz następujących wartości zdefiniowanych w CorError. h.</span><span class="sxs-lookup"><span data-stu-id="723fc-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="723fc-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="723fc-111">Return code</span></span>|<span data-ttu-id="723fc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="723fc-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="723fc-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="723fc-113">S_OK</span></span>|<span data-ttu-id="723fc-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="723fc-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="723fc-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="723fc-115">E_POINTER</span></span>|<span data-ttu-id="723fc-116">`ppv`jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="723fc-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="723fc-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="723fc-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="723fc-118">Funkcja nie została wyeksportowana z środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="723fc-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="723fc-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="723fc-119">Requirements</span></span>  
 <span data-ttu-id="723fc-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="723fc-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="723fc-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="723fc-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="723fc-122">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="723fc-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="723fc-123">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="723fc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723fc-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="723fc-124">See also</span></span>

- [<span data-ttu-id="723fc-125">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="723fc-125">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
