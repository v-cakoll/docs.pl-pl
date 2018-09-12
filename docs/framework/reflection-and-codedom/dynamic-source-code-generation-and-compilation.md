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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a90b4214e244bc1f9c5f8e71782e604bd6c7b619
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494242"
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="5aa1e-102">Dynamiczne generowanie i kompilacja kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="5aa1e-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="5aa1e-103">Program .NET Framework zawiera do tego mechanizm nazywany kodu Document Object Model (CodeDOM) umożliwia deweloperom programy, które emitują kod źródłowy do generowania kodu źródłowego w wielu językach programowania, w czasie wykonywania, oparty na jednym modelu, który reprezentuje kod do renderowania.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="5aa1e-104">Do reprezentowania kodem źródłowym, elementami CodeDOM są połączone ze sobą w celu utworzenia struktury danych, nazywane wykresu CodeDOM, który modeluje struktury kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="5aa1e-105">`System.CodeDom` Przestrzeni nazw definiuje typy, które mogą reprezentować logicznej struktury kodu źródłowego, niezależnie od określonego języka programowania.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="5aa1e-106">`System.CodeDom.Compiler` Przestrzeni nazw definiuje typy, generowanie kodu źródłowego z wykresu CodeDOM i zarządzania nimi kompilacja kodu źródłowego w obsługiwanych językach.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="5aa1e-107">Kompilator dostawców lub deweloperów, można rozszerzyć zbiór języków.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="5aa1e-108">Modelowanie kodu źródłowego niezależnego od języka mogą być przydatne, gdy program wymaga wygenerować kod źródłowy dla modelu programu, w wielu językach lub niepewne języka docelowego.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="5aa1e-109">Na przykład niektóre projektantów umożliwia CodeDOM jako interfejs abstrakcji języka generuje kod źródłowy w języku programowania, jeśli dostępna jest obsługa CodeDOM dla języka.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="5aa1e-110">Program .NET Framework zawiera generatorów kodu i kompilatory kodu <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, i <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5aa1e-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5aa1e-111">In This Section</span></span>  
 [<span data-ttu-id="5aa1e-112">Używanie modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="5aa1e-112">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 <span data-ttu-id="5aa1e-113">W tym artykule opisano typowe zastosowania i pokazuje, tworzenia grafu prostego obiektu za pomocą modelu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="5aa1e-114">Generowanie kodu źródłowego i kompilacja programu z wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="5aa1e-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="5aa1e-115">W tym artykule opisano sposób generowania kodu źródłowego i kompilowania wygenerowanego kodu za pomocą zewnętrznego kompilatora przy użyciu klas zdefiniowanych w `System.CodeDom.Compiler` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="5aa1e-116">Instrukcje: tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="5aa1e-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="5aa1e-117">W tym artykule opisano, jak za pomocą modelu CodeDOM generowanie kodu za pomocą komentarzy dokumentacji XML i kompilowania wygenerowanego kodu, aby tworzy dane wyjściowe dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="5aa1e-118">Instrukcje: tworzenie klasy za pomocą modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="5aa1e-118">How to: Create a Class Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="5aa1e-119">W tym artykule opisano, jak wygenerować klasę, zawierający pola, właściwości, metody, Konstruktor i punktu wejścia za pomocą modelu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5aa1e-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="5aa1e-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="5aa1e-121">Definiuje elementy, które reprezentują elementy kodu w językach programowania przeznaczonych środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="5aa1e-122">Definiuje interfejsów Generowanie i kompilowanie kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5aa1e-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5aa1e-123">Related Sections</span></span>  
 [<span data-ttu-id="5aa1e-124">CodeDOM — podręczny wykaz</span><span class="sxs-lookup"><span data-stu-id="5aa1e-124">CodeDOM Quick Reference</span></span>](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 <span data-ttu-id="5aa1e-125">Umożliwia szybkie dla deweloperów można znaleźć elementów CodeDOM, które reprezentują elementy kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5aa1e-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
