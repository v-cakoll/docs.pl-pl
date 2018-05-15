---
title: 'Porady: zbadanie i tworzenie wystąpień typów ogólnych za pomocą odbicia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0f964ac73f070b99cdfd06e9037d06ce7888938
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="6bc8a-102">Porady: zbadanie i tworzenie wystąpień typów ogólnych za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="6bc8a-102">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="6bc8a-103">Informacje o typach ogólnych są uzyskiwane w taki sam sposób jak informacje o innych typów:, sprawdzając <xref:System.Type> obiekt, który reprezentuje typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-103">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="6bc8a-104">Różnica zasady jest typem ogólnym listę <xref:System.Type> obiekty reprezentujące jego parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-104">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="6bc8a-105">Pierwsza procedura w tej sekcji sprawdza typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-105">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="6bc8a-106">Można utworzyć <xref:System.Type> obiekt, który reprezentuje skonstruowanego typu przez powiązanie argumentów typu do parametrów typu w definicji typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-106">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="6bc8a-107">Druga procedura pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-107">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="6bc8a-108">Aby sprawdzić typu ogólnego i jego parametrów typu</span><span class="sxs-lookup"><span data-stu-id="6bc8a-108">To examine a generic type and its type parameters</span></span>  
  
1.  <span data-ttu-id="6bc8a-109">Pobranie wystąpienia <xref:System.Type> reprezentujący typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-109">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="6bc8a-110">W poniższym kodzie typ są uzyskiwane przy użyciu języka C# `typeof` — operator (`GetType` w języku Visual Basic `typeid` w programie Visual C++).</span><span class="sxs-lookup"><span data-stu-id="6bc8a-110">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="6bc8a-111">Zobacz <xref:System.Type> klasy tematu inne sposoby <xref:System.Type> obiektu.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-111">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="6bc8a-112">Należy pamiętać, że w pozostałej części tej procedury, typ znajduje się w parametrze metody o nazwie `t`.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-112">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2.  <span data-ttu-id="6bc8a-113">Użyj <xref:System.Type.IsGenericType%2A> właściwość, aby ustalić, czy typ jest rodzajowy i użyj <xref:System.Type.IsGenericTypeDefinition%2A> właściwości w celu określenia, czy typ jest definicją typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-113">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3.  <span data-ttu-id="6bc8a-114">Pobierz tablicę, która zawiera argumenty typu ogólnego, używając <xref:System.Type.GetGenericArguments%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-114">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4.  <span data-ttu-id="6bc8a-115">Argumentu typu, należy ustalić, czy jest on parametr typu (na przykład w definicji typu ogólnego) lub typu, który został określony dla parametru typu (na przykład w skonstruowanego typu), za pomocą <xref:System.Type.IsGenericParameter%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-115">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5.  <span data-ttu-id="6bc8a-116">W systemie typów parametru typu ogólnego jest reprezentowany przez wystąpienie <xref:System.Type>, podobnie jak w zwykłym typy.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-116">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="6bc8a-117">Poniższy kod wyświetla nazwę i parametr pozycję <xref:System.Type> obiekt, który reprezentuje parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-117">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="6bc8a-118">Pozycja parametru jest prosta informacji jest większe znaczenie, badając parametr typu, który został użyty jako argument typu innego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-118">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6.  <span data-ttu-id="6bc8a-119">Określić ograniczenia typu podstawowego i ograniczenia interfejsu parametru typu ogólnego przy użyciu <xref:System.Type.GetGenericParameterConstraints%2A> metodę, aby uzyskać wszystkie ograniczenia w jednej macierzy.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-119">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="6bc8a-120">Ograniczenia nie gwarantuje się w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-120">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7.  <span data-ttu-id="6bc8a-121">Użyj <xref:System.Type.GenericParameterAttributes%2A> właściwości, aby odnaleźć ograniczeń specjalnych na parametr typu, np. wymaganie jej typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-121">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="6bc8a-122">Właściwość także wartości, które reprezentują wariancję, które można zamaskować off, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-122">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8.  <span data-ttu-id="6bc8a-123">Atrybuty specjalne ograniczenia są flagi i tę samą flagę (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) reprezentujący żadnych specjalnych ograniczenia reprezentuje również nie Kowariancja i kontrawariancja.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-123">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="6bc8a-124">W związku z tym aby przetestować dla dowolnego z tych warunków należy użyć odpowiednią maskę.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-124">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="6bc8a-125">W takim przypadku należy użyć <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> do izolowania flagi ograniczeń specjalnych.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-125">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="6bc8a-126">Utworzenie wystąpienia typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="6bc8a-126">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="6bc8a-127">Jest typem ogólnym jako szablonu.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-127">A generic type is like a template.</span></span> <span data-ttu-id="6bc8a-128">Nie można utworzyć wystąpień, chyba że zostanie rzeczywiste typy jego parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-128">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="6bc8a-129">Aby to zrobić w czasie wykonywania, za pomocą odbicia, wymaga <xref:System.Type.MakeGenericType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-129">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="6bc8a-130">Do utworzenia wystąpienia typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="6bc8a-130">To construct an instance of a generic type</span></span>  
  
1.  <span data-ttu-id="6bc8a-131">Pobierz <xref:System.Type> obiekt, który reprezentuje typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-131">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="6bc8a-132">Poniższy kod umożliwia pobranie typu ogólnego <xref:System.Collections.Generic.Dictionary%602> na dwa sposoby: za pomocą <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> przeciążenie metody zawierające ciąg opisujący typ i wywołując <xref:System.Type.GetGenericTypeDefinition%2A> metoda skonstruowanego typu `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6bc8a-132">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="6bc8a-133"><xref:System.Type.MakeGenericType%2A> Metoda wymaga definicji typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-133">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2.  <span data-ttu-id="6bc8a-134">Konstruować tablicę argumentów typu do zastąpienia dla parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-134">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="6bc8a-135">Tablica musi zawierać prawidłową liczbę <xref:System.Type> obiektów w tej samej kolejności, w jakiej występują na liście parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-135">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="6bc8a-136">W tym przypadku klucz (pierwszy parametr typu) jest typu <xref:System.String>, a wartości w słowniku są wystąpieniami klasy o nazwie `Example`.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-136">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3.  <span data-ttu-id="6bc8a-137">Wywołanie <xref:System.Type.MakeGenericType%2A> metodę, aby powiązać argumentów typu parametrów typu i konstruowania typu.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-137">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4.  <span data-ttu-id="6bc8a-138">Użyj <xref:System.Activator.CreateInstance%28System.Type%29> przeciążenie metody można utworzyć typu skonstruowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-138">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="6bc8a-139">Poniższy kod przechowuje dwa wystąpienia `Example` klasy w wynikowym `Dictionary<String, Example>` obiektu.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-139">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="6bc8a-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="6bc8a-140">Example</span></span>  
 <span data-ttu-id="6bc8a-141">Poniższy przykładowy kod definiuje `DisplayGenericType` metodę Przeanalizuj definicje typu ogólnego i typy utworzone używane w kodzie i wyświetlać swoje informacje.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-141">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="6bc8a-142">`DisplayGenericType` Metody przedstawia sposób użycia <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, i <xref:System.Type.GenericParameterPosition%2A> właściwości i <xref:System.Type.GetGenericArguments%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-142">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="6bc8a-143">Definiuje również przykład `DisplayGenericParameter` metody do badania parametr typu ogólnego i wyświetlić jej ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-143">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="6bc8a-144">Przykładowy kod definiuje zestaw typów testu, w tym typu ogólnego, przedstawiono ograniczenia parametru typu, która przedstawia sposób wyświetlania informacji na temat tych typów.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-144">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="6bc8a-145">Przykład tworzy typu z <xref:System.Collections.Generic.Dictionary%602> klasy, tworząc tablicę argumentów typu i wywoływanie <xref:System.Type.MakeGenericType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-145">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="6bc8a-146">Program porównuje <xref:System.Type> tworzony przy użyciu obiektu <xref:System.Type.MakeGenericType%2A> z <xref:System.Type> uzyskany przy użyciu obiektu `typeof` (`GetType` w języku Visual Basic), z którego wynika, że są one takie same.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-146">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="6bc8a-147">Podobnie, program używa <xref:System.Type.GetGenericTypeDefinition%2A> metodę, aby uzyskać definicji typu ogólnego utworzony typ i porównuje go do <xref:System.Type> reprezentujący obiekt <xref:System.Collections.Generic.Dictionary%602> klasy.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-147">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6bc8a-148">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6bc8a-148">Compiling the Code</span></span>  
  
-   <span data-ttu-id="6bc8a-149">Zawiera kod C# `using` instrukcje (`Imports` w języku Visual Basic) niezbędne do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-149">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="6bc8a-150">Nie odwołania do zestawów dodatkowe są wymagane.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-150">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="6bc8a-151">Kompilowanie kodu w wierszu polecenia przy użyciu csc.exe, vbc.exe lub cl.exe.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-151">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="6bc8a-152">Aby skompilować kod w programie Visual Studio, należy umieścić w szablonie Projekt aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="6bc8a-152">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc8a-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bc8a-153">See Also</span></span>  
 <xref:System.Type>  
 <xref:System.Reflection.MethodInfo>  
 [<span data-ttu-id="6bc8a-154">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="6bc8a-154">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [<span data-ttu-id="6bc8a-155">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="6bc8a-155">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [<span data-ttu-id="6bc8a-156">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="6bc8a-156">Generics</span></span>](../../../docs/standard/generics/index.md)
