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
ms.openlocfilehash: 8a4fbb40ec2426d000628fbd6d5f0241d3152c18
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441672"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="1dc82-102">ISymUnmanagedBinder2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1dc82-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="1dc82-103">Reprezentuje spinacz symboliczny dla kodu niezarządzanego i rozszerza interfejs [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1dc82-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1dc82-104">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych programu (PDB) z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="1dc82-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1dc82-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1dc82-105">Methods</span></span>  
  
|<span data-ttu-id="1dc82-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1dc82-106">Method</span></span>|<span data-ttu-id="1dc82-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1dc82-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1dc82-108">GetReaderForFile2, metoda</span><span class="sxs-lookup"><span data-stu-id="1dc82-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="1dc82-109">Podanym interfejsem metadanych i nazwą pliku zwraca poprawny interfejs [ISymUnmanagedReader](isymunmanagedreader-interface.md) , który odczytuje symbole debugowania skojarzone z modułem.</span><span class="sxs-lookup"><span data-stu-id="1dc82-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="1dc82-110">Zapewnia bardziej rozległe wyszukiwanie niż Metoda [ISymUnmanagedBinder:: GetReaderForFile —](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1dc82-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1dc82-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1dc82-111">Requirements</span></span>  
 <span data-ttu-id="1dc82-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1dc82-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc82-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dc82-113">See also</span></span>

- [<span data-ttu-id="1dc82-114">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="1dc82-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="1dc82-115">ISymUnmanagedBinder — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1dc82-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="1dc82-116">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1dc82-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
