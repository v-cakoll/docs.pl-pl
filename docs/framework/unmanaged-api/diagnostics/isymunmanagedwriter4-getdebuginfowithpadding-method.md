---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 274bf79175bda9e880b1ef3cf8f125a017ad0734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121662"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="cd91d-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd91d-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="cd91d-103">Działa tak samo jak [Metoda GetDebugInfo —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , z tą różnicą, że ciąg ścieżki jest dopełniany zerami po zamykającym znaku null, aby dane ciągu miały stały rozmiar `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="cd91d-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="cd91d-104">Uzupełnienie jest nadawane tylko wtedy, gdy sama długość ciągu ścieżki jest mniejsza niż `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="cd91d-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="cd91d-105">Ułatwia to pisanie narzędzi, które różnicuje pliki PE.</span><span class="sxs-lookup"><span data-stu-id="cd91d-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd91d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd91d-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd91d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd91d-107">Parameters</span></span>  
  
|<span data-ttu-id="cd91d-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="cd91d-108">Parameter</span></span>|<span data-ttu-id="cd91d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="cd91d-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="cd91d-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cd91d-110">Return Value</span></span>  
 <span data-ttu-id="cd91d-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="cd91d-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd91d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd91d-112">Requirements</span></span>  
 <span data-ttu-id="cd91d-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cd91d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd91d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd91d-114">See also</span></span>

- [<span data-ttu-id="cd91d-115">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd91d-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
