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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a17752257589ea4ee4d9e58182d4448f02f6460
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46568624"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="b0f34-102">Obsługa wyjątków międzyoperacyjności COM</span><span class="sxs-lookup"><span data-stu-id="b0f34-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="b0f34-103">Zarządzanego i niezarządzanego kodu mogą współpracować ze sobą, aby obsłużyć wyjątki.</span><span class="sxs-lookup"><span data-stu-id="b0f34-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="b0f34-104">Jeśli metoda zgłasza wyjątek w kodzie zarządzanym, środowisko uruchomieniowe języka wspólnego może przekazywać wartość HRESULT do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="b0f34-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="b0f34-105">Jeśli metoda nie powiedzie się w niezarządzanym kodzie, zwracając błąd HRESULT, środowisko wykonawcze zgłasza wyjątek, który może zostać przechwycony przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="b0f34-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="b0f34-106">Środowisko wykonawcze automatycznie mapuje wynik HRESULT COM interop bardziej szczegółowe wyjątki.</span><span class="sxs-lookup"><span data-stu-id="b0f34-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="b0f34-107">Na przykład staje się E_ACCESSDENIED <xref:System.UnauthorizedAccessException>, staje się E_OUTOFMEMORY <xref:System.OutOfMemoryException>i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b0f34-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="b0f34-108">Jeśli HRESULT znajduje się wynik niestandardowych lub jeśli jest nieznany do środowiska uruchomieniowego, środowisko uruchomieniowe przekazuje ogólnego <xref:System.Runtime.InteropServices.COMException> do klienta.</span><span class="sxs-lookup"><span data-stu-id="b0f34-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="b0f34-109">**ErrorCode** właściwość **COMException** zawiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b0f34-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="b0f34-110">Praca z IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="b0f34-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="b0f34-111">Gdy błąd jest przekazywany z modelu COM z kodem zarządzanym, środowisko uruchomieniowe wypełnia obiekt wyjątku przy użyciu informacji o błędzie.</span><span class="sxs-lookup"><span data-stu-id="b0f34-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="b0f34-112">Obiekty COM, które obsługują IErrorInfo i zwracać wartości HRESULT przekazać tę informację do wyjątków w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="b0f34-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="b0f34-113">Na przykład, środowisko uruchomieniowe mapuje opis błędu modelu COM, z wyjątkiem <xref:System.Exception.Message%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0f34-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="b0f34-114">Jeśli wynik HRESULT udostępniane nie dodatkowe informacje o błędzie, środowisko uruchomieniowe wypełnia wiele właściwości wyjątku z wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="b0f34-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="b0f34-115">Jeśli metoda nie powiedzie się w niezarządzanym kodzie, wyjątek może być przekazywany do segmentu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b0f34-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="b0f34-116">Temat [wyników HRESULT i wyjątków](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) zawiera tabelę przedstawiającą sposób mapowania wartości HRESULT do obiektów wyjątków czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b0f34-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="b0f34-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0f34-117">See also</span></span>

- [<span data-ttu-id="b0f34-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="b0f34-118">Exceptions</span></span>](index.md)
