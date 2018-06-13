---
title: 'Porady: tworzenie klasy za pomocą modelu CodeDOM'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf244e796dad0f3817a3c5acd1fcda8eaf189e2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395391"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="772dc-102">Porady: tworzenie klasy za pomocą modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="772dc-102">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="772dc-103">Poniższe procedury przedstawiają sposób tworzenia i kompilowania wykresu CodeDOM generujący klasa zawierająca dwa pola, właściwości trzy metody, konstruktora i punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="772dc-103">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1.  <span data-ttu-id="772dc-104">Tworzenie aplikacji konsoli, który będzie używany kod CodeDOM do generowania kodu źródłowego dla klasy.</span><span class="sxs-lookup"><span data-stu-id="772dc-104">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="772dc-105">W tym przykładzie generowania klasy o nazwie `Sample`, i wygenerowany kod jest klasa o nazwie `CodeDOMCreatedClass` w pliku o nazwie SampleCode.</span><span class="sxs-lookup"><span data-stu-id="772dc-105">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2.  <span data-ttu-id="772dc-106">Podczas generowania klasy, inicjowanie wykresu CodeDOM i za pomocą modelu CodeDOM metod można zdefiniować elementów członkowskich, Konstruktor i punkt wejścia (`Main` metody) wygenerowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="772dc-106">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="772dc-107">W tym przykładzie wygenerowana klasa ma dwa pola, trzech właściwości, konstruktora, metody, a `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="772dc-107">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3.  <span data-ttu-id="772dc-108">Podczas generowania klasy, należy utworzyć dostawcy specyficzny dla języka kodu i wywołanie jego <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody do generowania kodu z wykresu.</span><span class="sxs-lookup"><span data-stu-id="772dc-108">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4.  <span data-ttu-id="772dc-109">Skompiluj i uruchom aplikację do generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="772dc-109">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="772dc-110">W tym przykładzie wygenerowany kod znajduje się w pliku o nazwie SampleCode.</span><span class="sxs-lookup"><span data-stu-id="772dc-110">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="772dc-111">Skompiluj i wykonanie tego kodu, aby zobaczyć przykładowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="772dc-111">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="772dc-112">Aby utworzyć aplikację, która będzie wykonywał kodu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="772dc-112">To create the application that will execute the CodeDOM code</span></span>  
  
-   <span data-ttu-id="772dc-113">Utwórz klasę aplikacji konsoli, zawiera kod CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="772dc-113">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="772dc-114">Definiowanie globalnego pola, które mają być używane w klasie można odwoływać się do zestawu (<xref:System.CodeDom.CodeCompileUnit>) i klasy (<xref:System.CodeDom.CodeTypeDeclaration>), określ nazwę wygenerowanym pliku źródłowym i zadeklarować `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="772dc-114">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="772dc-115">Aby zainicjować wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="772dc-115">To initialize the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="772dc-116">W konstruktorze klasy aplikacji konsoli zainicjować zestaw i klasa i Dodaj deklaracje odpowiednie do wykresu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="772dc-116">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="772dc-117">Aby dodać członków do wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="772dc-117">To add members to the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="772dc-118">Dodaj pola do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeMemberField> obiekty do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwość klasy.</span><span class="sxs-lookup"><span data-stu-id="772dc-118">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   <span data-ttu-id="772dc-119">Dodawanie właściwości do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeMemberProperty> obiekty do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwość klasy.</span><span class="sxs-lookup"><span data-stu-id="772dc-119">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   <span data-ttu-id="772dc-120">Dodawanie metody do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeMemberMethod> do obiektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwość klasy.</span><span class="sxs-lookup"><span data-stu-id="772dc-120">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   <span data-ttu-id="772dc-121">Dodaj Konstruktor do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeConstructor> do obiektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwość klasy.</span><span class="sxs-lookup"><span data-stu-id="772dc-121">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   <span data-ttu-id="772dc-122">Dodaj punkt wejścia do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeEntryPointMethod> do obiektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwość klasy.</span><span class="sxs-lookup"><span data-stu-id="772dc-122">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="772dc-123">Aby wygenerować kod z wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="772dc-123">To generate the code from the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="772dc-124">Generowanie kodu źródłowego z wykresu CodeDOM przez wywołanie metody <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="772dc-124">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="772dc-125">Aby utworzyć wykres i generowania kodu</span><span class="sxs-lookup"><span data-stu-id="772dc-125">To create the graph and generate the code</span></span>  
  
1.  <span data-ttu-id="772dc-126">Dodaj utworzone w poprzednich krokach do metody `Main` metody zdefiniowanej w pierwszym kroku.</span><span class="sxs-lookup"><span data-stu-id="772dc-126">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  <span data-ttu-id="772dc-127">Należy skompilować i uruchomić generowania klasy.</span><span class="sxs-lookup"><span data-stu-id="772dc-127">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="772dc-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="772dc-128">Example</span></span>  
 <span data-ttu-id="772dc-129">Poniższy przykład kodu pokazuje kod z powyższych kroków.</span><span class="sxs-lookup"><span data-stu-id="772dc-129">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="772dc-130">Po powyższym przykładzie są kompilowane i wykonywane, generuje następujący kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="772dc-130">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="772dc-131">Kod źródłowy wygenerowanego tworzy następujące dane wyjściowe w przypadku kompilowania i wykonywane.</span><span class="sxs-lookup"><span data-stu-id="772dc-131">The generated source code produces the following output when compiled and executed.</span></span>  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="772dc-132">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="772dc-132">Compiling the Code</span></span>  
  
-   <span data-ttu-id="772dc-133">W tym przykładzie kodu wymaga `FullTrust` zestawu uprawnień do wykonania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="772dc-133">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772dc-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="772dc-134">See Also</span></span>  
 [<span data-ttu-id="772dc-135">Używanie modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="772dc-135">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 [<span data-ttu-id="772dc-136">Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="772dc-136">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
