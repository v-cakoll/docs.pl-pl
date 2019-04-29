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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f66e00c3334aecdf8c653f57e28d1b327c4170e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628005"
---
# <a name="getcorversion-function"></a><span data-ttu-id="db569-102">GetCORVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="db569-102">GetCORVersion Function</span></span>
<span data-ttu-id="db569-103">Zwraca numer wersji środowisko uruchomieniowe języka wspólnego (CLR) działającego w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="db569-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="db569-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db569-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db569-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="db569-105">Syntax</span></span>  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="db569-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="db569-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="db569-107">Wskaźnik do buforu, w którym środowisko CLR zwraca ciąg określający wersję środowiska uruchomieniowego, która jest aktualnie załadowana do procesu.</span><span class="sxs-lookup"><span data-stu-id="db569-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="db569-108">Zwracanego ciągu ma postać ten sam, jak ciągi przekazywane do [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), na przykład "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="db569-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="db569-109">Jeśli środowisko wykonawcze nie został jeszcze załadowany do procesu, funkcja zwraca informacje odpowiedniego katalogu dla najnowszej wersji środowiska uruchomieniowego zainstalowanego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="db569-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="db569-110">Liczba znaków (`WCHAR`s) mogą być przechowywane w `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="db569-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="db569-111">Wskaźnik do liczby znaków, które faktycznie są zwracane w `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="db569-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="db569-112">Jeśli `pbuffer` jest wskaźnikiem typu null, środowisko wykonawcze zwraca E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="db569-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="db569-113">Jeśli liczba znaków jest większa następnie długość `pbuffer` , środowisko wykonawcze zwraca ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="db569-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db569-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db569-114">Requirements</span></span>  
 <span data-ttu-id="db569-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db569-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db569-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db569-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db569-117">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db569-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db569-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db569-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db569-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db569-119">See also</span></span>

- [<span data-ttu-id="db569-120">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="db569-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
