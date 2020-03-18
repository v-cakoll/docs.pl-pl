---
title: Obsługa wyjątków międzyoperacyjności COM
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: 17cd739ac40b43bdd4a93b83a4ab9d0d92400e2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708935"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="548dc-102">Obsługa wyjątków międzyoperacyjności COM</span><span class="sxs-lookup"><span data-stu-id="548dc-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="548dc-103">Kod zarządzany i niezarządzany może współpracować w celu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="548dc-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="548dc-104">Jeśli metoda zgłasza wyjątek w kodzie zarządzanym, czas wykonywania języka wspólnego może przekazać HRESULT do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="548dc-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="548dc-105">Jeśli metoda nie powiedzie się w kodzie niezarządzanym przez zwrócenie błędu HRESULT, czas wykonywania zgłasza wyjątek, który może zostać przechwycony przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="548dc-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="548dc-106">Czas wykonywania automatycznie mapuje HRESULT z com interop do bardziej szczegółowych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="548dc-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="548dc-107">Na przykład, E_ACCESSDENIED <xref:System.UnauthorizedAccessException>staje się <xref:System.OutOfMemoryException>, E_OUTOFMEMORY staje się , i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="548dc-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="548dc-108">Jeśli Wynik HRESULT jest wynikiem niestandardowym lub jeśli nie jest znany <xref:System.Runtime.InteropServices.COMException> do czasu wykonywania, czas wykonywania przekazuje ogólny do klienta.</span><span class="sxs-lookup"><span data-stu-id="548dc-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="548dc-109">**Właściwość ErrorCode** **comexception** zawiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="548dc-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="548dc-110">Praca z IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="548dc-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="548dc-111">Gdy błąd jest przekazywany z COM do kodu zarządzanego, czas wykonywania wypełnia obiekt wyjątku z informacjami o błędzie.</span><span class="sxs-lookup"><span data-stu-id="548dc-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="548dc-112">Obiekty COM, które obsługują IErrorInfo i zwracają HRESULTS podać te informacje do wyjątków kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="548dc-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="548dc-113">Na przykład czas wykonywania mapuje opis z błędu <xref:System.Exception.Message%2A> COM do właściwości wyjątku.</span><span class="sxs-lookup"><span data-stu-id="548dc-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="548dc-114">Jeśli HRESULT nie zawiera żadnych dodatkowych informacji o błędzie, czas wykonywania wypełnia wiele właściwości wyjątku wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="548dc-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="548dc-115">Jeśli metoda nie powiedzie się w kodzie niezarządzanym, wyjątek można przekazać do segmentu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="548dc-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="548dc-116">Temat [HRESULTS i wyjątki](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) zawiera tabelę pokazującą, jak Mapa HRESULTS do obiektów wyjątków w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="548dc-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="548dc-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="548dc-117">See also</span></span>

- [<span data-ttu-id="548dc-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="548dc-118">Exceptions</span></span>](index.md)
