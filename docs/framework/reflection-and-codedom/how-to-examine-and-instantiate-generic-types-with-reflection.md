---
title: 'Instrukcje: Badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia'
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
ms.openlocfilehash: d6517edcc2784b7d70c08c4d15d837fc1f209c49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928240"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Instrukcje: Badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia
Informacje o typach ogólnych są uzyskiwane w taki sam sposób jak informacje o innych typach: przez badanie <xref:System.Type> obiektu, który reprezentuje typ ogólny. Różnica między zasadami polega na tym, że typ ogólny ma listę <xref:System.Type> obiektów reprezentujących parametry typu ogólnego. Pierwsza procedura w tej sekcji bada typy ogólne.  
  
 Można utworzyć <xref:System.Type> obiekt reprezentujący skonstruowany typ według argumentów typu powiązania do parametrów typu definicji typu ogólnego. Druga procedura pokazuje to.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Aby przejrzeć typ ogólny i jego parametry typu  
  
1. Pobierz wystąpienie <xref:System.Type> reprezentujące typ ogólny. W C# `typeof` poniższym kodzie, typ jest uzyskiwany przy użyciu operatora (`GetType` w Visual Basic, `typeid` w wizualizacji C++). Zapoznaj <xref:System.Type> się z tematem klasy, aby poznać <xref:System.Type> inne sposoby pobierania obiektu. Należy zauważyć, że w pozostałej części tej procedury typ jest zawarty w parametrze metody `t`o nazwie.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. Użyj właściwości, aby określić, czy typ jest ogólny, i <xref:System.Type.IsGenericTypeDefinition%2A> Użyj właściwości, aby określić, czy typ jest definicją typu ogólnego. <xref:System.Type.IsGenericType%2A>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. Pobierz tablicę zawierającą argumenty typu ogólnego przy użyciu <xref:System.Type.GetGenericArguments%2A> metody.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. Dla każdego argumentu typu należy określić, czy jest to parametr typu (na przykład w definicji typu ogólnego) czy typ, który został określony dla parametru typu (na przykład w typie konstruowanym), przy użyciu <xref:System.Type.IsGenericParameter%2A> właściwości.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. W systemie typów parametr typu ogólnego jest reprezentowany przez wystąpienie klasy <xref:System.Type>, podobnie jak typy zwykłe. Poniższy kod wyświetla nazwę i położenie <xref:System.Type> parametru obiektu, który reprezentuje parametr typu ogólnego. Pozycja parametru to uproszczone informacje. jest on bardziej interesujący podczas badania parametru typu, który został użyty jako argument typu innego typu ogólnego.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. Określanie ograniczenia typu podstawowego i ograniczeń interfejsu parametru typu ogólnego przy użyciu <xref:System.Type.GetGenericParameterConstraints%2A> metody w celu uzyskania wszystkich ograniczeń w pojedynczej tablicy. Ograniczenia nie są gwarantowane w żadnej określonej kolejności.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <xref:System.Type.GenericParameterAttributes%2A> Użyj właściwości, aby odnaleźć specjalne ograniczenia dla parametru typu, na przykład wymagając, aby był typem referencyjnym. Właściwość zawiera również wartości, które reprezentują wariancję, która może być maskowany, jak pokazano w poniższym kodzie.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. Specjalne atrybuty ograniczenia są flagami, a ta sama flaga (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>), która reprezentuje żadne specjalne ograniczenia, również nie reprezentuje kowariancji lub kontrawariancja. W ten sposób, aby testować dla dowolnego z tych warunków, należy użyć odpowiedniej maski. W takim przypadku należy użyć <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> do izolowania specjalnych flag ograniczeń.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Konstruowanie wystąpienia typu ogólnego  
 Typ ogólny jest podobny do szablonu. Nie można tworzyć wystąpień tego elementu, chyba że określono typy rzeczywiste dla parametrów typu ogólnego. Aby to zrobić w czasie wykonywania, przy użyciu odbicia wymaga <xref:System.Type.MakeGenericType%2A> metody.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>Aby skonstruować wystąpienie typu ogólnego  
  
1. <xref:System.Type> Pobierz obiekt, który reprezentuje typ ogólny. Poniższy kod pobiera typ <xref:System.Collections.Generic.Dictionary%602> ogólny na dwa różne sposoby: przy <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> użyciu przeciążenia metody z ciągiem opisującym typ i wywołując <xref:System.Type.GetGenericTypeDefinition%2A> metodę dla typu `Dictionary\<String, Example>` konstruowanego (`Dictionary(Of String, Example)` w Visual Basic). <xref:System.Type.MakeGenericType%2A> Metoda wymaga definicji typu ogólnego.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. Skonstruuj tablicę argumentów typu, które mają zostać zastąpione dla parametrów typu. Tablica musi zawierać poprawną liczbę <xref:System.Type> obiektów w tej samej kolejności, w jakiej występują na liście parametrów typu. W tym przypadku klucz (pierwszy typ parametru) jest typu <xref:System.String>, a wartości w słowniku są wystąpieniami klasy o nazwie. `Example`  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. Wywołaj <xref:System.Type.MakeGenericType%2A> metodę, aby powiązać argumenty typu z parametrami typu i skonstruować typ.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. Użyj przeciążenia <xref:System.Activator.CreateInstance%28System.Type%29> metody, aby utworzyć obiekt typu złożonego. Poniższy kod przechowuje dwa wystąpienia `Example` klasy w obiekcie będącym wynikiem. `Dictionary<String, Example>`  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu definiuje `DisplayGenericType` metodę, aby przeanalizować definicje typów ogólnych i skonstruowane typy używane w kodzie i wyświetlić ich informacje. <xref:System.Type.IsGenericType%2A> <xref:System.Type.IsGenericParameter%2A> <xref:System.Type.GenericParameterPosition%2A> Metoda pokazuje, jak używać właściwości, i i <xref:System.Type.GetGenericArguments%2A> metody. `DisplayGenericType`  
  
 W przykładzie zdefiniowano `DisplayGenericParameter` również metodę w celu sprawdzenia parametru typu ogólnego i wyświetlenia jego ograniczeń.  
  
 Przykładowy kod definiuje zestaw typów testów, w tym typ ogólny, który ilustruje ograniczenia parametru typu, i pokazuje, jak wyświetlić informacje o tych typach.  
  
 Przykład tworzy typ z <xref:System.Collections.Generic.Dictionary%602> klasy przez utworzenie tablicy argumentów typu i <xref:System.Type.MakeGenericType%2A> wywołanie metody. Program porównuje <xref:System.Type> obiekt skonstruowany przy <xref:System.Type.MakeGenericType%2A> użyciu z <xref:System.Type> obiektem uzyskanym`GetType` przy użyciu `typeof` (w Visual Basic), pokazując, że są one takie same. Podobnie program używa <xref:System.Type.GetGenericTypeDefinition%2A> metody do uzyskania definicji typu ogólnego złożonego typu i porównuje go <xref:System.Type> z obiektem reprezentującym <xref:System.Collections.Generic.Dictionary%602> klasę.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [Odbicie i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Typy ogólne](../../standard/generics/index.md)
