---
title: Współdziałanie — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 560218361f470266654734971a12de7862722a46
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423180"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="6a31d-102">Współdziałanie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="6a31d-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="6a31d-103">Współdziałanie pozwala zachować istniejące inwestycje w kodzie niezarządzanym i korzystać z nich.</span><span class="sxs-lookup"><span data-stu-id="6a31d-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="6a31d-104">Kod, który jest uruchamiany pod kontrolą środowiska uruchomieniowego języka wspólnego (CLR) jest nazywany *kodem zarządzanym*, a kod, który jest URUCHAMIANY poza środowiskiem CLR, jest nazywany *kodem niezarządzanym*.</span><span class="sxs-lookup"><span data-stu-id="6a31d-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="6a31d-105">COM, COM+, C++ składniki, składniki ActiveX i interfejs API systemu Microsoft Windows to przykłady kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6a31d-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="6a31d-106">.NET Framework umożliwia współdziałanie z kodem niezarządzanym za pomocą usług wywołania platformy, C++ <xref:System.Runtime.InteropServices> przestrzeni nazw, współdziałania i współdziałania modelu COM (międzyoperacyjność com).</span><span class="sxs-lookup"><span data-stu-id="6a31d-106">The .NET Framework enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a31d-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6a31d-107">In This Section</span></span>  
 [<span data-ttu-id="6a31d-108">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="6a31d-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="6a31d-109">Opisuje metody współpracy między C# kodem zarządzanym i niezarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="6a31d-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="6a31d-110">Instrukcje: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#</span><span class="sxs-lookup"><span data-stu-id="6a31d-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="6a31d-111">Zawiera opis funkcji wprowadzonych w wizualizacji C# w celu ułatwienia programowania pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="6a31d-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="6a31d-112">Instrukcje: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="6a31d-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="6a31d-113">Opisuje sposób używania właściwości indeksowanych w celu uzyskania dostępu do właściwości COM, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="6a31d-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="6a31d-114">Instrukcje: użycie wywołania platformy do odtwarzania pliku Wave</span><span class="sxs-lookup"><span data-stu-id="6a31d-114">How to: Use Platform Invoke to Play a Wave File</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="6a31d-115">Opisuje, jak używać usług wywołania platformy do odtwarzania pliku dźwiękowego WAV w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="6a31d-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="6a31d-116">Przewodnik: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="6a31d-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="6a31d-117">Pokazuje, jak utworzyć skoroszyt programu Excel i dokument programu Word, który zawiera link do skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="6a31d-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="6a31d-118">Przykładowa klasa modelu COM</span><span class="sxs-lookup"><span data-stu-id="6a31d-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="6a31d-119">Pokazuje, jak uwidocznić C# klasę jako obiekt com.</span><span class="sxs-lookup"><span data-stu-id="6a31d-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6a31d-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6a31d-120">C# Language Specification</span></span>  

<span data-ttu-id="6a31d-121">Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="6a31d-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="6a31d-122">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="6a31d-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6a31d-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a31d-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6a31d-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6a31d-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6a31d-125">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="6a31d-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="6a31d-126">Przewodnik: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="6a31d-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
