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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940065"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="daaca-102">ISymUnmanagedBinder — Interfejs</span><span class="sxs-lookup"><span data-stu-id="daaca-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="daaca-103">Reprezentuje integrator symboli dla niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="daaca-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="daaca-104">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych (PDB) programu z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="daaca-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="daaca-105">Metody</span><span class="sxs-lookup"><span data-stu-id="daaca-105">Methods</span></span>  
  
|<span data-ttu-id="daaca-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="daaca-106">Method</span></span>|<span data-ttu-id="daaca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="daaca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="daaca-108">GetReaderForFile, metoda</span><span class="sxs-lookup"><span data-stu-id="daaca-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="daaca-109">Podany interfejs metadanych i nazwę pliku, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać symbole debugowania, skojarzone z modułem.</span><span class="sxs-lookup"><span data-stu-id="daaca-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="daaca-110">GetReaderFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="daaca-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="daaca-111">Podany interfejs metadanych i strumienia, który zawiera magazyn symboli, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać debugowanie symboli z magazynu podanego symbolu.</span><span class="sxs-lookup"><span data-stu-id="daaca-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="daaca-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="daaca-112">Requirements</span></span>  
 <span data-ttu-id="daaca-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="daaca-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daaca-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="daaca-114">See also</span></span>

- [<span data-ttu-id="daaca-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="daaca-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="daaca-116">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="daaca-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="daaca-117">ISymUnmanagedBinder3, interfejs</span><span class="sxs-lookup"><span data-stu-id="daaca-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
