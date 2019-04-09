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
ms.openlocfilehash: 5d4723fbf2311316184cb77c90754d7e037badcd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089595"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="b831b-102">GetRealProcAddress — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b831b-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="b831b-103">Pobiera adres określonej funkcji, która została wyeksportowana z najnowszej zainstalowanej wersji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="b831b-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="b831b-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b831b-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b831b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b831b-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b831b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b831b-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="b831b-107">[in] Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="b831b-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="b831b-108">[out] Lokalizacja, który otrzymuje wskaźnik do adresu funkcji.</span><span class="sxs-lookup"><span data-stu-id="b831b-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b831b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b831b-109">Return Value</span></span>  
 <span data-ttu-id="b831b-110">Ta metoda zwraca standardowe kody błędów Component Object Model (COM), zgodnie z definicją w pliku WinError.h oprócz następujące wartości, które są zdefiniowane w CorError.h.</span><span class="sxs-lookup"><span data-stu-id="b831b-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="b831b-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="b831b-111">Return code</span></span>|<span data-ttu-id="b831b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b831b-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b831b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b831b-113">S_OK</span></span>|<span data-ttu-id="b831b-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b831b-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="b831b-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b831b-115">E_POINTER</span></span>|`ppv` <span data-ttu-id="b831b-116">nie jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="b831b-116">is not valid.</span></span>|  
|<span data-ttu-id="b831b-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="b831b-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="b831b-118">Funkcja nie jest eksportowane ze środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="b831b-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b831b-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b831b-119">Requirements</span></span>  
 <span data-ttu-id="b831b-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b831b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b831b-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b831b-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b831b-122">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b831b-122">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b831b-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b831b-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b831b-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b831b-124">See also</span></span>

- [<span data-ttu-id="b831b-125">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b831b-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
