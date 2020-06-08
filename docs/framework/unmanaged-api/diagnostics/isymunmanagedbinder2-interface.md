---
title: ISymUnmanagedBinder2 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
ms.openlocfilehash: f6155eb777b5071ff522af4f27d5fb2d73aa25ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501836"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="fc824-102">ISymUnmanagedBinder2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fc824-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="fc824-103">Reprezentuje spinacz symboliczny dla kodu niezarządzanego i rozszerza interfejs [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fc824-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc824-104">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych programu (PDB) z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="fc824-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc824-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fc824-105">Methods</span></span>  
  
|<span data-ttu-id="fc824-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fc824-106">Method</span></span>|<span data-ttu-id="fc824-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fc824-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc824-108">GetReaderForFile2, metoda</span><span class="sxs-lookup"><span data-stu-id="fc824-108">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="fc824-109">Podanym interfejsem metadanych i nazwą pliku zwraca poprawny interfejs [ISymUnmanagedReader](isymunmanagedreader-interface.md) , który odczytuje symbole debugowania skojarzone z modułem.</span><span class="sxs-lookup"><span data-stu-id="fc824-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="fc824-110">Zapewnia bardziej rozległe wyszukiwanie niż Metoda [ISymUnmanagedBinder:: GetReaderForFile —](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fc824-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc824-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc824-111">Requirements</span></span>  
 <span data-ttu-id="fc824-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fc824-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc824-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc824-113">See also</span></span>

- [<span data-ttu-id="fc824-114">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="fc824-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="fc824-115">ISymUnmanagedBinder — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fc824-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="fc824-116">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fc824-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
