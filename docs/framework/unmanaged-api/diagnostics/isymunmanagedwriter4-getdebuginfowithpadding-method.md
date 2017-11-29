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
ms.openlocfilehash: d9f2f0aad37fcd63e2345cd32a00b44412ed8c7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="9b4c8-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda</span><span class="sxs-lookup"><span data-stu-id="9b4c8-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="9b4c8-103">Działa tak samo, jak [GetDebugInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) z tą różnicą, że ciąg ścieżki jest uzupełniana zerami po znak końcowy null, aby udostępnić dane ciąg stały rozmiar `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="9b4c8-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="9b4c8-104">Dopełnienie tylko otrzyma, jeśli długość ciągu ścieżki sam jest mniejsza niż `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="9b4c8-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="9b4c8-105">Ułatwia to zapisać narzędzia pliki tej różnicy PE.</span><span class="sxs-lookup"><span data-stu-id="9b4c8-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b4c8-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b4c8-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b4c8-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b4c8-107">Parameters</span></span>  
  
|<span data-ttu-id="9b4c8-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="9b4c8-108">Parameter</span></span>|<span data-ttu-id="9b4c8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9b4c8-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="9b4c8-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9b4c8-110">Return Value</span></span>  
 <span data-ttu-id="9b4c8-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="9b4c8-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b4c8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b4c8-112">Requirements</span></span>  
 <span data-ttu-id="9b4c8-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9b4c8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b4c8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b4c8-114">See Also</span></span>  
 [<span data-ttu-id="9b4c8-115">Isymunmanagedwriter4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="9b4c8-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
