---
title: ISymENCUnmanagedMethod — Interfejs
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 575c732cf1b1caf4700568a9d168463359d1ad7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425506"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="5a6aa-102">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5a6aa-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="5a6aa-103">Informacje dotyczące funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="5a6aa-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a6aa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5a6aa-104">Methods</span></span>  
  
|<span data-ttu-id="5a6aa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5a6aa-105">Method</span></span>|<span data-ttu-id="5a6aa-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5a6aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a6aa-107">GetDocumentsForMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="5a6aa-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="5a6aa-108">Pobiera dokumentów, które ta metoda ma wiersze w.</span><span class="sxs-lookup"><span data-stu-id="5a6aa-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="5a6aa-109">GetDocumentsForMethodCount, metoda</span><span class="sxs-lookup"><span data-stu-id="5a6aa-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="5a6aa-110">Pobiera liczbę dokumentów, które ta metoda ma wiersze w.</span><span class="sxs-lookup"><span data-stu-id="5a6aa-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="5a6aa-111">GetFileNameFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="5a6aa-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="5a6aa-112">Pobiera nazwę pliku dla wiersz skojarzony z przesunięciem.</span><span class="sxs-lookup"><span data-stu-id="5a6aa-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="5a6aa-113">GetLineFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="5a6aa-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="5a6aa-114">Pobiera informacje o wiersz skojarzony z przesunięciem.</span><span class="sxs-lookup"><span data-stu-id="5a6aa-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="5a6aa-115">GetSourceExtentInDocument, metoda</span><span class="sxs-lookup"><span data-stu-id="5a6aa-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="5a6aa-116">Pobiera najmniejszą liczbę wierszy i uruchomić największy wiersz end dla metody w określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5a6aa-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a6aa-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a6aa-117">Requirements</span></span>  
 <span data-ttu-id="5a6aa-118">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5a6aa-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a6aa-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a6aa-119">See Also</span></span>  
 [<span data-ttu-id="5a6aa-120">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="5a6aa-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
