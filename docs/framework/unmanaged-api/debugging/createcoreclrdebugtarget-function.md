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
ms.openlocfilehash: a7fed8cb70785f0ccfcadf1e16181db303ac98e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789192"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="26c91-102">CreateCoreClrDebugTarget — Funkcja</span><span class="sxs-lookup"><span data-stu-id="26c91-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="26c91-103">Tworzy połączenie z serwerem proxy debugera, który jest uruchomiony na komputerze zdalnym i zwraca obiekt [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) , który może służyć do wykonywania zapytań dotyczących uruchomionych procesów i załadowanych środowiska uruchomieniowego na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="26c91-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26c91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26c91-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26c91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26c91-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="26c91-106">podczas Adres IPv4 zdalnej maszyny docelowej.</span><span class="sxs-lookup"><span data-stu-id="26c91-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="26c91-107">określoną Wskaźnik do wskaźnika do obiektu [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) , który zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="26c91-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26c91-108">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="26c91-108">Return Value</span></span>  
 <span data-ttu-id="26c91-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="26c91-109">S_OK</span></span>  
 <span data-ttu-id="26c91-110">Liczba CLRs w procesie została pomyślnie określona, a odpowiednie tablice uchwytów i ścieżek zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="26c91-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="26c91-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="26c91-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="26c91-112">Nie można przydzielić wystarczającej ilości pamięci dla `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="26c91-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="26c91-113">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="26c91-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="26c91-114">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="26c91-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26c91-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26c91-115">Requirements</span></span>  
 <span data-ttu-id="26c91-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26c91-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26c91-117">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="26c91-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="26c91-118">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="26c91-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="26c91-119">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="26c91-119">**.NET Framework Versions:** 3.5 SP1</span></span>
