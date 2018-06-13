---
title: Typy ogólne i odbicie (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 7e35c7d6712323bd7088ad68160da05cdf3a5115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335189"
---
# <a name="generics-and-reflection-c-programming-guide"></a>Typy ogólne i odbicie (Przewodnik programowania w języku C#)
Ponieważ środowisko uruchomieniowe języka wspólnego (CLR) ma dostęp do informacji typu ogólnego w czasie wykonywania, można użyć odbicia uzyskanie informacji na temat typów ogólnych w taki sam sposób jak w przypadku typów nierodzajową. Aby uzyskać więcej informacji, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 W [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] kilka nowych elementów członkowskich są dodawane do <xref:System.Type> klasę, aby włączyć informacje czasu wykonywania dla typów ogólnych. W dokumentacji tych klas, aby uzyskać więcej informacji na temat korzystania z tych metod i właściwości. <xref:System.Reflection.Emit> Przestrzeń nazw zawiera również nowe elementy członkowskie, które obsługuje elementów ogólnych. Zobacz [porady: Definiowanie typu ogólnego z odbiciem Emituj](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Lista niezmiennej warunki terminów używanych w ogólnym odbicia, zobacz <xref:System.Type.IsGenericType%2A> właściwości uwagi.  
  
|Nazwa elementu członkowskiego System.Type|Opis|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Zwraca wartość PRAWDA, jeśli typ jest rodzajowy.|  
|<xref:System.Type.GetGenericArguments%2A>|Zwraca tablicę `Type` obiektów, które reprezentują argumentów typu dostarczona do skonstruowanego typu lub typ parametrów definicji typu ogólnego.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Zwraca podstawowej definicji typu ogólnego dla bieżącego typu skonstruowane.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Zwraca tablicę `Type` obiekty reprezentujące ograniczenia dotyczące bieżącego ogólnego typu parametru.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Zwraca wartość PRAWDA, jeśli typ lub dowolny z jego otaczającego typach lub metodach zawierają parametrów typu, dla których określonych typów nie został podany.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Pobiera kombinację `GenericParameterAttributes` flagi opisujące ograniczeń specjalnych z bieżącym ogólnego typu parametru.|  
|<xref:System.Type.GenericParameterPosition%2A>|Aby uzyskać `Type` pozycja parametru typu na liście parametrów typu w definicji typu ogólnego lub ogólną definicją metody zadeklarowany parametr typu pobiera obiekt, który reprezentuje parametr typu.|  
|<xref:System.Type.IsGenericParameter%2A>|Pobiera wartość wskazującą, czy bieżący `Type` reprezentuje parametr typu ogólnego definicji typu lub metody.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Pobiera wartość wskazującą, czy bieżący <xref:System.Type> reprezentuje definicji typu ogólnego, z którego można skonstruować innych typów ogólnych. Zwraca wartość PRAWDA, jeśli typ reprezentuje definicji typu ogólnego.|  
|<xref:System.Type.DeclaringMethod%2A>|Zwraca metody ogólnej zdefiniowanego bieżący ogólny parametr typu, lub wartość null, jeśli parametr typu nie został zdefiniowany przez metody rodzajowej.|  
|<xref:System.Type.MakeGenericType%2A>|Zastępuje elementy tablicą typów parametrów typu bieżącej definicji typu ogólnego i zwraca <xref:System.Type> obiekt reprezentujący powstałe w ten sposób skonstruować typu.|  
  
 Ponadto członkowie <xref:System.Reflection.MethodInfo> klasy Włącz informacje czasu wykonywania dla metod generycznych. Zobacz <xref:System.Reflection.MethodBase.IsGenericMethod%2A> uwagi właściwości listę niezmiennej warunki terminów używanych w celu odzwierciedlenia na metody ogólne.  
  
|System.Reflection.MemberInfo Member Name|Opis|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Zwraca wartość PRAWDA, jeśli metody jest rodzajowy.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Zwraca tablicę obiektów typu, które reprezentują argumentów typu skonstruowane metody ogólnej lub parametrów typu definicję metody rodzajowej.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Zwraca podstawowej ogólną definicją metody dla bieżącej metody skonstruowane.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Zwraca wartość PRAWDA, jeśli metoda lub jej otaczającego typy zawierać żadnych parametrów typu, dla których nie podano określonych typów.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Zwraca wartość true, jeśli bieżący <xref:System.Reflection.MethodInfo> reprezentuje definicję metody rodzajowej.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Zastępuje elementy tablicą typów parametrów typu bieżącej definicji metody rodzajowej i zwraca <xref:System.Reflection.MethodInfo> obiekt reprezentujący powstałe w ten sposób skonstruowany — metoda.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  
 [Odbicie i typy ogólne](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [Typy ogólne](~/docs/standard/generics/index.md)
