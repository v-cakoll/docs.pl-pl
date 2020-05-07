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
ms.openlocfilehash: 2271611b5cbbfe487e5798be0429ed94c227a67f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860881"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="bb5cd-102">CreateCoreClrDebugTarget — Funkcja</span><span class="sxs-lookup"><span data-stu-id="bb5cd-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="bb5cd-103">Tworzy połączenie z serwerem proxy debugera, który jest uruchomiony na komputerze zdalnym i zwraca obiekt [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) , który może służyć do wykonywania zapytań dotyczących uruchomionych procesów i załadowanych środowiska uruchomieniowego na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb5cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb5cd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb5cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb5cd-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="bb5cd-106">podczas Adres IPv4 zdalnej maszyny docelowej.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="bb5cd-107">określoną Wskaźnik do wskaźnika do obiektu [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) , który zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb5cd-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bb5cd-108">Return Value</span></span>  
 <span data-ttu-id="bb5cd-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb5cd-109">S_OK</span></span>  
 <span data-ttu-id="bb5cd-110">Liczba CLRs w procesie została pomyślnie określona, a odpowiednie tablice uchwytów i ścieżek zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="bb5cd-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bb5cd-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="bb5cd-112">Nie można przydzielić wystarczającej `ppTarget`ilości pamięci dla.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="bb5cd-113">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="bb5cd-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="bb5cd-114">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb5cd-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb5cd-115">Requirements</span></span>  
 <span data-ttu-id="bb5cd-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb5cd-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb5cd-117">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="bb5cd-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="bb5cd-118">**Biblioteka:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="bb5cd-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="bb5cd-119">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="bb5cd-119">**.NET Framework Versions:** 3.5 SP1</span></span>
