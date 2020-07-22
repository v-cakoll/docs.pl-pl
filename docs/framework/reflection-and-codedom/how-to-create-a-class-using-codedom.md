---
title: 'Porady: tworzenie klasy za pomocą modelu CodeDOM'
description: Zobacz szczegółowy przykład, w którym wyjaśniono, jak utworzyć klasę przy użyciu Code Document Object Model (CodeDOM).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
ms.openlocfilehash: 3d7151d384402dba6fbb5da8fe54621346251f7b
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865310"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="d7ce2-103">Porady: tworzenie klasy za pomocą modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d7ce2-103">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="d7ce2-104">Poniższe procedury ilustrują sposób tworzenia i kompilowania wykresu CodeDOM, który generuje klasę zawierającą dwa pola, trzy właściwości, metodę, Konstruktor i punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-104">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1. <span data-ttu-id="d7ce2-105">Utwórz aplikację konsolową, która będzie używać kodu CodeDOM do generowania kodu źródłowego dla klasy.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-105">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="d7ce2-106">W tym przykładzie Klasa generująca ma nazwę `Sample` , a wygenerowany kod jest klasą o nazwie `CodeDOMCreatedClass` SampleCode.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-106">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2. <span data-ttu-id="d7ce2-107">W klasie generującej zainicjuj wykres CodeDOM i użyj metod CodeDOM, aby zdefiniować elementy członkowskie, Konstruktor i punkt wejścia ( `Main` metodę) wygenerowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-107">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="d7ce2-108">W tym przykładzie wygenerowana Klasa ma dwa pola, trzy właściwości, Konstruktor, metodę i `Main` metodę.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-108">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3. <span data-ttu-id="d7ce2-109">W klasie generującej Utwórz dostawcę kodu specyficzny dla języka i Wywołaj <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodę w celu wygenerowania kodu z grafu.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-109">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4. <span data-ttu-id="d7ce2-110">Skompiluj i uruchom aplikację w celu wygenerowania kodu.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-110">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="d7ce2-111">W tym przykładzie wygenerowany kod znajduje się w pliku o nazwie SampleCode.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-111">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="d7ce2-112">Skompiluj i wykonaj ten kod, aby zobaczyć przykładowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-112">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="d7ce2-113">Aby utworzyć aplikację, która będzie wykonywała kod CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d7ce2-113">To create the application that will execute the CodeDOM code</span></span>  
  
- <span data-ttu-id="d7ce2-114">Utwórz klasę aplikacji konsoli, która będzie zawierać kod CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-114">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="d7ce2-115">Zdefiniuj pola globalne, które mają być używane w klasie, aby odwołać się do zestawu ( <xref:System.CodeDom.CodeCompileUnit> ) i klasy ( <xref:System.CodeDom.CodeTypeDeclaration> ), określ nazwę wygenerowanego pliku źródłowego i Zadeklaruj `Main` metodę.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-115">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="d7ce2-116">Aby zainicjować wykres CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d7ce2-116">To initialize the CodeDOM graph</span></span>  
  
- <span data-ttu-id="d7ce2-117">W konstruktorze klasy aplikacji konsoli, Zainicjuj zestaw i klasę, a następnie Dodaj odpowiednie deklaracje do wykresu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-117">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="d7ce2-118">Aby dodać elementy członkowskie do wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d7ce2-118">To add members to the CodeDOM graph</span></span>  
  
- <span data-ttu-id="d7ce2-119">Dodaj pola do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeMemberField> obiektów do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-119">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- <span data-ttu-id="d7ce2-120">Dodaj właściwości do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeMemberProperty> obiektów do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-120">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- <span data-ttu-id="d7ce2-121">Dodaj metodę do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeMemberMethod> obiekt do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-121">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- <span data-ttu-id="d7ce2-122">Dodaj Konstruktor do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeConstructor> obiekt do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-122">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- <span data-ttu-id="d7ce2-123">Dodaj punkt wejścia do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeEntryPointMethod> obiekt do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-123">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="d7ce2-124">Aby wygenerować kod z wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d7ce2-124">To generate the code from the CodeDOM graph</span></span>  
  
- <span data-ttu-id="d7ce2-125">Wygeneruj kod źródłowy z grafu CodeDOM, wywołując <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-125">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="d7ce2-126">Aby utworzyć Graf i wygenerować kod</span><span class="sxs-lookup"><span data-stu-id="d7ce2-126">To create the graph and generate the code</span></span>  
  
1. <span data-ttu-id="d7ce2-127">Dodaj metody utworzone w poprzednich `Main` krokach do metody zdefiniowanej w pierwszym kroku.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-127">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. <span data-ttu-id="d7ce2-128">Kompiluj i wykonaj klasę generującą.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-128">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7ce2-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7ce2-129">Example</span></span>  
 <span data-ttu-id="d7ce2-130">Poniższy przykład kodu pokazuje kod z poprzednich kroków.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-130">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="d7ce2-131">Gdy poprzedni przykład jest kompilowany i wykonywany, generuje następujący kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-131">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="d7ce2-132">Wygenerowany kod źródłowy generuje następujące dane wyjściowe podczas kompilowania i wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-132">The generated source code produces the following output when compiled and executed.</span></span>  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7ce2-133">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d7ce2-133">Compiling the Code</span></span>  
  
- <span data-ttu-id="d7ce2-134">Ten przykład kodu wymaga `FullTrust` pomyślnego wykonania zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="d7ce2-134">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ce2-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7ce2-135">See also</span></span>

- [<span data-ttu-id="d7ce2-136">Używanie modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d7ce2-136">Using the CodeDOM</span></span>](using-the-codedom.md)
- [<span data-ttu-id="d7ce2-137">Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d7ce2-137">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)
