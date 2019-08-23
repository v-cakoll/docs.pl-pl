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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6f514cc070a0a38eb09a5387efc8611100765b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944099"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="7de75-102">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7de75-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="7de75-103">Rozszerza interfejs segregatora symboli.</span><span class="sxs-lookup"><span data-stu-id="7de75-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="7de75-104">Uzyskaj ten interfejs, wywołując `QueryInterface` obiekt, który `ISymUnmanagedBinder` implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="7de75-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7de75-105">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych programu (PDB) z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="7de75-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7de75-106">Metody</span><span class="sxs-lookup"><span data-stu-id="7de75-106">Methods</span></span>  
  
|<span data-ttu-id="7de75-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="7de75-107">Method</span></span>|<span data-ttu-id="7de75-108">Opis</span><span class="sxs-lookup"><span data-stu-id="7de75-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7de75-109">GetReaderFromCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="7de75-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="7de75-110">Zezwala użytkownikowi na implementowanie lub dostarczanie za pośrednictwem wywołania `IID_IDiaReadExeAtRVACallback` zwrotnego `IID_IDiaReadExeAtOffsetCallback` albo uzyskanie informacji o katalogu debugowania z pamięci</span><span class="sxs-lookup"><span data-stu-id="7de75-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7de75-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7de75-111">Requirements</span></span>  
 <span data-ttu-id="7de75-112">**Nagłówki** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7de75-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de75-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7de75-113">See also</span></span>

- [<span data-ttu-id="7de75-114">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="7de75-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7de75-115">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="7de75-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="7de75-116">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7de75-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
