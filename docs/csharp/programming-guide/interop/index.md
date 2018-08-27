---
title: Współdziałanie (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e854c51bd80809b92bb538475a407422b2eba7c0
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925639"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="3bc56-102">Współdziałanie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3bc56-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="3bc56-103">Współdziałanie pozwala na zachowanie i wykorzystać istniejące inwestycje w niezarządzanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="3bc56-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="3bc56-104">Kod, który działa pod kontrolą środowisko uruchomieniowe języka wspólnego (CLR) jest nazywany *kodu zarządzanego*, a kod, który działa poza środowisko CLR jest nazywana *kod niezarządzany*.</span><span class="sxs-lookup"><span data-stu-id="3bc56-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="3bc56-105">COM, COM +, składniki C++, składników ActiveX i Microsoft Win32 API są przykłady kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3bc56-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="3bc56-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umożliwia współdziałanie z kodem niezarządzanym za pośrednictwem platformy wywołania usług <xref:System.Runtime.InteropServices> przestrzeni nazw, współdziałanie języka C++ i współdziałanie z COM (Usługa międzyoperacyjna modelu COM).</span><span class="sxs-lookup"><span data-stu-id="3bc56-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bc56-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3bc56-107">In This Section</span></span>  
 [<span data-ttu-id="3bc56-108">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="3bc56-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="3bc56-109">W tym artykule opisano metody pod kątem współdziałania między kod zarządzany języka C#, a kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="3bc56-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="3bc56-110">Instrukcje: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#</span><span class="sxs-lookup"><span data-stu-id="3bc56-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="3bc56-111">W tym artykule opisano funkcje, które zostały wprowadzone w języku Visual C# do ułatwienia programowania pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="3bc56-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="3bc56-112">Instrukcje: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="3bc56-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="3bc56-113">W tym artykule opisano, jak używać właściwości indeksowanych na dostęp do właściwości modelu COM, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="3bc56-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="3bc56-114">Instrukcje: użycie wywołania platformy do odtwarzania pliku Wave</span><span class="sxs-lookup"><span data-stu-id="3bc56-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="3bc56-115">Opisuje sposób używania platformy wywołania usług do odtwarzania pliku dźwiękowego .wav w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="3bc56-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="3bc56-116">Wskazówki: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="3bc56-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="3bc56-117">Pokazuje, jak utworzyć skoroszytu programu Excel i dokument programu Word, zawierającą łącze do skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="3bc56-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="3bc56-118">Przykładowa klasa modelu COM</span><span class="sxs-lookup"><span data-stu-id="3bc56-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="3bc56-119">Pokazuje, jak udostępnić klasy C# jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="3bc56-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3bc56-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3bc56-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3bc56-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bc56-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="3bc56-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3bc56-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3bc56-123">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="3bc56-123">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="3bc56-124">Wskazówki: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="3bc56-124">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
