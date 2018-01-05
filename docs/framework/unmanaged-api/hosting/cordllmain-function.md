---
title: "_CorDllMain — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorDllMain
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorDllMain
helpviewer_keywords: _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 985f2284026054217671de767c316b1fba35c098
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordllmain-function"></a><span data-ttu-id="4d731-102">_CorDllMain — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4d731-102">_CorDllMain Function</span></span>
<span data-ttu-id="4d731-103">Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu biblioteki DLL i rozpoczęciu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4d731-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d731-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d731-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d731-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d731-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="4d731-106">[in] Dojście wystąpienia załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="4d731-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="4d731-107">[in] Wskazuje, dlaczego jest wywoływana funkcja punktu wejścia biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="4d731-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="4d731-108">Ten parametr może mieć jedną z następujących wartości: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH lub komunikat DLL_PROCESS_DETACH.</span><span class="sxs-lookup"><span data-stu-id="4d731-108">This parameter can be one of the following values: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH, or DLL_PROCESS_DETACH.</span></span> <span data-ttu-id="4d731-109">Aby uzyskać opis tych wartości, zobacz `DllMain` dokumentacji zestawu SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="4d731-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="4d731-110">[in] Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4d731-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d731-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4d731-111">Return Value</span></span>  
 <span data-ttu-id="4d731-112">Ta metoda zwraca `true` w przypadku powodzenia i `false` w przypadku wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="4d731-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d731-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d731-113">Remarks</span></span>  
 <span data-ttu-id="4d731-114">Ta funkcja jest wywoływana przez moduł ładujący systemu operacyjnego dla zestawów biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="4d731-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="4d731-115">Dla pliku wykonywalnego zestawów wywołuje moduł ładujący [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) zamiast tego działania.</span><span class="sxs-lookup"><span data-stu-id="4d731-115">For executable assemblies, the loader calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="4d731-116">Moduł ładujący systemu operacyjnego wywołuje tę metodę, niezależnie od punkt wejścia określony w pliku DLL.</span><span class="sxs-lookup"><span data-stu-id="4d731-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
 <span data-ttu-id="4d731-117">W Windows 98, Windows ME, Windows NT i system Windows 2000 `_CorDllMain` funkcja jest wywoływana bezpośrednio za pomocą fixupin modułu ładującego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="4d731-117">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorDllMain` function is called indirectly through a fixupin the operating system loader.</span></span> <span data-ttu-id="4d731-118">We wszystkich innych wersjach systemu Windows jest ona wywoływana bezpośrednio przez moduł ładujący systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="4d731-118">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="4d731-119">Aby uzyskać dodatkowe informacje, zobacz sekcję uwag w [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="4d731-119">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d731-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d731-120">Requirements</span></span>  
 <span data-ttu-id="4d731-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d731-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d731-122">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4d731-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d731-123">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d731-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d731-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d731-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d731-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d731-125">See Also</span></span>  
 [<span data-ttu-id="4d731-126">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="4d731-126">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
