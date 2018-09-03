---
title: Używanie modelu CodeDOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50ff6e2baaee683674f82cff178eeef7b7e43de4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486215"
---
# <a name="using-the-codedom"></a><span data-ttu-id="ea4b4-102">Używanie modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="ea4b4-102">Using the CodeDOM</span></span>
<span data-ttu-id="ea4b4-103">CodeDOM zawiera typy, które reprezentują wiele typowych elementów kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-103">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="ea4b4-104">Można zaprojektować program, który tworzy model kodu źródłowego za pomocą elementów CodeDOM, aby zamontować wykresu obiektu.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-104">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="ea4b4-105">Wykres tego obiektu może być renderowany jako kod źródłowy za pomocą generatora kodu CodeDOM dla obsługiwanego języka programowania.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-105">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="ea4b4-106">CodeDOM może również skompilować kod źródłowy do zestawu binarnego.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-106">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="ea4b4-107">Jedne z typowych zastosowań CodeDom obejmują:</span><span class="sxs-lookup"><span data-stu-id="ea4b4-107">Some common uses for the CodeDOM include:</span></span>  
  
-   <span data-ttu-id="ea4b4-108">Generowanie kodu szablonu: generowanie kodu dla programu ASP.NET, serwerów proxy klienta usług XML sieci Web, kreatorów kodu, projektantów lub innych mechanizmów emitujących kod.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-108">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
-   <span data-ttu-id="ea4b4-109">Dynamiczna kompilacja: wspieranie kompilacji kodu w jednym lub wielu języków.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-109">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="ea4b4-110">Tworzenie wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="ea4b4-110">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="ea4b4-111"><xref:System.CodeDom> Przestrzeń nazw zawiera klasy do reprezentowania logicznej struktury kodu źródłowego, niezależnie od składni języka.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-111">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="ea4b4-112">Struktura wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="ea4b4-112">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="ea4b4-113">Struktura wykresu CodeDOM jest drzewo kontenerów.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-113">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="ea4b4-114">Najważniejsze, lub katalogu głównego, kontener każdego nadawać wykresu CodeDOM <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-114">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="ea4b4-115">Każdy element modelu kodu źródłowego musi być połączony z wykresem za pomocą właściwości <xref:System.CodeDom.CodeObject> na wykresie.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-115">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="ea4b4-116">Tworzenie modelu kodu źródłowego dla przykładowy Program Hello World</span><span class="sxs-lookup"><span data-stu-id="ea4b4-116">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="ea4b4-117">Następujące instruktaż zawiera przykład sposobu tworzenia wykresu obiektu CodeDOM, który reprezentuje kod dla prostej aplikacji Hello World.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-117">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="ea4b4-118">Aby uzyskać pełnego kodu źródłowego dla tego przykładu kodu, zobacz <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> tematu.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-118">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="ea4b4-119">Tworzenie jednostki kompilacji</span><span class="sxs-lookup"><span data-stu-id="ea4b4-119">Creating a compile unit</span></span>  
 <span data-ttu-id="ea4b4-120">CodeDOM definiuje obiekt o nazwie <xref:System.CodeDom.CodeCompileUnit>, który może odwoływać się do wykresu obiektu CodeDOM, który modeluje kod źródłowy do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-120">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="ea4b4-121">A **elementu CodeCompileUnit** ma właściwości służąca do przechowywania odwołań do atrybutów, przestrzeni nazw i zestawów.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-121">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="ea4b4-122">Dostawcy CodeDom, które wynikają z <xref:System.CodeDom.Compiler.CodeDomProvider> klasy zawierają metody, które przetwarzają wykres obiektu odwołuje się **elementu CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-122">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="ea4b4-123">Do utworzenia wykresu obiektu dla prostej aplikacji, należy utworzyć model kodu źródłowego i odwoływać się do niego z **elementu CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-123">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="ea4b4-124">Możesz utworzyć nową jednostkę kompilacji przy użyciu składni, jak pokazano w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ea4b4-124">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="ea4b4-125">Element <xref:System.CodeDom.CodeSnippetCompileUnit> może zawierać sekcję kodu źródłowego, który jest już w języku docelowym, ale nie może być renderowana na inny język.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="ea4b4-126">Definiowanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="ea4b4-126">Defining a namespace</span></span>  
 <span data-ttu-id="ea4b4-127">Aby zdefiniować obszar nazw, należy utworzyć <xref:System.CodeDom.CodeNamespace> i przypisać mu nazwę, za pomocą odpowiedniego konstruktora lub przez ustawienie jego **nazwa** właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-127">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="ea4b4-128">Importowanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="ea4b4-128">Importing a namespace</span></span>  
 <span data-ttu-id="ea4b4-129">Aby dodać dyrektywę import obszaru nazw do obszaru nazw, należy dodać <xref:System.CodeDom.CodeNamespaceImport> oznacza to, przestrzeń nazw do zaimportowania do **CodeNamespace.Imports** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-129">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="ea4b4-130">Poniższy kod dodaje import dla **systemu** przestrzeń nazw **Importy** zbiór **CodeNamespace** o nazwie `samples`:</span><span class="sxs-lookup"><span data-stu-id="ea4b4-130">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="ea4b4-131">Łączenie elementów kodu na wykresie obiektu</span><span class="sxs-lookup"><span data-stu-id="ea4b4-131">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="ea4b4-132">Wszystkie elementy kodu, które tworzą wykres CodeDOM muszą być połączone z <xref:System.CodeDom.CodeCompileUnit> czyli elementem głównym drzewa przez szereg odwołań między elementami wywoływanymi bezpośrednio z właściwości obiektu głównego wykresu.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-132">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="ea4b4-133">Ustaw obiekt do właściwości obiektu kontenera, aby ustanowić odwołanie z obiektu kontenera.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-133">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="ea4b4-134">Poniższa instrukcja dodaje `samples` **CodeNamespace** do **przestrzenie nazw** kolekcji właściwości głównego **elementu CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-134">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="ea4b4-135">Definiowanie typu</span><span class="sxs-lookup"><span data-stu-id="ea4b4-135">Defining a type</span></span>  
 <span data-ttu-id="ea4b4-136">Aby zadeklarować klasy, struktury, interfejs lub wyliczenie przy użyciu CodeDOM, Utwórz nową <xref:System.CodeDom.CodeTypeDeclaration>i przypisz mu nazwy.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-136">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="ea4b4-137">Poniższy przykład przedstawia, to za pomocą przeciążenia konstruktora, aby ustawić **nazwa** właściwości:</span><span class="sxs-lookup"><span data-stu-id="ea4b4-137">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="ea4b4-138">Aby dodać typ do przestrzeni nazw, należy dodać <xref:System.CodeDom.CodeTypeDeclaration> reprezentujący typu do dodania do obszaru nazw do **typy** zbiór **CodeNamespace**.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-138">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="ea4b4-139">Poniższy przykład pokazuje, jak dodać klasę o nazwie `class1` do **CodeNamespace** o nazwie `samples`:</span><span class="sxs-lookup"><span data-stu-id="ea4b4-139">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="ea4b4-140">Dodawanie elementów członkowskich klasy do klasy</span><span class="sxs-lookup"><span data-stu-id="ea4b4-140">Adding class members to a class</span></span>  
 <span data-ttu-id="ea4b4-141"><xref:System.CodeDom> Przestrzeń nazw zapewnia różne elementy, które mogą służyć do reprezentowania członków klasy.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-141">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="ea4b4-142">Każdy element członkowski klasy mogą być dodawane do **członków** zbiór <xref:System.CodeDom.CodeTypeDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-142">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="ea4b4-143">Definiowanie metody punktu wejścia kodu pliku wykonywalnego</span><span class="sxs-lookup"><span data-stu-id="ea4b4-143">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="ea4b4-144">Jeśli tworzysz kod dla wykonywalnego programu jest wskazanie punktu wejścia programu, tworząc <xref:System.CodeDom.CodeEntryPointMethod> do reprezentowania metody, w której program powinien rozpocząć wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-144">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="ea4b4-145">Poniższy przykład ilustruje sposób definiowania metody punktu wejścia, który zawiera <xref:System.CodeDom.CodeMethodInvokeExpression> wywołująca **System.Console.WriteLine** do drukowania "Hello World!":</span><span class="sxs-lookup"><span data-stu-id="ea4b4-145">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="ea4b4-146">Poniższa instrukcja dodaje metody punktu wejścia o nazwie `Start` do **członków** zbiór `class1`:</span><span class="sxs-lookup"><span data-stu-id="ea4b4-146">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="ea4b4-147">Teraz <xref:System.CodeDom.CodeCompileUnit> o nazwie `compileUnit` zawiera wykres CodeDOM dla prostego programu Witaj świecie.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-147">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="ea4b4-148">Aby uzyskać informacje na temat generowania i kompilowania kodu z wykresu CodeDOM, zobacz [generowania kodu źródłowego i kompilacja programu z wykresu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span><span class="sxs-lookup"><span data-stu-id="ea4b4-148">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="ea4b4-149">Więcej informacji na temat tworzenia wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="ea4b4-149">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="ea4b4-150">CodeDOM obsługuje wiele często spotykanych rodzajów elementów kodu w językach programowania, które obsługują środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-150">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="ea4b4-151">CodeDOM nie został zaprojektowany w celu zapewnienia elementu do reprezentowania wszystkich możliwych funkcji języka programowania.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-151">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="ea4b4-152">Kod, który nie może być reprezentowany w prosty sposób z elementami CodeDOM można hermetyzować w <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, lub <xref:System.CodeDom.CodeSnippetCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-152">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="ea4b4-153">Jednak fragmentów kodu nie może być przetłumaczone na inne języki automatycznie przez CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-153">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="ea4b4-154">Aby uzyskać dokumentację dla każdego z typów CodeDOM, zobacz dokumentację referencyjną dla <xref:System.CodeDom> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ea4b4-154">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="ea4b4-155">Szybkiego wykresu do zlokalizowania elementu CodeDOM, który reprezentuje określony typ elementu kodu, zobacz [CodeDOM — podręczny wykaz](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524).</span><span class="sxs-lookup"><span data-stu-id="ea4b4-155">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524).</span></span>
