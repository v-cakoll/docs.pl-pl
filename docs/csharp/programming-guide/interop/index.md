---
title: Współdziałanie (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: dc68a2a9c21f6fdb9b531bd07428325ac22ebfb6
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "50980651"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="d80a4-102">Współdziałanie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d80a4-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="d80a4-103">Współdziałanie pozwala na zachowanie i wykorzystać istniejące inwestycje w niezarządzanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d80a4-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="d80a4-104">Kod, który działa pod kontrolą środowisko uruchomieniowe języka wspólnego (CLR) jest nazywany *kodu zarządzanego*, a kod, który działa poza środowisko CLR jest nazywana *kod niezarządzany*.</span><span class="sxs-lookup"><span data-stu-id="d80a4-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="d80a4-105">COM, COM +, składniki C++, składników ActiveX i Microsoft Win32 API są przykłady kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d80a4-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="d80a4-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umożliwia współdziałanie z kodem niezarządzanym za pośrednictwem platformy wywołania usług <xref:System.Runtime.InteropServices> przestrzeni nazw, współdziałanie języka C++ i współdziałanie z COM (Usługa międzyoperacyjna modelu COM).</span><span class="sxs-lookup"><span data-stu-id="d80a4-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d80a4-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d80a4-107">In This Section</span></span>  
 [<span data-ttu-id="d80a4-108">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="d80a4-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="d80a4-109">W tym artykule opisano metody pod kątem współdziałania między kod zarządzany języka C#, a kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="d80a4-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="d80a4-110">Instrukcje: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#</span><span class="sxs-lookup"><span data-stu-id="d80a4-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="d80a4-111">W tym artykule opisano funkcje, które zostały wprowadzone w języku Visual C# do ułatwienia programowania pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="d80a4-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="d80a4-112">Instrukcje: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="d80a4-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="d80a4-113">W tym artykule opisano, jak używać właściwości indeksowanych na dostęp do właściwości modelu COM, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="d80a4-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="d80a4-114">Instrukcje: użycie wywołania platformy do odtwarzania pliku Wave</span><span class="sxs-lookup"><span data-stu-id="d80a4-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="d80a4-115">Opisuje sposób używania platformy wywołania usług do odtwarzania pliku dźwiękowego .wav w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="d80a4-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="d80a4-116">Wskazówki: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="d80a4-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="d80a4-117">Pokazuje, jak utworzyć skoroszytu programu Excel i dokument programu Word, zawierającą łącze do skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="d80a4-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="d80a4-118">Przykładowa klasa modelu COM</span><span class="sxs-lookup"><span data-stu-id="d80a4-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="d80a4-119">Pokazuje, jak udostępnić klasy C# jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="d80a4-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d80a4-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d80a4-120">C# Language Specification</span></span>  

<span data-ttu-id="d80a4-121">Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d80a4-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="d80a4-122">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="d80a4-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d80a4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d80a4-123">See Also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="d80a4-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d80a4-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d80a4-125">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="d80a4-125">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
- [<span data-ttu-id="d80a4-126">Wskazówki: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="d80a4-126">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
