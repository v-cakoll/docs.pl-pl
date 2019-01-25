---
title: ISymUnmanagedWriter4 — Interfejs
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a5e44541a18f10588e899f59a166406c149691f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650057"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="816b7-102">ISymUnmanagedWriter4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="816b7-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="816b7-103">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="816b7-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="816b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="816b7-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="816b7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="816b7-105">Methods</span></span>  
 <span data-ttu-id="816b7-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="816b7-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="816b7-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="816b7-107">Method</span></span>|<span data-ttu-id="816b7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="816b7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="816b7-109">GetDebugInfoWithPadding, metoda</span><span class="sxs-lookup"><span data-stu-id="816b7-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="816b7-110">Działa tak samo, jak [getdebuginfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) z tą różnicą, że ciąg ścieżki są dopełniane zerami po kończącego znaku null, sprawić, że dane ciągu stały rozmiar `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="816b7-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="816b7-111">Dopełnienie tylko jest zwracany, jeśli długość ciągu ścieżki, sama jest mniejsza niż `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="816b7-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="816b7-112">Ułatwia do zapisania plików różnica PE narzędzia.</span><span class="sxs-lookup"><span data-stu-id="816b7-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="816b7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="816b7-113">Requirements</span></span>  
 <span data-ttu-id="816b7-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="816b7-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816b7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="816b7-115">See also</span></span>
- [<span data-ttu-id="816b7-116">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="816b7-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="816b7-117">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="816b7-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
