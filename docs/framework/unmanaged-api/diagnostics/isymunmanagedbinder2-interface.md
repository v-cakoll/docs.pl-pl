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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49949989a48be13bcb70b27e47407d907b284670
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494957"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="b91ac-102">ISymUnmanagedBinder2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b91ac-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="b91ac-103">Reprezentuje integrator symboli dla niezarządzanego kodu i rozszerza [isymunmanagedbinder —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b91ac-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b91ac-104">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych (PDB) programu z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="b91ac-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b91ac-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b91ac-105">Methods</span></span>  
  
|<span data-ttu-id="b91ac-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b91ac-106">Method</span></span>|<span data-ttu-id="b91ac-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b91ac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b91ac-108">GetReaderForFile2, metoda</span><span class="sxs-lookup"><span data-stu-id="b91ac-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="b91ac-109">Podany interfejs metadanych i nazwę pliku, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) interfejs, który zostanie odczytany symbole debugowania, skojarzone z modułem.</span><span class="sxs-lookup"><span data-stu-id="b91ac-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="b91ac-110">Zapewnia bardziej rozbudowane wyszukiwanie niż [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b91ac-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b91ac-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b91ac-111">Requirements</span></span>  
 <span data-ttu-id="b91ac-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b91ac-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91ac-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b91ac-113">See also</span></span>
- [<span data-ttu-id="b91ac-114">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="b91ac-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="b91ac-115">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="b91ac-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="b91ac-116">ISymUnmanagedBinder3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b91ac-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
