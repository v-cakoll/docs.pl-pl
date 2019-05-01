---
title: CreateCoreClrDebugTarget — Funkcja
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48ce5381c745669b813f5b28d801add7daba7825
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965844"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="a865a-102">CreateCoreClrDebugTarget — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a865a-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="a865a-103">Tworzy połączenie z serwerem proxy debugera, jest uruchomiona na maszynie zdalnej, która zwraca [icoreclrdebugtarget —](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) obiekt, który może służyć do kwerendy, uruchomione procesy i załadować środowisk wykonawczych na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="a865a-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a865a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a865a-104">Syntax</span></span>  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a865a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a865a-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="a865a-106">[in] Adres IPv4 komputera zdalnego docelowego.</span><span class="sxs-lookup"><span data-stu-id="a865a-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="a865a-107">[out] Wskaźnik do wskaźnika do [icoreclrdebugtarget —](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) obiektu, który zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="a865a-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a865a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a865a-108">Return Value</span></span>  
 <span data-ttu-id="a865a-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="a865a-109">S_OK</span></span>  
 <span data-ttu-id="a865a-110">CLRs procesu został pomyślnie określana i odpowiednie dojścia i tablice ścieżki zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="a865a-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="a865a-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a865a-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="a865a-112">Nie można przydzielić wystarczającej ilości pamięci do `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="a865a-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="a865a-113">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="a865a-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a865a-114">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="a865a-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a865a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a865a-115">Requirements</span></span>  
 <span data-ttu-id="a865a-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a865a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a865a-117">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="a865a-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a865a-118">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="a865a-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a865a-119">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="a865a-119">**.NET Framework Versions:** 3.5 SP1</span></span>
