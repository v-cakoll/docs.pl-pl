---
title: "Współdziałanie (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2965543066b0846a6a4f8a3199590049947122f2
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="fb27a-102">Współdziałanie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="fb27a-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="fb27a-103">Współdziałanie umożliwia zachowanie i wykorzystać istniejące inwestycje w technologie kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="fb27a-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="fb27a-104">Kod uruchamiany pod kontrolą środowisko uruchomieniowe języka wspólnego (CLR) jest nazywany *kodu zarządzanego*, i jest nazywany kodu uruchamianego poza środowiskiem CLR *niezarządzany kod*.</span><span class="sxs-lookup"><span data-stu-id="fb27a-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="fb27a-105">COM, COM +, składniki C++, składników ActiveX i interfejsu API Win32 usługi Microsoft są przykłady kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="fb27a-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="fb27a-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umożliwia współdziałanie z kodem niezarządzanym za pośrednictwem platformy wywołania usług, <xref:System.Runtime.InteropServices> przestrzeni nazw, współdziałanie języka C++ i współdziałanie COM (Usługa międzyoperacyjna modelu COM).</span><span class="sxs-lookup"><span data-stu-id="fb27a-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fb27a-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fb27a-107">In This Section</span></span>  
 [<span data-ttu-id="fb27a-108">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="fb27a-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="fb27a-109">W tym artykule opisano metody współpraca między kodem C# zarządzanego i kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="fb27a-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="fb27a-110">Porady: dostęp do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#</span><span class="sxs-lookup"><span data-stu-id="fb27a-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="fb27a-111">Zawiera opis funkcji, które zostały wprowadzone w programie Visual C# ułatwia programowanie Office.</span><span class="sxs-lookup"><span data-stu-id="fb27a-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="fb27a-112">Porady: użycie właściwości indeksowanych w programowaniu usługi Międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="fb27a-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="fb27a-113">W tym artykule opisano, jak używać właściwości indeksowanych do dostępu do właściwości modelu COM, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="fb27a-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="fb27a-114">Porady: użycie wywołania platformy do odtwarzania pliku Wave</span><span class="sxs-lookup"><span data-stu-id="fb27a-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="fb27a-115">Informacje dotyczące używania platformy wywołania usług do odtwarzania pliku dźwiękowego .wav w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="fb27a-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="fb27a-116">Wskazówki: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="fb27a-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="fb27a-117">Przedstawia sposób tworzenia skoroszytu programu Excel i dokument programu Word, zawierającą łącze do skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="fb27a-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="fb27a-118">Klasa COM — przykład</span><span class="sxs-lookup"><span data-stu-id="fb27a-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="fb27a-119">Demonstracja ujawnia klasy C# jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="fb27a-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fb27a-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fb27a-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fb27a-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb27a-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="fb27a-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fb27a-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fb27a-123">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="fb27a-123">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="fb27a-124">Wskazówki: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="fb27a-124">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
