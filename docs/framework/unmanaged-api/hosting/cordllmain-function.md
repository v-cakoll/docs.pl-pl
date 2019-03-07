---
title: _CorDllMain — Funkcja
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3c529e77cad16f0bde12e34491829b58add17aa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500394"
---
# <a name="cordllmain-function"></a><span data-ttu-id="529a4-102">_CorDllMain — Funkcja</span><span class="sxs-lookup"><span data-stu-id="529a4-102">_CorDllMain Function</span></span>
<span data-ttu-id="529a4-103">Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu biblioteki DLL i rozpoczyna wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="529a4-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="529a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="529a4-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="529a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="529a4-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="529a4-106">[in] Uchwyt wystąpienia załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="529a4-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="529a4-107">[in] Wskazuje, dlaczego jest wywoływana funkcja punktu wejścia biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="529a4-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="529a4-108">Ten parametr może być jedną z następujących wartości: DLL_PROCESS_ATTACH DLL_THREAD_ATTACH, DLL_THREAD_ATTACH lub komunikat DLL_PROCESS_DETACH.</span><span class="sxs-lookup"><span data-stu-id="529a4-108">This parameter can be one of the following values: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH, or DLL_PROCESS_DETACH.</span></span> <span data-ttu-id="529a4-109">Aby uzyskać opis tych wartości, zobacz `DllMain` dokumentacji w zestawie SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="529a4-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="529a4-110">[in] Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="529a4-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="529a4-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="529a4-111">Return Value</span></span>  
 <span data-ttu-id="529a4-112">Ta metoda zwraca `true` w celu osiągnięcia sukcesu i `false` w przypadku wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="529a4-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="529a4-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="529a4-113">Remarks</span></span>  
 <span data-ttu-id="529a4-114">Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego dla zestawów DLL.</span><span class="sxs-lookup"><span data-stu-id="529a4-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="529a4-115">Dla pliku wykonywalnego zestawów wywołuje moduł ładujący [_corexemain —](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) zamiast tego funkcji.</span><span class="sxs-lookup"><span data-stu-id="529a4-115">For executable assemblies, the loader calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="529a4-116">Program ładujący systemu operacyjnego wywołuje tę metodę, niezależnie od tego punktu wejścia, określone w pliku DLL.</span><span class="sxs-lookup"><span data-stu-id="529a4-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="529a4-117">`_CorDllMain` Funkcja jest wywoływana bezpośrednio przez program ładujący systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="529a4-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="529a4-118">Aby uzyskać dodatkowe informacje, zobacz sekcję Uwagi w [_corvalidateimage —](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="529a4-118">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="529a4-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="529a4-119">Requirements</span></span>  
 <span data-ttu-id="529a4-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="529a4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="529a4-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="529a4-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="529a4-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="529a4-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="529a4-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="529a4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="529a4-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="529a4-124">See also</span></span>
- [<span data-ttu-id="529a4-125">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="529a4-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
