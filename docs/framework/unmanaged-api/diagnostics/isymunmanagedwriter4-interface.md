---
title: ISymUnmanagedWriter4 — Interfejs
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5732cc08512df25a14cc8ea9dcaa03c56207dde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202049"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="e65b6-102">ISymUnmanagedWriter4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e65b6-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="e65b6-103">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="e65b6-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e65b6-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="e65b6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e65b6-105">Methods</span></span>  
 <span data-ttu-id="e65b6-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="e65b6-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="e65b6-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="e65b6-107">Method</span></span>|<span data-ttu-id="e65b6-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e65b6-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e65b6-109">GetDebugInfoWithPadding, metoda</span><span class="sxs-lookup"><span data-stu-id="e65b6-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="e65b6-110">Działa tak samo, jak [getdebuginfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) z tą różnicą, że ciąg ścieżki są dopełniane zerami po kończącego znaku null, sprawić, że dane ciągu stały rozmiar `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="e65b6-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="e65b6-111">Dopełnienie tylko jest zwracany, jeśli długość ciągu ścieżki, sama jest mniejsza niż `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="e65b6-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="e65b6-112">Ułatwia do zapisania plików różnica PE narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e65b6-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e65b6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e65b6-113">Requirements</span></span>  
 <span data-ttu-id="e65b6-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e65b6-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e65b6-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e65b6-115">See also</span></span>

- [<span data-ttu-id="e65b6-116">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="e65b6-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="e65b6-117">ISymUnmanagedWriter3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e65b6-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
