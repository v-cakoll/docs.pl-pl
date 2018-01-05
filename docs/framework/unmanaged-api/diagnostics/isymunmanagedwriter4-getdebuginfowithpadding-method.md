---
title: "ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f85486370d567ceb1506c41f6aa7c4f3a1929941
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="e3207-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3207-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="e3207-103">Działa tak samo, jak [GetDebugInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) z tą różnicą, że ciąg ścieżki jest uzupełniana zerami po znak końcowy null, aby udostępnić dane ciąg stały rozmiar `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="e3207-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="e3207-104">Dopełnienie tylko otrzyma, jeśli długość ciągu ścieżki sam jest mniejsza niż `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="e3207-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="e3207-105">Ułatwia to zapisać narzędzia pliki tej różnicy PE.</span><span class="sxs-lookup"><span data-stu-id="e3207-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3207-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3207-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3207-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3207-107">Parameters</span></span>  
  
|<span data-ttu-id="e3207-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="e3207-108">Parameter</span></span>|<span data-ttu-id="e3207-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e3207-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="e3207-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3207-110">Return Value</span></span>  
 <span data-ttu-id="e3207-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="e3207-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3207-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3207-112">Requirements</span></span>  
 <span data-ttu-id="e3207-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e3207-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3207-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3207-114">See Also</span></span>  
 [<span data-ttu-id="e3207-115">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3207-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
