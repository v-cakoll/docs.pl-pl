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
ms.openlocfilehash: 0b210f105495fa3f5595adbcb0805e1d1fb62310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179218"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="a35d2-102">CreateCoreClrDebugTarget — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a35d2-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="a35d2-103">Tworzy połączenie z serwerem proxy debugera, który jest uruchomiony na komputerze zdalnym i zwraca [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) obiektu, który może służyć do wykonywania zapytań uruchomionych procesów i załadowanych runtimes na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="a35d2-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a35d2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a35d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a35d2-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="a35d2-106">[w] adres IPv4 zdalnego komputera docelowego.</span><span class="sxs-lookup"><span data-stu-id="a35d2-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="a35d2-107">[na zewnątrz] Wskaźnik do wskaźnika do [obiektu ICoreClrDebugTarget,](icoreclrdebugtarget-interface.md) który zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="a35d2-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a35d2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a35d2-108">Return Value</span></span>  
 <span data-ttu-id="a35d2-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="a35d2-109">S_OK</span></span>  
 <span data-ttu-id="a35d2-110">Liczba clr w procesie została pomyślnie określona, a odpowiednie tablice dojścia i ścieżki zostały poprawnie wypełnione.</span><span class="sxs-lookup"><span data-stu-id="a35d2-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="a35d2-111">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="a35d2-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="a35d2-112">Nie można przydzielić `ppTarget`wystarczającej ilości pamięci dla pliku .</span><span class="sxs-lookup"><span data-stu-id="a35d2-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="a35d2-113">E_FAIL (lub inne E_ kody zwrotne)</span><span class="sxs-lookup"><span data-stu-id="a35d2-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a35d2-114">Inne awarie.</span><span class="sxs-lookup"><span data-stu-id="a35d2-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a35d2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a35d2-115">Requirements</span></span>  
 <span data-ttu-id="a35d2-116">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a35d2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a35d2-117">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="a35d2-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a35d2-118">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="a35d2-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a35d2-119">**Wersje .NET Framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a35d2-119">**.NET Framework Versions:** 3.5 SP1</span></span>
