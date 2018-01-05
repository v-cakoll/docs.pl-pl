---
title: "ISymENCUnmanagedMethod — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod
helpviewer_keywords: ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7cc1cea74cc632c65c7e3c2aee408e2f9e864d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="61c8a-102">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="61c8a-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="61c8a-103">Informacje dotyczące funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="61c8a-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61c8a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="61c8a-104">Methods</span></span>  
  
|<span data-ttu-id="61c8a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="61c8a-105">Method</span></span>|<span data-ttu-id="61c8a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="61c8a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61c8a-107">GetDocumentsForMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="61c8a-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="61c8a-108">Pobiera dokumentów, które ta metoda ma wiersze w.</span><span class="sxs-lookup"><span data-stu-id="61c8a-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="61c8a-109">GetDocumentsForMethodCount, metoda</span><span class="sxs-lookup"><span data-stu-id="61c8a-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="61c8a-110">Pobiera liczbę dokumentów, które ta metoda ma wiersze w.</span><span class="sxs-lookup"><span data-stu-id="61c8a-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="61c8a-111">GetFileNameFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="61c8a-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="61c8a-112">Pobiera nazwę pliku dla wiersz skojarzony z przesunięciem.</span><span class="sxs-lookup"><span data-stu-id="61c8a-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="61c8a-113">GetLineFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="61c8a-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="61c8a-114">Pobiera informacje o wiersz skojarzony z przesunięciem.</span><span class="sxs-lookup"><span data-stu-id="61c8a-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="61c8a-115">GetSourceExtentInDocument, metoda</span><span class="sxs-lookup"><span data-stu-id="61c8a-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="61c8a-116">Pobiera najmniejszą liczbę wierszy i uruchomić największy wiersz end dla metody w określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="61c8a-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61c8a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61c8a-117">Requirements</span></span>  
 <span data-ttu-id="61c8a-118">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="61c8a-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c8a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61c8a-119">See Also</span></span>  
 [<span data-ttu-id="61c8a-120">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="61c8a-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
