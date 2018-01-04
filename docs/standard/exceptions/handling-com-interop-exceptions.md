---
title: "Obsługa wyjątków międzyoperacyjności COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: error-reference
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e894d07e77b929b1ea22df2d34e542544ec3b1f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="8f4a0-102">Obsługa wyjątków międzyoperacyjności COM</span><span class="sxs-lookup"><span data-stu-id="8f4a0-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="8f4a0-103">Zarządzanego i kodu niezarządzanego mogą współdziałać ze sobą do obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="8f4a0-104">Jeśli metoda zgłosi wyjątek w kodzie zarządzanym, środowisko uruchomieniowe języka wspólnego można przekazać HRESULT do obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="8f4a0-105">W przypadku niepowodzenia metody za pomocą kodu niezarządzanego zwracając błąd HRESULT środowiska uruchomieniowego zgłasza wyjątek, który może być przechwycony przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="8f4a0-106">Środowisko uruchomieniowe mapuje automatycznie HRESULT z międzyoperacyjności z modelem COM na bardziej szczegółowe wyjątki.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="8f4a0-107">Na przykład, staje się E_ACCESSDENIED <xref:System.UnauthorizedAccessException>, staje się E_OUTOFMEMORY <xref:System.OutOfMemoryException>i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="8f4a0-108">Jeśli HRESULT znajduje się wynik niestandardowych lub jeśli jest on nieznany do środowiska wykonawczego, środowisko uruchomieniowe przekazuje ogólnego <xref:System.Runtime.InteropServices.COMException> do klienta.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="8f4a0-109">**ErrorCode** właściwość **COMException** zawiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="8f4a0-110">Praca z IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="8f4a0-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="8f4a0-111">Po upływie błąd z modelu COM do kodu zarządzanego środowiska wykonawczego wypełnia obiekt wyjątku z informacje o błędzie.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="8f4a0-112">Obiekty COM, które obsługują IErrorInfo i zwrócić wyników HRESULT Przekaż te informacje do wyjątków kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="8f4a0-113">Na przykład środowiska uruchomieniowego mapuje opis błędu COM z wyjątkiem <xref:System.Exception.Message%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="8f4a0-114">Jeśli wynik HRESULT udostępnia nie dodatkowe informacje o błędzie, środowisko uruchomieniowe wypełnia wiele właściwości wyjątku z wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="8f4a0-115">Jeśli metoda nie powiedzie się za pomocą kodu niezarządzanego, wyjątek mogą być przekazywane do segmentu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="8f4a0-116">Temat [wyników HRESULT i wyjątków](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) zawiera tabelę przedstawiającą jak mapowanie wyników HRESULT do obiektów wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8f4a0-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="8f4a0-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f4a0-117">See Also</span></span>
[<span data-ttu-id="8f4a0-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="8f4a0-118">Exceptions</span></span>](index.md) 
