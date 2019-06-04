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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40cd5b6298012ef4dc21987a2a2dbe95c02a0ff2
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490355"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="7d941-102">GetRealProcAddress — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7d941-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="7d941-103">Pobiera adres określonej funkcji, która została wyeksportowana z najnowszej zainstalowanej wersji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="7d941-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="7d941-104">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7d941-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d941-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d941-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d941-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d941-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="7d941-107">[in] Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d941-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="7d941-108">[out] Lokalizacja, który otrzymuje wskaźnik do adresu funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d941-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d941-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7d941-109">Return Value</span></span>  
 <span data-ttu-id="7d941-110">Ta metoda zwraca standardowe kody błędów Component Object Model (COM), zgodnie z definicją w pliku WinError.h oprócz następujące wartości, które są zdefiniowane w CorError.h.</span><span class="sxs-lookup"><span data-stu-id="7d941-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="7d941-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="7d941-111">Return code</span></span>|<span data-ttu-id="7d941-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7d941-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7d941-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d941-113">S_OK</span></span>|<span data-ttu-id="7d941-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7d941-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7d941-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7d941-115">E_POINTER</span></span>|<span data-ttu-id="7d941-116">`ppv` nie jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="7d941-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="7d941-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="7d941-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="7d941-118">Funkcja nie jest eksportowane ze środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="7d941-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d941-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d941-119">Requirements</span></span>  
 <span data-ttu-id="7d941-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d941-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d941-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d941-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d941-122">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d941-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d941-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d941-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d941-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d941-124">See also</span></span>

- [<span data-ttu-id="7d941-125">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="7d941-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
