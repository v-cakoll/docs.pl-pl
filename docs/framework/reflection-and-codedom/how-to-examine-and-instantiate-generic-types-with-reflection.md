---
title: 'Instrukcje: Badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia'
description: Zobacz, jak sprawdzić i utworzyć wystąpienia typów ogólnych z odbiciem. Użyj właściwości IsGenericType, IsGenericParameter i GenericParameterPosition.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
ms.openlocfilehash: b57a0ed0c809da442dc9fcf202ad364060971f80
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865102"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="49767-104">Instrukcje: Badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="49767-104">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="49767-105">Informacje o typach ogólnych są uzyskiwane w taki sam sposób jak informacje o innych typach: przez badanie <xref:System.Type> obiektu, który reprezentuje typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="49767-105">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="49767-106">Różnica między zasadami polega na tym, że typ ogólny ma listę <xref:System.Type> obiektów reprezentujących parametry typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="49767-106">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="49767-107">Pierwsza procedura w tej sekcji bada typy ogólne.</span><span class="sxs-lookup"><span data-stu-id="49767-107">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="49767-108">Można utworzyć <xref:System.Type> obiekt reprezentujący skonstruowany typ według argumentów typu powiązania do parametrów typu definicji typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="49767-108">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="49767-109">Druga procedura pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="49767-109">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="49767-110">Aby przejrzeć typ ogólny i jego parametry typu</span><span class="sxs-lookup"><span data-stu-id="49767-110">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="49767-111">Pobierz wystąpienie <xref:System.Type> reprezentujące typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="49767-111">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="49767-112">W poniższym kodzie, typ jest uzyskiwany przy użyciu operatora języka C# `typeof` ( `GetType` w Visual Basic, `typeid` w Visual C++).</span><span class="sxs-lookup"><span data-stu-id="49767-112">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="49767-113">Zapoznaj się z <xref:System.Type> tematem klasy, aby poznać inne sposoby pobierania <xref:System.Type> obiektu.</span><span class="sxs-lookup"><span data-stu-id="49767-113">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="49767-114">Należy zauważyć, że w pozostałej części tej procedury typ jest zawarty w parametrze metody o nazwie `t` .</span><span class="sxs-lookup"><span data-stu-id="49767-114">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="49767-115">Użyj <xref:System.Type.IsGenericType%2A> właściwości, aby określić, czy typ jest ogólny, i Użyj <xref:System.Type.IsGenericTypeDefinition%2A> właściwości, aby określić, czy typ jest definicją typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="49767-115">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="49767-116">Pobierz tablicę zawierającą argumenty typu ogólnego przy użyciu <xref:System.Type.GetGenericArguments%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="49767-116">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="49767-117">Dla każdego argumentu typu należy określić, czy jest to parametr typu (na przykład w definicji typu ogólnego) czy typ, który został określony dla parametru typu (na przykład w typie konstruowanym), przy użyciu <xref:System.Type.IsGenericParameter%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="49767-117">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="49767-118">W systemie typów parametr typu ogólnego jest reprezentowany przez wystąpienie klasy <xref:System.Type> , podobnie jak typy zwykłe.</span><span class="sxs-lookup"><span data-stu-id="49767-118">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="49767-119">Poniższy kod wyświetla nazwę i położenie parametru <xref:System.Type> obiektu, który reprezentuje parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="49767-119">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="49767-120">Pozycja parametru to uproszczone informacje. jest on bardziej interesujący podczas badania parametru typu, który został użyty jako argument typu innego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="49767-120">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="49767-121">Określanie ograniczenia typu podstawowego i ograniczeń interfejsu parametru typu ogólnego przy użyciu <xref:System.Type.GetGenericParameterConstraints%2A> metody w celu uzyskania wszystkich ograniczeń w pojedynczej tablicy.</span><span class="sxs-lookup"><span data-stu-id="49767-121">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="49767-122">Ograniczenia nie są gwarantowane w żadnej określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="49767-122">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="49767-123">Użyj <xref:System.Type.GenericParameterAttributes%2A> właściwości, aby odnaleźć specjalne ograniczenia dla parametru typu, na przykład wymagając, aby był typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="49767-123">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="49767-124">Właściwość zawiera również wartości, które reprezentują wariancję, która może być maskowany, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="49767-124">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="49767-125">Specjalne atrybuty ograniczenia są flagami, a ta sama flaga ( <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType> ), która reprezentuje żadne specjalne ograniczenia, również nie reprezentuje kowariancji lub kontrawariancja.</span><span class="sxs-lookup"><span data-stu-id="49767-125">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="49767-126">W ten sposób, aby testować dla dowolnego z tych warunków, należy użyć odpowiedniej maski.</span><span class="sxs-lookup"><span data-stu-id="49767-126">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="49767-127">W takim przypadku należy użyć <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> do izolowania specjalnych flag ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="49767-127">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="49767-128">Konstruowanie wystąpienia typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="49767-128">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="49767-129">Typ ogólny jest podobny do szablonu.</span><span class="sxs-lookup"><span data-stu-id="49767-129">A generic type is like a template.</span></span> <span data-ttu-id="49767-130">Nie można tworzyć wystąpień tego elementu, chyba że określono typy rzeczywiste dla parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="49767-130">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="49767-131">Aby to zrobić w czasie wykonywania, przy użyciu odbicia wymaga <xref:System.Type.MakeGenericType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="49767-131">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="49767-132">Aby skonstruować wystąpienie typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="49767-132">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="49767-133">Pobierz <xref:System.Type> obiekt, który reprezentuje typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="49767-133">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="49767-134">Poniższy kod pobiera typ ogólny <xref:System.Collections.Generic.Dictionary%602> na dwa różne sposoby: przy użyciu <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> przeciążenia metody z ciągiem opisującym typ oraz przez wywołanie <xref:System.Type.GetGenericTypeDefinition%2A> metody dla konstruowanego typu `Dictionary\<String, Example>` ( `Dictionary(Of String, Example)` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="49767-134">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="49767-135"><xref:System.Type.MakeGenericType%2A>Metoda wymaga definicji typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="49767-135">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="49767-136">Skonstruuj tablicę argumentów typu, które mają zostać zastąpione dla parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="49767-136">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="49767-137">Tablica musi zawierać poprawną liczbę <xref:System.Type> obiektów w tej samej kolejności, w jakiej występują na liście parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="49767-137">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="49767-138">W tym przypadku klucz (pierwszy typ parametru) jest typu <xref:System.String> , a wartości w słowniku są wystąpieniami klasy o nazwie `Example` .</span><span class="sxs-lookup"><span data-stu-id="49767-138">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="49767-139">Wywołaj <xref:System.Type.MakeGenericType%2A> metodę, aby powiązać argumenty typu z parametrami typu i skonstruować typ.</span><span class="sxs-lookup"><span data-stu-id="49767-139">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="49767-140">Użyj <xref:System.Activator.CreateInstance%28System.Type%29> przeciążenia metody, aby utworzyć obiekt typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="49767-140">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="49767-141">Poniższy kod przechowuje dwa wystąpienia `Example` klasy w obiekcie będącym wynikiem `Dictionary<String, Example>` .</span><span class="sxs-lookup"><span data-stu-id="49767-141">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="49767-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="49767-142">Example</span></span>  
 <span data-ttu-id="49767-143">Poniższy przykład kodu definiuje metodę, `DisplayGenericType` Aby przeanalizować definicje typów ogólnych i skonstruowane typy używane w kodzie i wyświetlić ich informacje.</span><span class="sxs-lookup"><span data-stu-id="49767-143">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="49767-144">`DisplayGenericType`Metoda pokazuje, jak używać <xref:System.Type.IsGenericType%2A> właściwości, i <xref:System.Type.IsGenericParameter%2A> <xref:System.Type.GenericParameterPosition%2A> i <xref:System.Type.GetGenericArguments%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="49767-144">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="49767-145">W przykładzie zdefiniowano również `DisplayGenericParameter` metodę w celu sprawdzenia parametru typu ogólnego i wyświetlenia jego ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="49767-145">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="49767-146">Przykładowy kod definiuje zestaw typów testów, w tym typ ogólny, który ilustruje ograniczenia parametru typu, i pokazuje, jak wyświetlić informacje o tych typach.</span><span class="sxs-lookup"><span data-stu-id="49767-146">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="49767-147">Przykład tworzy typ z <xref:System.Collections.Generic.Dictionary%602> klasy przez utworzenie tablicy argumentów typu i wywołanie <xref:System.Type.MakeGenericType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="49767-147">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="49767-148">Program porównuje <xref:System.Type> obiekt skonstruowany przy użyciu <xref:System.Type.MakeGenericType%2A> z <xref:System.Type> obiektem uzyskanym przy użyciu `typeof` ( `GetType` w Visual Basic), pokazując, że są one takie same.</span><span class="sxs-lookup"><span data-stu-id="49767-148">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="49767-149">Podobnie program używa <xref:System.Type.GetGenericTypeDefinition%2A> metody do uzyskania definicji typu ogólnego złożonego typu i porównuje go z <xref:System.Type> obiektem reprezentującym <xref:System.Collections.Generic.Dictionary%602> klasę.</span><span class="sxs-lookup"><span data-stu-id="49767-149">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="49767-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49767-150">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="49767-151">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="49767-151">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
- [<span data-ttu-id="49767-152">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="49767-152">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="49767-153">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="49767-153">Generics</span></span>](../../standard/generics/index.md)
