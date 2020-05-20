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
ms.openlocfilehash: 3b2322f708afed08172f87e843c225aa9c60d9d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616609"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="5573c-102">\_CorDllMain, funkcja</span><span class="sxs-lookup"><span data-stu-id="5573c-102">\_CorDllMain Function</span></span>

<span data-ttu-id="5573c-103">Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu DLL i rozpoczyna wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="5573c-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5573c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5573c-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5573c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5573c-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="5573c-106">podczas Dojście wystąpienia załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="5573c-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="5573c-107">podczas Wskazuje, dlaczego funkcja punktu wejścia biblioteki DLL jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="5573c-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="5573c-108">Ten parametr może mieć jedną z następujących wartości: DLL PROCESS_ATTACH, dołączania do \_ \_ wątku dll \_ , \_ \_ dołączania wątku dll lub \_ \_ odłączania procesu biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="5573c-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="5573c-109">Opisy tych wartości można znaleźć `DllMain` w dokumentacji zestawu Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="5573c-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="5573c-110">podczas Przestrzeń.</span><span class="sxs-lookup"><span data-stu-id="5573c-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5573c-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5573c-111">Return Value</span></span>  
 <span data-ttu-id="5573c-112">Ta metoda zwraca `true` sukces i w `false` przypadku wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="5573c-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5573c-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5573c-113">Remarks</span></span>  
 <span data-ttu-id="5573c-114">Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego dla zestawów bibliotek DLL.</span><span class="sxs-lookup"><span data-stu-id="5573c-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="5573c-115">W przypadku zestawów wykonywalnych moduł ładujący wywołuje funkcję [ \_ CorExeMain](corexemain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="5573c-115">For executable assemblies, the loader calls the [\_CorExeMain](corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="5573c-116">Moduł ładujący systemu operacyjnego wywołuje tę metodę niezależnie od punktu wejścia określonego w pliku DLL.</span><span class="sxs-lookup"><span data-stu-id="5573c-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="5573c-117">`_CorDllMain`Funkcja jest wywoływana bezpośrednio przez program ładujący systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5573c-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="5573c-118">Aby uzyskać dodatkowe informacje, zobacz sekcję Uwagi w temacie [ \_ CorValidateImage](corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="5573c-118">For additional information, see the Remarks section in the [\_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5573c-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5573c-119">Requirements</span></span>  

 <span data-ttu-id="5573c-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5573c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5573c-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5573c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5573c-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5573c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5573c-123">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5573c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5573c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5573c-124">See also</span></span>

- [<span data-ttu-id="5573c-125">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="5573c-125">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
