---
title: ISymUnmanagedENCUpdate — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 634716b36a0e5826cd7667a9ae948e8172724a1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630869"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="3b895-102">ISymUnmanagedENCUpdate — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3b895-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="3b895-103">Oferuje funkcje funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="3b895-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b895-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3b895-104">Methods</span></span>  
  
|<span data-ttu-id="3b895-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3b895-105">Method</span></span>|<span data-ttu-id="3b895-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3b895-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3b895-107">GetLocalVariableCount, metoda</span><span class="sxs-lookup"><span data-stu-id="3b895-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="3b895-108">Pobiera liczbę zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="3b895-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="3b895-109">GetLocalVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="3b895-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="3b895-110">Pobiera zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="3b895-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="3b895-111">InitializeForEnc, metoda</span><span class="sxs-lookup"><span data-stu-id="3b895-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="3b895-112">Umożliwia granice metody ma zostać obliczony przed pierwszym wywołaniu [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3b895-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="3b895-113">UpdateMethodLines, metoda</span><span class="sxs-lookup"><span data-stu-id="3b895-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="3b895-114">Zezwala na aktualizowanie informacji o wierszu dla metody, która nie zwrócenie, ale których wiersze zostały przeniesione niezależnie.</span><span class="sxs-lookup"><span data-stu-id="3b895-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="3b895-115">Delta dla każdej instrukcji jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="3b895-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="3b895-116">UpdateSymbolStore2, metoda</span><span class="sxs-lookup"><span data-stu-id="3b895-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="3b895-117">Umożliwia kompilatorowi pominąć funkcje, które nie zostały zmodyfikowane ze strumienia bazy danych (PDB) programu, pod warunkiem, że informacje wiersza spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="3b895-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="3b895-118">Informacje wiersza poprawne można ustalić przy użyciu starych informacji PDB w wierszu i jeden różnicowej dla wszystkich wierszy w funkcji.</span><span class="sxs-lookup"><span data-stu-id="3b895-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b895-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b895-119">Requirements</span></span>  
 <span data-ttu-id="3b895-120">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3b895-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b895-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b895-121">See also</span></span>
- [<span data-ttu-id="3b895-122">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="3b895-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
