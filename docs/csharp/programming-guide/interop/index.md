---
title: Interoperacyjność — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712055"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="1bba0-102">Współdziałanie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1bba0-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="1bba0-103">Współdziałanie umożliwia zachowanie i wykorzystanie istniejących inwestycji w kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="1bba0-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="1bba0-104">Kod, który jest uruchamiany pod kontrolą wspólnego języka runtime (CLR) jest nazywany *kodem zarządzanym,* a kod, który działa poza CLR jest nazywany *kodem niezarządzanym*.</span><span class="sxs-lookup"><span data-stu-id="1bba0-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="1bba0-105">Przykłady niezarządzanego kodu COM+, C++, składników ActiveX i interfejsu API systemu Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="1bba0-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="1bba0-106">Program .NET Framework umożliwia współdziałanie z kodem niezarządzanym za pośrednictwem usług wywoływania platformy, przestrzeni <xref:System.Runtime.InteropServices> nazw, współdziałania języka C++ i współdziałania modelu COM (COM interop).</span><span class="sxs-lookup"><span data-stu-id="1bba0-106">The .NET Framework enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1bba0-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1bba0-107">In This Section</span></span>  
 [<span data-ttu-id="1bba0-108">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="1bba0-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="1bba0-109">W tym artykule opisano metody współdziałania między kodem zarządzanym języka C# a kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="1bba0-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="1bba0-110">Uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji języka C#</span><span class="sxs-lookup"><span data-stu-id="1bba0-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="1bba0-111">W tym artykule opisano funkcje wprowadzone w języku Visual C# w celu ułatwienia programowania pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="1bba0-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="1bba0-112">Używanie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="1bba0-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="1bba0-113">W tym artykule opisano, jak używać właściwości indeksowanych do uzyskiwania dostępu do właściwości COM, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="1bba0-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="1bba0-114">Używanie wywołania platformy do odtwarzania pliku WAV</span><span class="sxs-lookup"><span data-stu-id="1bba0-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="1bba0-115">W tym artykule opisano, jak używać usług wywoływania platformy do odtwarzania pliku dźwiękowego .wav w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="1bba0-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="1bba0-116">Instruktaż: Programowanie pakietu Office</span><span class="sxs-lookup"><span data-stu-id="1bba0-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="1bba0-117">Pokazuje, jak utworzyć skoroszyt programu Excel i dokument programu Word zawierający łącze do skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="1bba0-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="1bba0-118">Przykładowa klasa modelu COM</span><span class="sxs-lookup"><span data-stu-id="1bba0-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="1bba0-119">Pokazuje, jak udostępnić klasy C# jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="1bba0-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1bba0-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1bba0-120">C# Language Specification</span></span>  

<span data-ttu-id="1bba0-121">Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia](~/_csharplang/spec/unsafe-code.md) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="1bba0-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="1bba0-122">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="1bba0-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1bba0-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bba0-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1bba0-124">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="1bba0-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1bba0-125">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="1bba0-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="1bba0-126">Instruktaż: Programowanie pakietu Office</span><span class="sxs-lookup"><span data-stu-id="1bba0-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
