---
title: "ISymUnmanagedBinder2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder2 Interface
helpviewer_keywords: ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c276f0abedf4ccab92770af649a8dd0afb6d39d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="b4b57-102">ISymUnmanagedBinder2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b4b57-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="b4b57-103">Reprezentuje integrator symbol dla niezarządzanego kodu i rozszerza [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b4b57-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b4b57-104">Jest to zagrożenie, aby otworzyć plik programu (PDB) bazy danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="b4b57-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4b57-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b4b57-105">Methods</span></span>  
  
|<span data-ttu-id="b4b57-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b4b57-106">Method</span></span>|<span data-ttu-id="b4b57-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b4b57-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4b57-108">GetReaderForFile2 — metoda</span><span class="sxs-lookup"><span data-stu-id="b4b57-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="b4b57-109">Podany interfejs metadanych i nazwę pliku, zwraca poprawny <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interfejs, który będzie odczytywać symbole debugowania skojarzone z modułu.</span><span class="sxs-lookup"><span data-stu-id="b4b57-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="b4b57-110">Zapewnia bardziej zaawansowane wyszukiwanie niż [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b4b57-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4b57-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4b57-111">Requirements</span></span>  
 <span data-ttu-id="b4b57-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b4b57-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b57-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4b57-113">See Also</span></span>  
 [<span data-ttu-id="b4b57-114">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="b4b57-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="b4b57-115">ISymUnmanagedBinder — interfejs</span><span class="sxs-lookup"><span data-stu-id="b4b57-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="b4b57-116">ISymUnmanagedBinder3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="b4b57-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
