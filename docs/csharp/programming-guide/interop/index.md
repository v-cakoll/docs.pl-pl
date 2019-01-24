---
title: 'Współdziałanie — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
  - COM interop
  - interoperability
  - 'platform invoke, accessing APIs with C#'
  - 'C# language, interoperability'
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="822e8-102">Współdziałanie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="822e8-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="822e8-103">Współdziałanie pozwala na zachowanie i wykorzystać istniejące inwestycje w niezarządzanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="822e8-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="822e8-104">Kod, który działa pod kontrolą środowisko uruchomieniowe języka wspólnego (CLR) jest nazywany *kodu zarządzanego*, a kod, który działa poza środowisko CLR jest nazywana *kod niezarządzany*.</span><span class="sxs-lookup"><span data-stu-id="822e8-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="822e8-105">COM, COM +, składniki C++, składników ActiveX i Microsoft Win32 API są przykłady kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="822e8-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="822e8-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umożliwia współdziałanie z kodem niezarządzanym za pośrednictwem platformy wywołania usług <xref:System.Runtime.InteropServices> przestrzeni nazw, współdziałanie języka C++ i współdziałanie z COM (Usługa międzyoperacyjna modelu COM).</span><span class="sxs-lookup"><span data-stu-id="822e8-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="822e8-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="822e8-107">In This Section</span></span>  
 [<span data-ttu-id="822e8-108">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="822e8-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="822e8-109">W tym artykule opisano metody pod kątem współdziałania między kod zarządzany języka C#, a kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="822e8-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="822e8-110">Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcji</span><span class="sxs-lookup"><span data-stu-id="822e8-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="822e8-111">W tym artykule opisano funkcje, które zostały wprowadzone w języku Visual C# do ułatwienia programowania pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="822e8-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="822e8-112">Instrukcje: Użycie właściwości indeksowanych w programowaniu usługi Międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="822e8-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="822e8-113">W tym artykule opisano, jak używać właściwości indeksowanych na dostęp do właściwości modelu COM, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="822e8-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="822e8-114">Instrukcje: Użycie wywołania platformy do odtwarzania pliku Wave</span><span class="sxs-lookup"><span data-stu-id="822e8-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="822e8-115">Opisuje sposób używania platformy wywołania usług do odtwarzania pliku dźwiękowego .wav w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="822e8-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="822e8-116">Przewodnik: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="822e8-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="822e8-117">Pokazuje, jak utworzyć skoroszytu programu Excel i dokument programu Word, zawierającą łącze do skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="822e8-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="822e8-118">Przykładowa klasa modelu COM</span><span class="sxs-lookup"><span data-stu-id="822e8-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="822e8-119">Pokazuje, jak udostępnić klasy C# jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="822e8-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="822e8-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="822e8-120">C# Language Specification</span></span>  

<span data-ttu-id="822e8-121">Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="822e8-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="822e8-122">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="822e8-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="822e8-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="822e8-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="822e8-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="822e8-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="822e8-125">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="822e8-125">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)
- [<span data-ttu-id="822e8-126">Przewodnik: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="822e8-126">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
