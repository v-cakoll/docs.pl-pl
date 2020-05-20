---
title: ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset — Metoda
ms.date: 03/30/2017
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
ms.openlocfilehash: f45b9a53909ab23428a8d51be2e672bfdd15d951
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441854"
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="0209d-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="0209d-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="0209d-103">Zobacz [DefineCatchHandlerILOffset —](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="0209d-103">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0209d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0209d-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0209d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0209d-105">Parameters</span></span>  
  
|<span data-ttu-id="0209d-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="0209d-106">Parameter</span></span>|<span data-ttu-id="0209d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0209d-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="0209d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0209d-108">Return Value</span></span>  
 <span data-ttu-id="0209d-109">Zwraca wartość `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="0209d-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0209d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0209d-110">Requirements</span></span>  
 <span data-ttu-id="0209d-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0209d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0209d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0209d-112">See also</span></span>

- [<span data-ttu-id="0209d-113">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0209d-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
