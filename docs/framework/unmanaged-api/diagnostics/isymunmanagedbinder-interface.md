---
title: "ISymUnmanagedBinder — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79d3758f57976d08d4599de500e2e12e4d67cb4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="0b218-102">ISymUnmanagedBinder — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0b218-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="0b218-103">Reprezentuje integrator symbol dla kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0b218-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b218-104">Jest to zagrożenie, aby otworzyć plik programu (PDB) bazy danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="0b218-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b218-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0b218-105">Methods</span></span>  
  
|<span data-ttu-id="0b218-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0b218-106">Method</span></span>|<span data-ttu-id="0b218-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0b218-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b218-108">GetReaderForFile, metoda</span><span class="sxs-lookup"><span data-stu-id="0b218-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="0b218-109">Podany interfejs metadanych i nazwę pliku, zwraca poprawny [ISymUnmanagedReader](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać symbole debugowania skojarzone z modułu.</span><span class="sxs-lookup"><span data-stu-id="0b218-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="0b218-110">GetReaderFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="0b218-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="0b218-111">Podany interfejs metadanych i strumienia, który zawiera magazyn symbol zwraca poprawny [ISymUnmanagedReader](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać debugowanie symboli z magazynu podanego symbolu.</span><span class="sxs-lookup"><span data-stu-id="0b218-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b218-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b218-112">Requirements</span></span>  
 <span data-ttu-id="0b218-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0b218-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b218-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b218-114">See Also</span></span>  
 [<span data-ttu-id="0b218-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="0b218-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="0b218-116">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b218-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="0b218-117">ISymUnmanagedBinder3, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b218-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
