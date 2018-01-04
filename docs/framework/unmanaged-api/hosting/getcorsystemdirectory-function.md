---
title: "GetCORSystemDirectory — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORSystemDirectory
helpviewer_keywords: GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02b695ac7f75dd38da8cd06e1444af4ae425ebd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="f22cb-102">GetCORSystemDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f22cb-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="f22cb-103">Zwraca katalog instalacyjny programu środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="f22cb-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="f22cb-104">Katalogu instalacyjnego jest w pełni kwalifikowana, na przykład "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="f22cb-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="f22cb-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="f22cb-105">This function is deprecated.</span></span> <span data-ttu-id="f22cb-106">Zostało zastąpione przez [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) metody w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f22cb-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f22cb-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f22cb-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="f22cb-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="f22cb-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="f22cb-109">[out] Bufor, w którym środowiska uruchomieniowego zwraca ciąg zawierający w pełni kwalifikowaną nazwę katalogu instalacyjnego środowiska uruchomieniowego, który jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="f22cb-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="f22cb-110">Jeśli środowisko uruchomieniowe nie został jeszcze załadowany do procesu, funkcja zwraca informacje odpowiedniego katalogu dla najnowszej wersji środowiska uruchomieniowego zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f22cb-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f22cb-111">[in] Rozmiar w bajtach z `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="f22cb-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="f22cb-112">[out] Liczba znaków zwracane w `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="f22cb-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f22cb-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f22cb-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f22cb-114">Nie należy używać tej funkcji w procesów uruchomionych w wersji 4 środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="f22cb-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="f22cb-115">Jeśli starszej wersji środowiska CLR jest zainstalowany na komputerze, ta funkcja zwraca katalog instalacyjny dla tej wersji.</span><span class="sxs-lookup"><span data-stu-id="f22cb-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f22cb-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f22cb-116">Requirements</span></span>  
 <span data-ttu-id="f22cb-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f22cb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f22cb-118">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f22cb-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f22cb-119">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f22cb-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f22cb-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f22cb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f22cb-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f22cb-121">See Also</span></span>  
 [<span data-ttu-id="f22cb-122">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="f22cb-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
