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
ms.openlocfilehash: e2160ad4174d9cdfe6e27d2ba7f4748bd473a5f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944231"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="a3ed3-102">ISymUnmanagedBinder — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a3ed3-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="a3ed3-103">Reprezentuje spinacz symboliczny dla niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="a3ed3-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a3ed3-104">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych programu (PDB) z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="a3ed3-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3ed3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a3ed3-105">Methods</span></span>  
  
|<span data-ttu-id="a3ed3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a3ed3-106">Method</span></span>|<span data-ttu-id="a3ed3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a3ed3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3ed3-108">GetReaderForFile, metoda</span><span class="sxs-lookup"><span data-stu-id="a3ed3-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="a3ed3-109">W przypadku interfejsu metadanych i nazwy pliku funkcja zwraca poprawną strukturę [ISymUnmanagedReader](isymunmanagedreader-interface.md) , która odczyta symbole debugowania skojarzone z modułem.</span><span class="sxs-lookup"><span data-stu-id="a3ed3-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="a3ed3-110">GetReaderFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="a3ed3-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="a3ed3-111">Podano interfejs metadanych i strumień zawierający magazyn symboli, zwracając poprawną strukturę [ISymUnmanagedReader](isymunmanagedreader-interface.md) , która odczyta symbole debugowania z danego magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="a3ed3-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3ed3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3ed3-112">Requirements</span></span>  
 <span data-ttu-id="a3ed3-113">**Nagłówki** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a3ed3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ed3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3ed3-114">See also</span></span>

- [<span data-ttu-id="a3ed3-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="a3ed3-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="a3ed3-116">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3ed3-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="a3ed3-117">ISymUnmanagedBinder3, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3ed3-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
