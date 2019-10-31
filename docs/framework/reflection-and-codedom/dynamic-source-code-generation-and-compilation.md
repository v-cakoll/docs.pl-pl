---
title: Dynamiczne generowanie i kompilacja kodu źródłowego
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
ms.openlocfilehash: a7e341bb5bfb5b4648a222409951275169a29b79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130254"
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="d583c-102">Dynamiczne generowanie i kompilacja kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="d583c-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="d583c-103">.NET Framework obejmuje mechanizm o nazwie Code Document Object Model (CodeDOM), który umożliwia deweloperom programów, które emitują kod źródłowy w celu generowania kodu źródłowego w wielu językach programowania w czasie wykonywania, na podstawie jednego modelu, który reprezentuje kod do renderowania.</span><span class="sxs-lookup"><span data-stu-id="d583c-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="d583c-104">Aby reprezentować kod źródłowy, elementy CodeDOM są połączone ze sobą, aby utworzyć strukturę danych znaną jako wykres CodeDOM, który modeluje strukturę pewnego kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d583c-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="d583c-105">Przestrzeń nazw `System.CodeDom` definiuje typy, które mogą reprezentować logiczną strukturę kodu źródłowego niezależnie od określonego języka programowania.</span><span class="sxs-lookup"><span data-stu-id="d583c-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="d583c-106">Przestrzeń nazw `System.CodeDom.Compiler` definiuje typy do generowania kodu źródłowego z wykresów CodeDOM i zarządzania kompilacją kodu źródłowego w obsługiwanych językach.</span><span class="sxs-lookup"><span data-stu-id="d583c-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="d583c-107">Dostawcy lub deweloperzy kompilatora mogą rozciągnąć zestaw obsługiwanych języków.</span><span class="sxs-lookup"><span data-stu-id="d583c-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="d583c-108">Modelowanie kodu źródłowego niezależne od języka może być przydatne, gdy program musi wygenerować kod źródłowy dla modelu programu w wielu językach lub dla nieokreślonego języka docelowego.</span><span class="sxs-lookup"><span data-stu-id="d583c-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="d583c-109">Na przykład niektórzy projektanci używają języka CodeDOM jako interfejsu abstrakcji języka do tworzenia kodu źródłowego w prawidłowym języku programowania, jeśli dostępna jest obsługa języka CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="d583c-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="d583c-110">.NET Framework obejmuje generatory kodu i kompilatory kodu dla <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>i <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="d583c-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d583c-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d583c-111">In This Section</span></span>  
 [<span data-ttu-id="d583c-112">Używanie modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d583c-112">Using the CodeDOM</span></span>](using-the-codedom.md)  
 <span data-ttu-id="d583c-113">Opisuje typowe zastosowania i demonstruje Tworzenie prostego grafu obiektów przy użyciu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="d583c-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="d583c-114">Generowanie kodu źródłowego i kompilowanie programu z wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d583c-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="d583c-115">Opisuje sposób generowania kodu źródłowego i kompilowania wygenerowanego kodu z kompilatorem zewnętrznym przy użyciu klas zdefiniowanych w przestrzeni nazw `System.CodeDom.Compiler`.</span><span class="sxs-lookup"><span data-stu-id="d583c-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="d583c-116">Instrukcje: tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d583c-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="d583c-117">Opisuje, jak używać CodeDOM do generowania kodu za pomocą komentarzy dokumentacji XML i kompilowania wygenerowanego kodu w celu utworzenia danych wyjściowych dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="d583c-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="d583c-118">Instrukcje: tworzenie klasy za pomocą modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d583c-118">How to: Create a Class Using CodeDOM</span></span>](how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="d583c-119">Opisuje, jak używać CodeDOM do wygenerowania klasy zawierającej pola, właściwości, metodę, Konstruktor i punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="d583c-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d583c-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d583c-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="d583c-121">Definiuje elementy reprezentujące elementy kodu w językach programowania przeznaczonych dla środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="d583c-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="d583c-122">Definiuje interfejsy do generowania i kompilowania kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d583c-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d583c-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d583c-123">Related Sections</span></span>  
 <span data-ttu-id="d583c-124">[Zwięzłe odwołanie CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d583c-124">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>  
 <span data-ttu-id="d583c-125">Umożliwia deweloperom znalezienie elementów CodeDOM, które reprezentują elementy kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d583c-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
