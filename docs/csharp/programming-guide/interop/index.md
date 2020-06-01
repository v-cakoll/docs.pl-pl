---
title: Współdziałanie — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e53465066cf27a5f46c66ac73ee242370be23395
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84242010"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="26744-102">Współdziałanie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="26744-102">Interoperability (C# Programming Guide)</span></span>

<span data-ttu-id="26744-103">Współdziałanie pozwala zachować istniejące inwestycje w kodzie niezarządzanym i korzystać z nich.</span><span class="sxs-lookup"><span data-stu-id="26744-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="26744-104">Kod, który jest uruchamiany pod kontrolą środowiska uruchomieniowego języka wspólnego (CLR) jest nazywany *kodem zarządzanym*, a kod, który jest URUCHAMIANY poza środowiskiem CLR, jest nazywany *kodem niezarządzanym*.</span><span class="sxs-lookup"><span data-stu-id="26744-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="26744-105">Przykłady kodu niezarządzanego modelu COM, COM+, C++, Components, ActiveX i Microsoft Windows API.</span><span class="sxs-lookup"><span data-stu-id="26744-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
<span data-ttu-id="26744-106">Platforma .NET umożliwia współdziałanie z kodem niezarządzanym za pomocą usług wywołania platformy, <xref:System.Runtime.InteropServices> przestrzeni nazw, współdziałania C++ i współdziałania modelu COM (międzyoperacyjna com)</span><span class="sxs-lookup"><span data-stu-id="26744-106">.NET enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26744-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="26744-107">In This Section</span></span>  
 [<span data-ttu-id="26744-108">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="26744-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="26744-109">Opisuje metody współpracy między kodem zarządzanym C# i niezarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="26744-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="26744-110">Uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji języka C#</span><span class="sxs-lookup"><span data-stu-id="26744-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="26744-111">Zawiera opis funkcji wprowadzonych w Visual C# w celu ułatwienia programowania pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="26744-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="26744-112">Używanie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="26744-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="26744-113">Opisuje sposób używania właściwości indeksowanych w celu uzyskania dostępu do właściwości COM, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="26744-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="26744-114">Używanie wywołania platformy do odtwarzania pliku WAV</span><span class="sxs-lookup"><span data-stu-id="26744-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="26744-115">Opisuje, jak używać usług wywołania platformy do odtwarzania pliku dźwiękowego WAV w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="26744-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="26744-116">Przewodnik: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="26744-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="26744-117">Pokazuje, jak utworzyć skoroszyt programu Excel i dokument programu Word, który zawiera link do skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="26744-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="26744-118">Klasa COM — Przykład</span><span class="sxs-lookup"><span data-stu-id="26744-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="26744-119">Pokazuje, jak uwidocznić klasę języka C# jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="26744-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="26744-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="26744-120">C# Language Specification</span></span>  

<span data-ttu-id="26744-121">Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia](~/_csharplang/spec/unsafe-code.md) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="26744-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="26744-122">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="26744-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="26744-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26744-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="26744-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="26744-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="26744-125">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="26744-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="26744-126">Przewodnik: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="26744-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
