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
ms.openlocfilehash: f60f159ab4770023cee7123b39109040243e1ccd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136966"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="f3ab3-102">\_funkcja CorDllMain</span><span class="sxs-lookup"><span data-stu-id="f3ab3-102">\_CorDllMain Function</span></span>

<span data-ttu-id="f3ab3-103">Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu DLL i rozpoczyna wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="f3ab3-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ab3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3ab3-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3ab3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3ab3-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="f3ab3-106">podczas Dojście wystąpienia załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="f3ab3-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="f3ab3-107">podczas Wskazuje, dlaczego funkcja punktu wejścia biblioteki DLL jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="f3ab3-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="f3ab3-108">Ten parametr może być jedną z następujących wartości: DLL\_PROCESS_ATTACH, DLL\_wątku\_ATTACH, DLL\_wątku\_ATTACH, lub\_proces\_odłączania.</span><span class="sxs-lookup"><span data-stu-id="f3ab3-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="f3ab3-109">Opisy tych wartości można znaleźć w dokumentacji `DllMain` w zestawie SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="f3ab3-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="f3ab3-110">podczas Przestrzeń.</span><span class="sxs-lookup"><span data-stu-id="f3ab3-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3ab3-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f3ab3-111">Return Value</span></span>  
 <span data-ttu-id="f3ab3-112">Ta metoda zwraca `true` dla sukcesu i `false` w przypadku wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="f3ab3-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3ab3-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3ab3-113">Remarks</span></span>  
 <span data-ttu-id="f3ab3-114">Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego dla zestawów bibliotek DLL.</span><span class="sxs-lookup"><span data-stu-id="f3ab3-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="f3ab3-115">W przypadku zestawów wykonywalnych moduł ładujący wywołuje [\_funkcję CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f3ab3-115">For executable assemblies, the loader calls the [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="f3ab3-116">Moduł ładujący systemu operacyjnego wywołuje tę metodę niezależnie od punktu wejścia określonego w pliku DLL.</span><span class="sxs-lookup"><span data-stu-id="f3ab3-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="f3ab3-117">Funkcja `_CorDllMain` jest wywoływana bezpośrednio przez program ładujący systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f3ab3-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="f3ab3-118">Aby uzyskać dodatkowe informacje, zobacz sekcję Uwagi w temacie [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f3ab3-118">For additional information, see the Remarks section in the [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3ab3-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3ab3-119">Requirements</span></span>  

 <span data-ttu-id="f3ab3-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3ab3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3ab3-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f3ab3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3ab3-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3ab3-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3ab3-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3ab3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ab3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3ab3-124">See also</span></span>

- [<span data-ttu-id="f3ab3-125">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="f3ab3-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
