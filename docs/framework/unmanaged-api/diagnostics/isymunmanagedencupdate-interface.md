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
ms.openlocfilehash: 1986d5f91a3dcfa31a43f729ee1f50129e083f5f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501745"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="1ff6c-102">ISymUnmanagedENCUpdate — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1ff6c-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="1ff6c-103">Udostępnia funkcje funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ff6c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1ff6c-104">Methods</span></span>  
  
|<span data-ttu-id="1ff6c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1ff6c-105">Method</span></span>|<span data-ttu-id="1ff6c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1ff6c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ff6c-107">GetLocalVariableCount, metoda</span><span class="sxs-lookup"><span data-stu-id="1ff6c-107">GetLocalVariableCount Method</span></span>](isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="1ff6c-108">Pobiera liczbę zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="1ff6c-109">GetLocalVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="1ff6c-109">GetLocalVariables Method</span></span>](isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="1ff6c-110">Pobiera zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="1ff6c-111">InitializeForEnc, metoda</span><span class="sxs-lookup"><span data-stu-id="1ff6c-111">InitializeForEnc Method</span></span>](isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="1ff6c-112">Umożliwia obliczenia granic metod przed pierwszym wywołaniem metody [ISymUnmanagedENCUpdate:: UpdateSymbolStore2 —](isymunmanagedencupdate-updatesymbolstore2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1ff6c-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="1ff6c-113">UpdateMethodLines, metoda</span><span class="sxs-lookup"><span data-stu-id="1ff6c-113">UpdateMethodLines Method</span></span>](isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="1ff6c-114">Umożliwia aktualizowanie informacji o wierszu dla metody, która nie została ponownie skompilowana, ale których linie nie zostały przesunięte niezależnie.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="1ff6c-115">Różnicowa dla każdej instrukcji jest dozwolony.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="1ff6c-116">UpdateSymbolStore2, metoda</span><span class="sxs-lookup"><span data-stu-id="1ff6c-116">UpdateSymbolStore2 Method</span></span>](isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="1ff6c-117">Pozwala kompilatorowi pominąć funkcje, które nie zostały zmodyfikowane ze strumienia bazy danych programu (PDB), pod warunkiem, że informacje o wierszu spełniają wymagania.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="1ff6c-118">Informacje o prawidłowych wierszach można określić ze starymi informacjami o wierszu PDB i jedną różnicą dla wszystkich wierszy w funkcji.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ff6c-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ff6c-119">Requirements</span></span>  
 <span data-ttu-id="1ff6c-120">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1ff6c-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff6c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ff6c-121">See also</span></span>

- [<span data-ttu-id="1ff6c-122">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="1ff6c-122">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
