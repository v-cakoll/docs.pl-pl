---
title: GetCORVersion — Funkcja
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178190"
---
# <a name="getcorversion-function"></a><span data-ttu-id="97be1-102">GetCORVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="97be1-102">GetCORVersion Function</span></span>
<span data-ttu-id="97be1-103">Zwraca numer wersji środowiska wykonawczego języka wspólnego (CLR), który jest uruchomiony w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="97be1-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="97be1-104">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="97be1-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97be1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="97be1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="97be1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97be1-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="97be1-107">Wskaźnik do buforu, w którym CLR zwraca ciąg określający wersję środowiska wykonawczego, który jest aktualnie ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="97be1-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="97be1-108">Zwracany ciąg ma taką samą formę jak ciągi przekazywane do [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), na przykład "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="97be1-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="97be1-109">Jeśli środowisko wykonawcze nie zostało jeszcze załadowane do procesu, funkcja zwraca odpowiednie informacje o katalogu dla najnowszej wersji środowiska wykonawczego zainstalowanego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="97be1-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="97be1-110">Liczba znaków (`WCHAR`s), które mogą `pbuffer`być przechowywane w .</span><span class="sxs-lookup"><span data-stu-id="97be1-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="97be1-111">Wskaźnik do liczby znaków faktycznie `pbuffer`zwróconych w .</span><span class="sxs-lookup"><span data-stu-id="97be1-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="97be1-112">Jeśli `pbuffer` jest wskaźnikiem zerowym, środowisko wykonawcze zwraca E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="97be1-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="97be1-113">Jeśli liczba znaków jest większa niż `pbuffer` długość , środowisko wykonawcze zwraca ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="97be1-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97be1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97be1-114">Requirements</span></span>  
 <span data-ttu-id="97be1-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97be1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97be1-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97be1-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97be1-117">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="97be1-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97be1-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97be1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97be1-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97be1-119">See also</span></span>

- [<span data-ttu-id="97be1-120">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="97be1-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
