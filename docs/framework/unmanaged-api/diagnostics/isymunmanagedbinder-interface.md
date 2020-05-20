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
ms.openlocfilehash: f4f925282d65cd9cbc8eb1c8825f358602de68ed
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441698"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="6a1f9-102">ISymUnmanagedBinder — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6a1f9-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="6a1f9-103">Reprezentuje spinacz symboliczny dla niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6a1f9-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6a1f9-104">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych programu (PDB) z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="6a1f9-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a1f9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6a1f9-105">Methods</span></span>  
  
|<span data-ttu-id="6a1f9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6a1f9-106">Method</span></span>|<span data-ttu-id="6a1f9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6a1f9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a1f9-108">GetReaderForFile, metoda</span><span class="sxs-lookup"><span data-stu-id="6a1f9-108">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="6a1f9-109">W przypadku interfejsu metadanych i nazwy pliku funkcja zwraca poprawną strukturę [ISymUnmanagedReader](isymunmanagedreader-interface.md) , która odczyta symbole debugowania skojarzone z modułem.</span><span class="sxs-lookup"><span data-stu-id="6a1f9-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="6a1f9-110">GetReaderFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="6a1f9-110">GetReaderFromStream Method</span></span>](isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="6a1f9-111">Podano interfejs metadanych i strumień zawierający magazyn symboli, zwracając poprawną strukturę [ISymUnmanagedReader](isymunmanagedreader-interface.md) , która odczyta symbole debugowania z danego magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="6a1f9-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a1f9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a1f9-112">Requirements</span></span>  
 <span data-ttu-id="6a1f9-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6a1f9-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1f9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a1f9-114">See also</span></span>

- [<span data-ttu-id="6a1f9-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="6a1f9-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="6a1f9-116">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6a1f9-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="6a1f9-117">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6a1f9-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
