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
ms.openlocfilehash: 9c8eb374058ddbd2ba3d866079f0f40b292b69ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286109"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="48ea7-102">Obsługa wyjątków międzyoperacyjności COM</span><span class="sxs-lookup"><span data-stu-id="48ea7-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="48ea7-103">Kod zarządzany i niezarządzany może współdziałać ze sobą w celu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="48ea7-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="48ea7-104">Jeśli metoda zgłasza wyjątek w kodzie zarządzanym, środowisko uruchomieniowe języka wspólnego może przekazać wynik HRESULT do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="48ea7-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="48ea7-105">Jeśli metoda zakończy się niepowodzeniem w kodzie niezarządzanym przez zwrócenie błędu HRESULT, środowisko uruchomieniowe zgłasza wyjątek, który może zostać przechwycony przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="48ea7-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="48ea7-106">Środowisko uruchomieniowe automatycznie mapuje wynik HRESULT z międzyoperacyjności modelu COM do bardziej szczegółowych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="48ea7-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="48ea7-107">Na przykład E_ACCESSDENIED jest <xref:System.UnauthorizedAccessException> E_OUTOFMEMORY <xref:System.OutOfMemoryException> i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="48ea7-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="48ea7-108">Jeśli HRESULT jest wynikiem niestandardowym lub jeśli jest nieznany dla środowiska uruchomieniowego, środowisko uruchomieniowe przekazuje <xref:System.Runtime.InteropServices.COMException> do klienta ogólne.</span><span class="sxs-lookup"><span data-stu-id="48ea7-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="48ea7-109">Właściwość **ErrorCode** elementu **COMEXCEPTION** zawiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="48ea7-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="48ea7-110">Praca z IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="48ea7-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="48ea7-111">Po przekazaniu błędu z modelu COM do kodu zarządzanego środowisko uruchomieniowe wypełnia obiekt wyjątku informacjami o błędzie.</span><span class="sxs-lookup"><span data-stu-id="48ea7-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="48ea7-112">Obiekty COM obsługujące IErrorInfo i zwracają wartości HRESULT zawierają te informacje do wyjątków kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="48ea7-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="48ea7-113">Na przykład środowisko uruchomieniowe mapuje opis z błędu COM na <xref:System.Exception.Message%2A> Właściwość wyjątku.</span><span class="sxs-lookup"><span data-stu-id="48ea7-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="48ea7-114">Jeśli HRESULT nie zawiera żadnych dodatkowych informacji o błędzie, środowisko uruchomieniowe wypełnia wiele właściwości wyjątku z wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="48ea7-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="48ea7-115">Jeśli metoda zakończy się niepowodzeniem w kodzie niezarządzanym, można przekazywać wyjątek do segmentu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="48ea7-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="48ea7-116">Temat [HResults i Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) zawiera tabelę przedstawiającą sposób, w jaki HRESULT są mapowane na obiekty wyjątków czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="48ea7-116">The topic [HRESULTS and Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="48ea7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48ea7-117">See also</span></span>

- [<span data-ttu-id="48ea7-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="48ea7-118">Exceptions</span></span>](index.md)
