---
title: ISymUnmanagedBinder — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6d91f68ac737ce28cdbef926119bb3711bc1096
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105822"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="e29ca-102">ISymUnmanagedBinder — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e29ca-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="e29ca-103">Reprezentuje integrator symboli dla niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="e29ca-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e29ca-104">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych (PDB) programu z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="e29ca-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e29ca-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e29ca-105">Methods</span></span>  
  
|<span data-ttu-id="e29ca-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e29ca-106">Method</span></span>|<span data-ttu-id="e29ca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e29ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e29ca-108">GetReaderForFile, metoda</span><span class="sxs-lookup"><span data-stu-id="e29ca-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="e29ca-109">Podany interfejs metadanych i nazwę pliku, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać symbole debugowania, skojarzone z modułem.</span><span class="sxs-lookup"><span data-stu-id="e29ca-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="e29ca-110">GetReaderFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="e29ca-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="e29ca-111">Podany interfejs metadanych i strumienia, który zawiera magazyn symboli, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać debugowanie symboli z magazynu podanego symbolu.</span><span class="sxs-lookup"><span data-stu-id="e29ca-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e29ca-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e29ca-112">Requirements</span></span>  
 <span data-ttu-id="e29ca-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e29ca-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e29ca-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e29ca-114">See also</span></span>

- [<span data-ttu-id="e29ca-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="e29ca-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="e29ca-116">ISymUnmanagedBinder2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e29ca-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="e29ca-117">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e29ca-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
