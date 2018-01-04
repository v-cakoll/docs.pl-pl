---
title: "CreateCoreClrDebugTarget — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateCorClrDebugTarget
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5b05cc6c84f2f891691613a485d35d008ef79e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="9d68b-102">CreateCoreClrDebugTarget — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9d68b-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="9d68b-103">Tworzy połączenie debugera serwer proxy, który jest uruchomiony na komputerze zdalnym i zwraca [icoreclrdebugtarget —](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) obiektu, który może służyć do badania uruchomione procesy i załadować środowisk uruchomieniowych na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="9d68b-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d68b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d68b-104">Syntax</span></span>  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d68b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d68b-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="9d68b-106">[in] Adres IPv4 maszynę docelową zdalnego.</span><span class="sxs-lookup"><span data-stu-id="9d68b-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="9d68b-107">[out] Wskaźnik na wskaźnik do [icoreclrdebugtarget —](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) obiektu, który zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="9d68b-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d68b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d68b-108">Return Value</span></span>  
 <span data-ttu-id="9d68b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d68b-109">S_OK</span></span>  
 <span data-ttu-id="9d68b-110">CLRs procesu został pomyślnie określana i odpowiednie dojścia tablice ścieżki zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="9d68b-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="9d68b-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9d68b-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="9d68b-112">Nie można przydzielić wystarczającej ilości pamięci do `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="9d68b-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="9d68b-113">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="9d68b-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9d68b-114">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="9d68b-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d68b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d68b-115">Requirements</span></span>  
 <span data-ttu-id="9d68b-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d68b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d68b-117">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="9d68b-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="9d68b-118">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="9d68b-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="9d68b-119">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="9d68b-119">**.NET Framework Versions:** 3.5 SP1</span></span>
