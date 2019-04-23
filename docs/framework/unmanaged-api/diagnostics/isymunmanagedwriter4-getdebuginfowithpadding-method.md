---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 191aa16c285b3a28beed65004d65525c9214ec93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081576"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="44156-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda</span><span class="sxs-lookup"><span data-stu-id="44156-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="44156-103">Działa tak samo, jak [getdebuginfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) z tą różnicą, że ciąg ścieżki są dopełniane zerami po kończącego znaku null, sprawić, że dane ciągu stały rozmiar `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="44156-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="44156-104">Dopełnienie tylko jest zwracany, jeśli długość ciągu ścieżki, sama jest mniejsza niż `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="44156-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="44156-105">Ułatwia do zapisania plików różnica PE narzędzia.</span><span class="sxs-lookup"><span data-stu-id="44156-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44156-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="44156-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44156-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="44156-107">Parameters</span></span>  
  
|<span data-ttu-id="44156-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="44156-108">Parameter</span></span>|<span data-ttu-id="44156-109">Opis</span><span class="sxs-lookup"><span data-stu-id="44156-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="44156-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="44156-110">Return Value</span></span>  
 <span data-ttu-id="44156-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="44156-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44156-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44156-112">Requirements</span></span>  
 <span data-ttu-id="44156-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="44156-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44156-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44156-114">See also</span></span>

- [<span data-ttu-id="44156-115">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="44156-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
