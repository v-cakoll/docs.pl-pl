---
title: "ISymUnmanagedENCUpdate — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate
helpviewer_keywords: ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 36ac53094751cb43ef122d439c7a784070c28182
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="62406-102">ISymUnmanagedENCUpdate — Interfejs</span><span class="sxs-lookup"><span data-stu-id="62406-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="62406-103">Udostępnia funkcje dla funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="62406-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62406-104">Metody</span><span class="sxs-lookup"><span data-stu-id="62406-104">Methods</span></span>  
  
|<span data-ttu-id="62406-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="62406-105">Method</span></span>|<span data-ttu-id="62406-106">Opis</span><span class="sxs-lookup"><span data-stu-id="62406-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62406-107">GetLocalVariableCount — metoda</span><span class="sxs-lookup"><span data-stu-id="62406-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="62406-108">Pobiera liczbę zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="62406-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="62406-109">GetLocalVariables — metoda</span><span class="sxs-lookup"><span data-stu-id="62406-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="62406-110">Pobiera zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="62406-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="62406-111">InitializeForEnc — metoda</span><span class="sxs-lookup"><span data-stu-id="62406-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="62406-112">Umożliwia granice metody ma zostać obliczony przed pierwszym wywołaniu [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="62406-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="62406-113">UpdateMethodLines — metoda</span><span class="sxs-lookup"><span data-stu-id="62406-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="62406-114">Zezwala na aktualizowanie informacji linii dla metody, która nie zwrócenie, ale których wiersze zostały przeniesione osobno.</span><span class="sxs-lookup"><span data-stu-id="62406-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="62406-115">Delta dla każdej instrukcji jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="62406-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="62406-116">UpdateSymbolStore2 — metoda</span><span class="sxs-lookup"><span data-stu-id="62406-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="62406-117">Umożliwia kompilatora pominąć funkcje, które nie zostały zmodyfikowane ze strumienia programu (PDB) bazy danych, pod warunkiem, że informacje dotyczące wiersza spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="62406-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="62406-118">Starych informacji PDB w wierszu i jeden delta dla wszystkich wierszy w funkcji można określić informacje dotyczące poprawne wiersza.</span><span class="sxs-lookup"><span data-stu-id="62406-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62406-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62406-119">Requirements</span></span>  
 <span data-ttu-id="62406-120">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="62406-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62406-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62406-121">See Also</span></span>  
 [<span data-ttu-id="62406-122">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="62406-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
