---
title: ISymUnmanagedBinder3 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: e4a415b21e3980e7603319d7acbb3831462fac9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449299"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="cf6c3-102">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cf6c3-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="cf6c3-103">Rozszerza interfejs segregatora symboli.</span><span class="sxs-lookup"><span data-stu-id="cf6c3-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="cf6c3-104">Uzyskaj ten interfejs, wywołując `QueryInterface` na obiekcie, który implementuje interfejs `ISymUnmanagedBinder`.</span><span class="sxs-lookup"><span data-stu-id="cf6c3-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cf6c3-105">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych programu (PDB) z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="cf6c3-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf6c3-106">Metody</span><span class="sxs-lookup"><span data-stu-id="cf6c3-106">Methods</span></span>  
  
|<span data-ttu-id="cf6c3-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="cf6c3-107">Method</span></span>|<span data-ttu-id="cf6c3-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cf6c3-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf6c3-109">GetReaderFromCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="cf6c3-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="cf6c3-110">Zezwala użytkownikowi na implementowanie lub dostarczanie za pośrednictwem wywołania zwrotnego albo `IID_IDiaReadExeAtRVACallback` lub `IID_IDiaReadExeAtOffsetCallback`, aby uzyskać informacje o katalogu debugowania z pamięci</span><span class="sxs-lookup"><span data-stu-id="cf6c3-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf6c3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf6c3-111">Requirements</span></span>  
 <span data-ttu-id="cf6c3-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cf6c3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf6c3-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf6c3-113">See also</span></span>

- [<span data-ttu-id="cf6c3-114">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="cf6c3-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="cf6c3-115">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf6c3-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="cf6c3-116">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf6c3-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
