---
title: "Dynamiczne generowanie i kompilacja kodu źródłowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1eb17af8fef96f42973e65859bd17b1e835fa98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="1f013-102">Dynamiczne generowanie i kompilacja kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="1f013-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="1f013-103">Mechanizm wywołuje kod Document Object Model (CodeDOM), który umożliwia deweloperom programów, które Emituj kod źródłowy do generowania kodu źródłowego w wielu języków programowania, w czasie wykonywania, oparte na jednym modelu, który reprezentuje kod zawiera programu .NET Framework do renderowania.</span><span class="sxs-lookup"><span data-stu-id="1f013-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="1f013-104">Do reprezentowania kodu źródłowego, CodeDOM elementy są połączone ze sobą do tworzenia struktury danych, nazywane wykresu CodeDOM modele struktury kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="1f013-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="1f013-105">`System.CodeDom` Przestrzeni nazw definiuje typy reprezentujące struktury logicznej kodu źródłowego, niezależnie od określonego języka programowania.</span><span class="sxs-lookup"><span data-stu-id="1f013-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="1f013-106">`System.CodeDom.Compiler` Przestrzeni nazw określa typy generowanie kodu źródłowego z wykresu CodeDOM i zarządzania nimi kompilacji kodu źródłowego w obsługiwanych językach.</span><span class="sxs-lookup"><span data-stu-id="1f013-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="1f013-107">Dostawcom kompilatora i deweloperzy mogą rozszerzać zestaw obsługiwanych języków.</span><span class="sxs-lookup"><span data-stu-id="1f013-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="1f013-108">Modelowanie kodu źródłowego niezależnego od języka może być przydatna, gdy program wymaga do generowania kodu źródłowego dla modelu programu w wielu językach lub niepewne języka docelowego.</span><span class="sxs-lookup"><span data-stu-id="1f013-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="1f013-109">Na przykład niektóre projektanci używali modelu CodeDOM jako interfejs abstrakcji języka aby wygenerować kod źródłowy w języku programowania, jeśli dostępna jest obsługa CodeDOM dla języka.</span><span class="sxs-lookup"><span data-stu-id="1f013-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="1f013-110">.NET Framework obejmuje generatory kodu i kompilatory kodu dla <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, i <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="1f013-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f013-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1f013-111">In This Section</span></span>  
 [<span data-ttu-id="1f013-112">Używanie modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1f013-112">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 <span data-ttu-id="1f013-113">W tym artykule opisano typowe zastosowania i pokazano tworzenie wykres prostych obiektów przy użyciu modelu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="1f013-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="1f013-114">Generowanie kodu źródłowego i kompilowanie programu z wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1f013-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="1f013-115">Opisuje sposób generowania kodu źródłowego i kompilowania wygenerowanego kodu z zewnętrznego kompilatorem przy użyciu klas zdefiniowanych w `System.CodeDom.Compiler` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1f013-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="1f013-116">Porady: Tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1f013-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="1f013-117">Informacje dotyczące używania CodeDOM do generowania kodu przy użyciu komentarze dokumentacji XML i kompilowania wygenerowanego kodu tak, aby tworzy dane wyjściowe dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="1f013-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="1f013-118">Porady: Tworzenie klasy za pomocą modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1f013-118">How to: Create a Class Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="1f013-119">Informacje dotyczące używania CodeDOM do generowania klasy zawierające pola, właściwości, metody, konstruktora i punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="1f013-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1f013-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="1f013-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="1f013-121">Definiuje elementy, które reprezentują elementy kodu w językach programowania kierowanych środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="1f013-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="1f013-122">Definiuje interfejs Generowanie i kompilowanie kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1f013-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1f013-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="1f013-123">Related Sections</span></span>  
 [<span data-ttu-id="1f013-124">Krótki przewodnik codeDOM</span><span class="sxs-lookup"><span data-stu-id="1f013-124">CodeDOM Quick Reference</span></span>](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 <span data-ttu-id="1f013-125">Umożliwia szybkie dla deweloperów znaleźć elementy CodeDOM, które reprezentują elementy kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="1f013-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
