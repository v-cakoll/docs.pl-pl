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
ms.openlocfilehash: 5a26de2a8f5439b7c81560927c991d449e57b76c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441594"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="c7256-102">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7256-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="c7256-103">Rozszerza interfejs segregatora symboli.</span><span class="sxs-lookup"><span data-stu-id="c7256-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="c7256-104">Uzyskaj ten interfejs, wywołując `QueryInterface` obiekt, który implementuje `ISymUnmanagedBinder` interfejs.</span><span class="sxs-lookup"><span data-stu-id="c7256-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c7256-105">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych programu (PDB) z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="c7256-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7256-106">Metody</span><span class="sxs-lookup"><span data-stu-id="c7256-106">Methods</span></span>  
  
|<span data-ttu-id="c7256-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7256-107">Method</span></span>|<span data-ttu-id="c7256-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c7256-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7256-109">GetReaderFromCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="c7256-109">GetReaderFromCallback Method</span></span>](isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="c7256-110">Zezwala użytkownikowi na implementowanie lub dostarczanie za pośrednictwem wywołania zwrotnego albo `IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` uzyskanie informacji o katalogu debugowania z pamięci</span><span class="sxs-lookup"><span data-stu-id="c7256-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7256-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7256-111">Requirements</span></span>  
 <span data-ttu-id="c7256-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c7256-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7256-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7256-113">See also</span></span>

- [<span data-ttu-id="c7256-114">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="c7256-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="c7256-115">ISymUnmanagedBinder — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7256-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="c7256-116">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7256-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
